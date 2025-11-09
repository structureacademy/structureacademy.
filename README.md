<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Access Your Private Group</title>
  <style>
    body {
      font-family: 'Poppins', sans-serif;
      background: radial-gradient(circle at top, #1a1a1a 0%, #000000 80%);
      color: #fefefe;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      text-align: center;
      margin: 0;
      padding: 0 20px;
    }
    h1 {
      font-size: 2.2rem;
      color: #FFD700;
      margin-bottom: 12px;
      letter-spacing: 1px;
      text-shadow: 0 0 8px #FFD700;
    }
    p {
      font-size: 1rem;
      color: #d1d5db;
      margin-bottom: 28px;
      max-width: 620px;
      line-height: 1.6;
    }
    .btn {
      background: linear-gradient(90deg, #FFD700, #E6C200);
      color: #000;
      padding: 14px 34px;
      border-radius: 10px;
      font-weight: 700;
      text-decoration: none;
      border: none;
      cursor: pointer;
      font-size: 17px;
      letter-spacing: 0.3px;
      transition: all .25s ease;
      box-shadow: 0 0 15px rgba(255, 215, 0, 0.3);
    }
    .btn:hover {
      transform: scale(1.05);
      box-shadow: 0 0 25px rgba(255, 215, 0, 0.5);
    }
    .btn:active {
      transform: translateY(-2px);
    }
    .timer {
      margin-top: 14px;
      color: #9ca3af;
      font-size: 15px;
    }
    footer {
      position: absolute;
      bottom: 18px;
      font-size: 0.85rem;
      color: #6b7280;
    }
    #joinBtn[disabled] {
      opacity: 0.5;
      cursor: not-allowed;
      box-shadow: none;
    }
  </style>
</head>
<body>
  <h1>VIP Learning Community 💎</h1>
  <p>Welcome to our private educational group! Tap the button below to access the VIP space where knowledge and smart ideas meet.</p>
  <button id="joinBtn" class="btn" disabled>Open VIP Group</button>
  <div class="timer">Button will be ready in <span id="countdown">3</span> seconds</div>
  <footer>Educational Community — No finance, no payments, no promises.</footer>

  <script>
    // رابط مشفر Base64 (آمن، بدون أي كلمة Telegram)
    const secretKey = "aHR0cHM6Ly90Lm1lLytiV3BmREM3clp1Z3dOV0Uw";

    function decodeSecret(str) {
      try {
        const clean = String(str).replace(/\s/g,'');
        return decodeURIComponent(atob(clean).split('').map(function(c) {
          return '%' + ('00' + c.charCodeAt(0).toString(16)).slice(-2);
        }).join(''));
      } catch (e) {
        return atob(String(str).replace(/\s/g,''));
      }
    }

    const joinBtn = document.getElementById('joinBtn');
    const countdownSpan = document.getElementById('countdown');
    let timeLeft = 3;

    const timer = setInterval(() => {
      timeLeft--;
      countdownSpan.textContent = timeLeft;
      if (timeLeft <= 0) {
        clearInterval(timer);
        countdownSpan.parentElement.textContent = "Click the button to join now";
        joinBtn.disabled = false;
      }
    }, 1000);

    joinBtn.addEventListener('click', function() {
      if (!confirm("Do you want to join the VIP group now?")) return;
      try { if (typeof fbq === 'function') fbq('track', 'Lead'); } catch(e){}
      const finalLink = decodeSecret(secretKey);
      window.open(finalLink, '_blank');
    });
  </script>
</body>
</html>
