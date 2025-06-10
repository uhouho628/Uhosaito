# Uhosaito
<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>Webビューア（ショートカット付き）</title>
  <style>
    body {
      font-family: sans-serif;
      padding: 1em;
      max-width: 800px;
      margin: auto;
    }
    iframe {
      width: 100%;
      height: 80vh;
      border: 1px solid #ccc;
      display: none;
      margin-top: 1em;
    }
    .shortcuts {
      margin: 1em 0;
    }
    .shortcuts button {
      margin: 0.3em;
      padding: 0.5em 1em;
      font-size: 1em;
    }
    input[type="text"] {
      font-size: 1em;
      padding: 0.5em;
    }
    button {
      cursor: pointer;
    }
  </style>
</head>
<body>
  <h1>Webビューア（ショートカット付き）</h1>

  <div class="shortcuts">
    <button onclick="loadPageFromShortcut('https://example.com')">🧪 Example</button>
    <button onclick="loadPageFromShortcut('https://news.yahoo.co.jp')">📰 Yahoo!ニュース</button>
    <button onclick="loadPageFromShortcut('https://note.com')">📝 note</button>
    <button onclick="loadPageFromShortcut('https://qiita.com')">👨‍💻 Qiita</button>
    <button onclick="loadPageFromShortcut('https://github.com')">🐙 GitHub</button>
  </div>

  <input type="text" id="urlInput" placeholder="https://example.com" style="width: 80%;">
  <button onclick="loadPage()">表示</button>

  <iframe id="webFrame" sandbox="allow-scripts allow-forms allow-same-origin"></iframe>

  <script>
    function loadPageFromShortcut(url) {
      document.getElementById('urlInput').value = url;
      loadPage();
    }

    function loadPage() {
      const url = document.getElementById('urlInput').value;
      const frame = document.getElementById('webFrame');

      frame.style.display = 'block';
      frame.src = url;

      setTimeout(() => {
        try {
          const test = frame.contentWindow.location.href;
        } catch (e) {
          window.location.href = url;
        }
      }, 2000);
    }
  </script>
</body>
</html>
