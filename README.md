# Taskbucks-
Online earning platform 
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TaskBucks - Earn by Writing, Working, and Referring</title>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@500;700&family=Roboto&display=swap" rel="stylesheet">
    <style>
        body { font-family: 'Roboto', sans-serif; margin:0; padding:0; background:#f5f5f5; }
        header { background:#1D6FA5; color:white; padding:20px; text-align:center; }
        header h1 { font-family:'Montserrat', sans-serif; margin:0; }
        nav { display:flex; justify-content:center; gap:20px; margin-top:10px; }
        nav a { color:white; text-decoration:none; font-weight:bold; }
        .hero { background:linear-gradient(90deg, #1D6FA5, #2AAE66); color:white; text-align:center; padding:80px 20px; }
        .hero h2 { font-family:'Montserrat', sans-serif; margin-bottom:20px; }
        .hero button { background:#F39C12; border:none; padding:15px 30px; font-size:18px; font-weight:bold; color:white; cursor:pointer; border-radius:10px; }
        .section { padding:60px 20px; text-align:center; }
        .packages { display:flex; flex-wrap:wrap; justify-content:center; gap:20px; }
        .package { background:white; padding:30px; border-radius:15px; width:250px; box-shadow:0 4px 8px rgba(0,0,0,0.1); }
        .package h3 { color:#1D6FA5; }
        .package p { font-size:14px; margin:10px 0; }
        .package button { background:#D4AF37; border:none; padding:10px 20px; border-radius:8px; cursor:pointer; font-weight:bold; }
        footer { background:#1D6FA5; color:white; text-align:center; padding:20px; margin-top:40px; }
        .dashboard { padding:40px 20px; max-width:900px; margin:0 auto; background:white; border-radius:15px; box-shadow:0 4px 8px rgba(0,0,0,0.1); margin-top:40px; }
        .wallet { display:flex; justify-content:space-between; margin-bottom:20px; }
        .tasks { margin-top:20px; }
        .task { background:#2AAE66; color:white; padding:15px; margin-bottom:15px; border-radius:10px; display:flex; justify-content:space-between; align-items:center; }
        .task button { background:#F39C12; border:none; padding:10px 15px; border-radius:8px; cursor:pointer; font-weight:bold; }
        @media(max-width:600px){ .packages{ flex-direction:column; align-items:center; } .wallet { flex-direction:column; gap:10px; } .task { flex-direction:column; gap:10px; } }
    </style>
</head>
<body>

<header>
    <h1>TaskBucks</h1>
    <nav>
        <a href="#packages">Packages</a>
        <a href="#dashboard">Dashboard</a>
        <a href="#contact">Contact</a>
    </nav>
</header>

<section class="hero">
    <h2>Earn by Writing, Completing Tasks, and Referring Friends!</h2>
    <button onclick="alert('Select a package below to pay via M-Pesa')">Join Now</button>
</section>

<section class="section" id="packages">
    <h2>Choose Your Package</h2>
    <div class="packages">
        <div class="package">
            <h3>Ksh 100</h3>
            <p>Earn up to Ksh 300 daily</p>
            <button onclick="payMpesastk(100)">Select</button>
        </div>
        <div class="package">
            <h3>Ksh 200</h3>
            <p>Earn up to Ksh 500 daily</p>
            <button onclick="payMpesastk(200)">Select</button>
        </div>
        <div class="package">
            <h3>Ksh 300</h3>
            <p>Earn up to Ksh 700 daily</p>
            <button onclick="payMpesastk(300)">Select</button>
        </div>
        <div class="package">
            <h3>Ksh 400</h3>
            <p>Earn up to Ksh 1000 daily</p>
            <button onclick="payMpesastk(400)">Select</button>
        </div>
    </div>
</section>

<section class="dashboard" id="dashboard">
    <h2>Your Dashboard</h2>
    <div class="wallet">
        <div>Wallet Balance: Ksh <span id="balance">0</span></div>
        <div>Referral Earnings: Ksh <span id="referral">0</span></div>
    </div>

    <div class="tasks">
        <h3>Available Tasks</h3>
        <div class="task">
            <span>Write a 500-word article</span>
            <button>Apply</button>
        </div>
        <div class="task">
            <span>Complete a short survey</span>
            <button>Start</button>
        </div>
        <div class="task">
            <span>Review a product online</span>
            <button>Start</button>
        </div>
    </div>
</section>

<footer id="contact">
    &copy; 2025 TaskBucks | Contact: support@taskbucks.com
</footer>

<script>
async function payMpesastk(amount) {
    const phone = prompt("Enter your phone number (format 2547xxxxxxx):");
    if(!phone) return;
    const accountReference = `Package-${amount}`;
    try {
        const response = await fetch('/api/payments/stkpush', {
            method: 'POST',
            headers: { 'Content-Type': 'application/json' },
            body: JSON.stringify({ phone, amount, accountReference })
        });
        const data = await response.json();
        alert('STK Push Sent! Please check your phone to complete payment.');
        console.log(data);
    } catch (err) {
        console.error(err);
        alert('Failed to initiate STK Push');
    }
}
</script>

</body>
</html>
