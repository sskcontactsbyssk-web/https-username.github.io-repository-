# https-username.github.io-repository-
<!DOCTYPE html>
<html>
<head>
  <base target="_top">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f3f4f6;
      padding: 25px;
      margin: 0;
    }

    .container {
      max-width: 850px;
      margin: 20px auto;
      background: white;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 3px 15px #ddd;
    }

    h2 {
      color: #24292f;
      margin-top: 0;
    }

    label {
      display: block;
      font-weight: bold;
      margin: 15px 0 7px;
    }

    input, textarea {
      width: 100%;
      box-sizing: border-box;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 14px;
    }

    textarea {
      height: 300px;
      font-family: Consolas, monospace;
      resize: vertical;
    }

    button {
      background: #238636;
      color: white;
      border: none;
      padding: 14px 25px;
      margin-top: 18px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 16px;
      font-weight: bold;
      width: 100%;
    }

    button:disabled {
      opacity: .6;
      cursor: wait;
    }

    #status {
      margin-top: 18px;
      padding: 12px;
      border-radius: 6px;
      overflow-wrap: anywhere;
    }

    a {
      color: #0969da;
    }
  </style>
</head>

<body>
<div class="container">

  <h2>GitHub HTML Publisher</h2>
  <p>Upload your HTML page directly to GitHub.</p>

  <label>GitHub Repository URL</label>
  <input id="repo"
    placeholder="https://github.com/username/repository">

  <label>Branch Name</label>
  <input id="branch" value="main">

  <label>File Name / Path</label>
  <input id="filename" value="index.html">

  <label>HTML / CSS / JavaScript Code</label>
  <textarea id="content"
    placeholder="Paste your complete HTML code here"></textarea>

  <button id="pushBtn" onclick="pushCode()">
    Push to GitHub
  </button>

  <div id="status"></div>

</div>

<script>
function pushCode() {

  const data = {
    repo: document.getElementById('repo').value.trim(),
    branch: document.getElementById('branch').value.trim(),
    filename: document.getElementById('filename').value.trim(),
    content: document.getElementById('content').value
  };

  if (!data.repo || !data.filename || !data.content) {
    alert('Please fill all required fields.');
    return;
  }

  const btn = document.getElementById('pushBtn');
  const status = document.getElementById('status');

  btn.disabled = true;
  btn.innerText = 'Pushing...';
  status.textContent = 'Connecting to GitHub...';

  google.script.run
    .withSuccessHandler(function(result) {

      btn.disabled = false;
      btn.innerText = 'Push to GitHub';

      if (result.success) {
        status.innerHTML =
          'Successfully pushed!<br><br>' +
          '<a target="_blank" rel="noopener" href="' +
          encodeURI(result.url) + '">View GitHub File</a>';
      } else {
        status.textContent = 'Error: ' + result.message;
      }
    })
    .withFailureHandler(function(error) {
      btn.disabled = false;
      btn.innerText = 'Push to GitHub';
      status.textContent = 'Error: ' + error.message;
    })
    .pushToGitHub(data);
}
</script>

</body>
</html>

<!DOCTYPE html>
<html>
<head>
  <base target="_top">
  <meta name="viewport" content="width=device-width, initial-scale=1">

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f3f4f6;
      padding: 25px;
      margin: 0;
    }

    .container {
      max-width: 850px;
      margin: 20px auto;
      background: white;
      padding: 25px;
      border-radius: 12px;
      box-shadow: 0 3px 15px #ddd;
    }

    h2 {
      color: #24292f;
      margin-top: 0;
    }

    label {
      display: block;
      font-weight: bold;
      margin: 15px 0 7px;
    }

    input, textarea {
      width: 100%;
      box-sizing: border-box;
      padding: 12px;
      border: 1px solid #ccc;
      border-radius: 6px;
      font-size: 14px;
    }

    textarea {
      height: 300px;
      font-family: Consolas, monospace;
      resize: vertical;
    }

    button {
      background: #238636;
      color: white;
      border: none;
      padding: 14px 25px;
      margin-top: 18px;
      border-radius: 6px;
      cursor: pointer;
      font-size: 16px;
      font-weight: bold;
      width: 100%;
    }

    button:disabled {
      opacity: .6;
      cursor: wait;
    }

    #status {
      margin-top: 18px;
      padding: 12px;
      border-radius: 6px;
      overflow-wrap: anywhere;
    }

    a {
      color: #0969da;
    }
  </style>
</head>

<body>
<div class="container">

  <h2>GitHub HTML Publisher</h2>
  <p>Upload your HTML page directly to GitHub.</p>

  <label>GitHub Repository URL</label>
  <input id="repo"
    placeholder="https://github.com/username/repository">

  <label>Branch Name</label>
  <input id="branch" value="main">

  <label>File Name / Path</label>
  <input id="filename" value="index.html">

  <label>HTML / CSS / JavaScript Code</label>
  <textarea id="content"
    placeholder="Paste your complete HTML code here"></textarea>

  <button id="pushBtn" onclick="pushCode()">
    Push to GitHub
  </button>

  <div id="status"></div>

</div>

<script>
function pushCode() {

  const data = {
    repo: document.getElementById('repo').value.trim(),
    branch: document.getElementById('branch').value.trim(),
    filename: document.getElementById('filename').value.trim(),
    content: document.getElementById('content').value
  };

  if (!data.repo || !data.filename || !data.content) {
    alert('Please fill all required fields.');
    return;
  }

  const btn = document.getElementById('pushBtn');
  const status = document.getElementById('status');

  btn.disabled = true;
  btn.innerText = 'Pushing...';
  status.textContent = 'Connecting to GitHub...';

  google.script.run
    .withSuccessHandler(function(result) {

      btn.disabled = false;
      btn.innerText = 'Push to GitHub';

      if (result.success) {
        status.innerHTML =
          'Successfully pushed!<br><br>' +
          '<a target="_blank" rel="noopener" href="' +
          encodeURI(result.url) + '">View GitHub File</a>';
      } else {
        status.textContent = 'Error: ' + result.message;
      }
    })
    .withFailureHandler(function(error) {
      btn.disabled = false;
      btn.innerText = 'Push to GitHub';
      status.textContent = 'Error: ' + error.message;
    })
    .pushToGitHub(data);
}
</script>

</body>
</html>


