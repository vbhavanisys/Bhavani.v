<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Student Portfolio | Your Name</title>
  <meta name="description" content="Clean, responsive student portfolio for college projects, skills, and contact." />
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
  <style>
    :root{
      --bg: #0b0f19;
      --text: #e6e9f2;
      --muted: #9aa3b2;
      --brand: #6ee7f9;
      --brand-2: #a78bfa;
      --card: rgba(255,255,255,0.06);
      --border: rgba(255,255,255,0.12);
      --ring: rgba(110,231,249,.5);
      --shadow: 0 10px 30px rgba(0,0,0,.35);
      --radius: 18px;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0; font-family: Inter, system-ui, -apple-system, Segoe UI, Roboto, "Helvetica Neue", Arial, "Noto Sans", "Apple Color Emoji", "Segoe UI Emoji";
      color:var(--text); background:var(--bg); line-height:1.6;
      overflow-x:hidden;
    }
    /* ===== Background design (animated blobs + stars) ===== */
    .bg-wrap{position:fixed; inset:0; overflow:hidden; z-index:-1}
    .blob{position:absolute; filter: blur(60px); opacity:.55; mix-blend-mode:screen; animation: float 18s ease-in-out infinite}
    .b1{width:60vmax; height:60vmax; left:-10vmax; top:-10vmax; background: radial-gradient(circle at 30% 30%, #2dd4bf, transparent 50%), radial-gradient(circle at 70% 60%, #6366f1, transparent 50%)}
    .b2{width:55vmax; height:55vmax; right:-15vmax; bottom:-15vmax; background: radial-gradient(circle at 40% 40%, #a78bfa, transparent 50%), radial-gradient(circle at 70% 70%, #22d3ee, transparent 50%); animation-delay: -6s}
    .b3{width:45vmax; height:45vmax; left:40%; top:60%; transform:translate(-50%,-50%); background: radial-gradient(circle at 50% 50%, #f472b6, transparent 50%), radial-gradient(circle at 60% 60%, #60a5fa, transparent 50%); animation-delay: -12s}
    @keyframes float{0%,100%{transform:translateY(0) scale(1)}50%{transform:translateY(-20px) scale(1.05)}}
    .stars{position:absolute; inset:0; background-image: radial-gradient(2px 2px at 20% 30%, rgba(255,255,255,.5), rgba(255,255,255,0)), radial-gradient(1px 1px at 70% 80%, rgba(255,255,255,.4), rgba(255,255,255,0)), radial-gradient(1.5px 1.5px at 80% 20%, rgba(255,255,255,.35), rgba(255,255,255,0)); opacity:.7}

    /* ===== Layout ===== */
    header{position:sticky; top:0; backdrop-filter:saturate(160%) blur(10px); background:rgba(10,14,26,.45); border-bottom:1px solid var(--border); z-index:10}
    .nav{max-width:1100px; margin:0 auto; display:flex; align-items:center; justify-content:space-between; padding:14px 20px}
    .brand{display:flex; align-items:center; gap:10px; font-weight:700; letter-spacing:.2px}
    .brand .logo{width:36px; height:36px; border-radius:50%; display:grid; place-items:center; background:linear-gradient(135deg, var(--brand), var(--brand-2)); color:#0b0f19; font-weight:800}
    nav a{color:var(--text); text-decoration:none; margin:0 10px; font-weight:500; opacity:.85}
    nav a:hover{opacity:1}
    .btn{display:inline-flex; align-items:center; gap:10px; background:linear-gradient(135deg,var(--brand), var(--brand-2)); color:#0b0f19; padding:10px 16px; border-radius:999px; font-weight:700; border:none; cursor:pointer; box-shadow: var(--shadow)}

    main{max-width:1100px; margin:0 auto; padding: 28px 20px 80px}

    /* ===== Hero ===== */
    .hero{display:grid; grid-template-columns:1.2fr .8fr; gap:30px; align-items:center; padding:50px 0}
    .hero .card{background:var(--card); border:1px solid var(--border); border-radius: var(--radius); padding:28px; box-shadow: var(--shadow)}
    h1{font-size: clamp(28px, 5vw, 48px); line-height:1.15; margin:0 0 14px}
    .subtitle{color:var(--muted); margin:0 0 22px}
    .tags{display:flex; flex-wrap:wrap; gap:10px; margin-top:16px}
    .tag{padding:6px 10px; border-radius:999px; border:1px solid var(--border); background:rgba(255,255,255,.04); font-size:14px; color:var(--text)}
    .avatar{
      width:220px; aspect-ratio:1/1; border-radius: 28px; background: conic-gradient(from 180deg at 50% 50%, var(--brand), var(--brand-2)); padding:6px; margin:0 auto; display:grid; place-items:center;
      box-shadow: var(--shadow);
    }
    .avatar-inner{width:100%; height:100%; border-radius:22px; background:linear-gradient(180deg, rgba(255,255,255,.15), rgba(255,255,255,.03)); display:grid; place-items:center; font-size:64px; font-weight:800; color:#0b0f19}

    /* ===== Sections ===== */
    section{margin-top:50px}
    .section-title{font-size: clamp(20px, 3vw, 28px); margin:0 0 18px}
    .grid{display:grid; gap:18px}
    .cards-3{grid-template-columns: repeat(3, 1fr)}
    .cards-2{grid-template-columns: repeat(2, 1fr)}
    .card{background:var(--card); border:1px solid var(--border); border-radius: var(--radius); padding:18px; box-shadow: var(--shadow)}
    .card h3{margin:0 0 8px}
    .muted{color:var(--muted)}

    /* ===== Timeline (Education) ===== */
    .timeline{position:relative; padding-left:20px}
    .timeline:before{content:""; position:absolute; left:6px; top:0; bottom:0; width:2px; background:linear-gradient(var(--brand), var(--brand-2))}
    .t-item{position:relative; padding-left:18px; margin-bottom:18px}
    .t-item:before{content:""; position:absolute; left:-2px; top:4px; width:10px; height:10px; border-radius:50%; background:linear-gradient(135deg, var(--brand), var(--brand-2)); box-shadow:0 0 0 3px rgba(255,255,255,.08)}

    /* ===== Project card ===== */
    .project{display:flex; flex-direction:column; gap:12px}
    .project .thumb{height:150px; border-radius:14px; background:linear-gradient(135deg, rgba(110,231,249,.25), rgba(167,139,250,.25)); border:1px dashed rgba(255,255,255,.25); display:grid; place-items:center}
    .project a{color:var(--brand)}

    /* ===== Skills ===== */
    .skill{display:flex; justify-content:space-between; align-items:center; gap:10px}
    .bar{height:10px; background:#111827; border-radius:999px; overflow:hidden; border:1px solid var(--border)}
    .bar > span{display:block; height:100%; background:linear-gradient(90deg, var(--brand), var(--brand-2))}

    /* ===== Contact ===== */
    form{display:grid; gap:12px}
    input, textarea{width:100%; padding:12px 14px; background:rgba(255,255,255,.06); color:var(--text); border:1px solid var(--border); border-radius:12px; outline:none}
    input:focus, textarea:focus{box-shadow:0 0 0 4px var(--ring)}
    textarea{min-height:120px; resize:vertical}

    /* Footer */
    footer{margin-top:60px; padding:24px 0; text-align:center; color:var(--muted)}

    /* ===== Utilities ===== */
    .row{display:flex; gap:12px; flex-wrap:wrap}
    .mt-8{margin-top:8px}
    .mt-16{margin-top:16px}

    /* ===== Responsive ===== */
    @media (max-width: 900px){
      .hero{grid-template-columns:1fr}
    }
    @media (max-width: 720px){
      .cards-3{grid-template-columns: 1fr}
      .cards-2{grid-template-columns: 1fr}
    }

    /* Print-friendly tweaks */
    @media print{
      header, .btn { display:none !important }
      body{ background:white }
      .bg-wrap{ display:none }
      .card, .hero .card{ border:1px solid #ddd; background:white; box-shadow:none }
    }
  </style>
</head>
<body>
  <!-- Background visuals -->
  <div class="bg-wrap" aria-hidden="true">
    <div class="stars"></div>
    <div class="blob b1"></div>
    <div class="blob b2"></div>
    <div class="blob b3"></div>
  </div>

  <!-- Top nav -->
  <header>
    <div class="nav">
      <div class="brand">
        <div class="logo" aria-hidden="true">S</div>
        <span>Student Portfolio</span>
      </div>
      <nav>
        <a href="#about">About</a>
        <a href="#education">Education</a>
        <a href="#projects">Projects</a>
        <a href="#skills">Skills</a>
        <a href="#contact">Contact</a>
      </nav>
      <a class="btn" href="#contact">Hire / Contact</a>
    </div>
  </header>

  <main>
    <!-- Hero -->
    <section class="hero" id="home">
      <div class="card">
        <h1>Hi, I'm <span style="background:linear-gradient(135deg,var(--brand), var(--brand-2)); -webkit-background-clip:text; background-clip:text; color:transparent">Bhavani.V</span></h1>
        <p class="subtitle">Undergraduate Student • Computer Application• Passionate about web development and data structure.</p>
        <div class="row">
          <a class="btn" href="#projects">View Projects</a>
          <a class="btn" style="background:transparent; color:var(--text); border:1px solid var(--border)" href="resume.pdf" download>Download Résumé</a>
        </div>
        <div class="tags">
          <span class="tag">HTML</span>
          <span class="tag">CSS</span>
          <span class="tag">JavaScript</span>
          <span class="tag">C / C++</span>
          <span class="tag">Python</span>
        </div>
   
    </section>

    <!-- About -->
    <section id="about">
      <h2 class="section-title">About Me</h2>
      <div class="card">
        <p>Hello! I'm a Second-year BCA student at <strong>Prince shri Venkateswara arts and science College </strong>. I enjoy solving problems and turning ideas into delightful products. Currently exploring frontend frameworks and preparing for placements.</p>
        <p class="muted mt-8">Email: bhavani.v1013@gmail.com
• Location: Tamilnadu, Country:India • Open to internships and freelance work</p>
      </div>
    </section>

    <!-- Education -->
    <section id="education">
      <h2 class="section-title">Education</h2>
      <div class="card timeline">
        <div class="t-item">
          <h3>Bachelor of computer applications </h3>
          <p class="muted">Prince shri Venkateswara arts and science College
<br>
• 2024 – 2027<br> • CGPA: -</p>
        </div>
        <div class="t-item">
          <h3>Higher Secondary (Class XII)</h3>
          <p class="muted">Christ king girls higher secondary school<br>• 2023 – 2024 • Percentage: 92%</p>
        </div>
        <div class="t-item">
          <h3>Secondary (Class X)</h3>
          <p class="muted">Christ king girls higher secondary school 
<br>• 2012 – 2023 • Percentage: 87%</p>
        </div>
      </div>
    </section>

    
     
    <!-- Skills -->
    <section id="skills">
      <h2 class="section-title">Skills</h2>
      <div class="grid cards-2">
        <div class="card">
          <h3>Web Development</h3>
          <div class="skill mt-8"><span>HTML</span><span>90%</span></div>
          <div class="bar"><span style="width:90%"></span></div>
          <div class="skill mt-8"><span>CSS</span><span>85%</span></div>
          <div class="bar"><span style="width:85%"></span></div>
          <div class="skill mt-8"><span>JavaScript</span><span>75%</span></div>
          <div class="bar"><span style="width:75%"></span></div>
        </div>
        <div class="card">
          <h3>Computer Science</h3>
          <div class="skill mt-8"><span>Data Structures</span><span>80%</span></div>
          <div class="bar"><span style="width:80%"></span></div>
          <div class="skill mt-8"><span>OOP (C++/Java)</span><span>70%</span></div>
          <div class="bar"><span style="width:70%"></span></div>
          <div class="skill mt-8"><span>DBMS / SQL</span><span>90%</span></div>
          <div class="bar"><span style="width:65%"></span></div>
        </div>
      </div>
    </section>

    <!-- Contact -->
    <section id="contact">
      <h2 class="section-title">Contact</h2>
      <div class="grid cards-2">
        <div class="card">
          <form onsubmit="event.preventDefault(); alert('Thanks! Your message has been captured (demo).'); this.reset();">
            <div class="row">
              <input aria-label="Your name" placeholder="Your name" required />
              <input aria-label="Email" type="email" placeholder="Email" required />
            </div>
            <input aria-label="Subject" placeholder="Subject" />
            <textarea aria-label="Message" placeholder="Write your message..."></textarea>
            <button class="btn" type="submit">Send Message</button>
          </form>
        </div>
        <div class="card">
          <h3>Quick Links</h3>
          <p class="muted">Feel free to reach out on any of these platforms.</p>
          <p class="mt-16">
            <a href="#" class="tag">GitHub</a>
            <a href="#" class="tag">LinkedIn</a>
            <a href="#" class="tag">Email</a>
            <a href="#" class="tag">LeetCode</a>
          </p>
        </div>
      </div>
    </section>

    <footer>
      © <span id="year"></span> Bhavani.V• Built with HTML & CSS
    </footer>
  </main>

  <script>
    // Small enhancement: current year
    document.getElementById('year').textContent = new Date().getFullYear();
  </script>
</body>
</html>
