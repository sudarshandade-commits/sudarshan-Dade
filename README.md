# Sudarshan Dade
It my portfolio
Hi, I am Sudarshan Dade, an aspiring AI/ML currently pursuing my engineering studies. I am passionate about building innovative solutions using technology. I enjoy learning new skills, solving real-world problems, and continuously improving my technical knowledge. My goal is to become a skilled professional and contribute to the field of artificial intelligence.

1. HTML (index.html)
      <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>AI Intrusion Detection System</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

<div class="container">
    <h1>🔐 AI-Based URL Threat Detector</h1>
    
    <input type="text" id="urlInput" placeholder="Enter URL here...">
    
    <button onclick="checkURL()">Check URL</button>
    
    <div id="result"></div>
</div>

<script src="script.js"></script>
</body>
</html> 

 2. CSS (style.css)
        body {
    font-family: Arial, sans-serif;
    background: linear-gradient(to right, #1e3c72, #2a5298);
    color: white;
    text-align: center;
    padding-top: 100px;
}

.container {
    background: rgba(0,0,0,0.6);
    padding: 30px;
    border-radius: 10px;
    width: 400px;
    margin: auto;
}

h1 {
    margin-bottom: 20px;
}

input {
    width: 90%;
    padding: 10px;
    border-radius: 5px;
    border: none;
    margin-bottom: 15px;
}

button {
    padding: 10px 20px;
    background: #00c853;
    border: none;
    color: white;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background: #009624;
}

#result {
    margin-top: 20px;
    font-size: 18px;
    font-weight: bold;
}
3. JavaScript (script.js)
         function checkURL() {
    let url = document.getElementById("urlInput").value;
    let result = document.getElementById("result");

    if (url === "") {
        result.innerHTML = "⚠️ Please enter a URL";
        return;
    }

    let score = 0;

    // 🔹 Rule 1: URL length
    if (url.length > 75) score++;

    // 🔹 Rule 2: Contains suspicious characters
    if (url.includes("@") || url.includes("-") || url.split('.').length > 4) {
        score++;
    }

    // 🔹 Rule 3: Uses IP instead of domain
    let ipPattern = /(\d{1,3}\.){3}\d{1,3}/;
    if (ipPattern.test(url)) {
        score++;
    }

    // 🔹 Rule 4: No HTTPS
    if (!url.startsWith("https")) {
        score++;
    }

    // 🔹 Rule 5: Suspicious keywords
    let keywords = ["login", "verify", "bank", "urgent", "update"];
    for (let word of keywords) {
        if (url.toLowerCase().includes(word)) {
            score++;
            break;
        }
    }

    // 🔹 Final decision
    if (score <= 1) {
        result.innerHTML = "✅ Safe URL";
        result.style.color = "lightgreen";
    } else if (score <= 3) {
        result.innerHTML = "⚠️ Suspicious URL";
        result.style.color = "yellow";
    } else {
        result.innerHTML = "❌ Dangerous URL";
        result.style.color = "red";
    }
}
         
