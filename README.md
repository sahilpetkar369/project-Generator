<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>ProjectGen AI — From Idea to Deployed</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Syne:wght@400;600;700;800&family=DM+Mono:ital,wght@0,300;0,400;0,500;1,400&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet">
<style>
:root{--bg:#05060a;--bg2:#0b0d14;--surface:#111420;--border:#1e2236;--accent:#6aff8e;--accent2:#3d8bff;--text:#e8eaf0;--muted:#6b7190;--card:#0f1220}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{background:var(--bg);color:var(--text);font-family:'DM Mono',monospace;overflow-x:hidden}
body::before{content:'';position:fixed;inset:0;background-image:url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");pointer-events:none;z-index:0}

/* NAV */
nav{position:fixed;top:0;left:0;right:0;z-index:100;padding:16px 40px;display:flex;align-items:center;justify-content:space-between;background:rgba(5,6,10,0.88);backdrop-filter:blur(20px);border-bottom:1px solid var(--border)}
.nav-logo{font-family:'Syne',sans-serif;font-weight:800;font-size:1.15rem;letter-spacing:-0.02em;color:var(--text);display:flex;align-items:center;gap:4px;cursor:pointer}
.nav-logo em{color:var(--accent);font-family:'Instrument Serif',serif;font-style:italic;font-weight:400}
.nav-links{display:flex;align-items:center;gap:28px;list-style:none}
.nav-links a{color:var(--muted);text-decoration:none;font-size:0.74rem;letter-spacing:0.08em;text-transform:uppercase;transition:color .2s}
.nav-links a:hover{color:var(--text)}
.nav-cta{background:var(--accent);color:#000;border:none;padding:9px 22px;font-family:'Syne',sans-serif;font-weight:700;font-size:0.82rem;cursor:pointer;transition:all .2s}
.nav-cta:hover{box-shadow:0 6px 24px rgba(106,255,142,.3);transform:translateY(-1px)}

/* HERO */
.hero{min-height:100vh;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;padding:120px 20px 60px;position:relative}
.hero-grid{position:absolute;inset:0;background-image:linear-gradient(rgba(106,255,142,.035) 1px,transparent 1px),linear-gradient(90deg,rgba(106,255,142,.035) 1px,transparent 1px);background-size:60px 60px;mask-image:radial-gradient(ellipse 80% 60% at 50% 50%,black 0%,transparent 100%)}
.badge{display:inline-flex;align-items:center;gap:8px;border:1px solid var(--border);padding:6px 16px;font-size:0.7rem;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-bottom:32px}
.badge-dot{width:6px;height:6px;background:var(--accent);border-radius:50%;animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1;transform:scale(1)}50%{opacity:.5;transform:scale(1.5)}}
.hero h1{font-family:'Syne',sans-serif;font-weight:800;font-size:clamp(3rem,8vw,7rem);line-height:.92;letter-spacing:-0.04em}
.hero h1 em{font-family:'Instrument Serif',serif;font-style:italic;font-weight:400;color:var(--accent);display:block}
.hero-sub{max-width:520px;margin:28px auto 0;color:var(--muted);font-size:.88rem;line-height:1.75}
.hero-btns{display:flex;gap:14px;margin-top:40px;justify-content:center;flex-wrap:wrap}
.btn-p{background:var(--accent);color:#000;border:none;padding:13px 30px;font-family:'Syne',sans-serif;font-weight:700;font-size:.88rem;cursor:pointer;transition:all .2s}
.btn-p:hover{transform:translateY(-2px);box-shadow:0 12px 36px rgba(106,255,142,.3)}
.btn-g{background:transparent;color:var(--text);border:1px solid var(--border);padding:13px 30px;font-family:'Syne',sans-serif;font-weight:600;font-size:.88rem;cursor:pointer;transition:all .2s}
.btn-g:hover{border-color:var(--muted);background:var(--surface)}
.stat-row{display:flex;gap:48px;justify-content:center;margin-top:64px;padding-top:48px;border-top:1px solid var(--border);flex-wrap:wrap}
.stat-num{font-family:'Syne',sans-serif;font-weight:800;font-size:2.2rem;letter-spacing:-0.04em}
.stat-num em{color:var(--accent);font-style:normal}
.stat-lbl{font-size:.7rem;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-top:4px}

/* SECTIONS */
.sec{padding:96px 20px}
.sec-inner{max-width:1100px;margin:0 auto}
.sec-tag{font-size:.7rem;letter-spacing:.14em;text-transform:uppercase;color:var(--accent);margin-bottom:12px}
.sec-h{font-family:'Syne',sans-serif;font-weight:800;font-size:clamp(2rem,4vw,3rem);letter-spacing:-0.03em;line-height:1.08}
.sec-h em{font-family:'Instrument Serif',serif;font-style:italic;font-weight:400;color:var(--muted)}

/* GENERATOR CARD */
.gen-card{margin-top:52px;background:var(--card);border:1px solid var(--border);overflow:hidden}
.card-bar{background:var(--surface);border-bottom:1px solid var(--border);padding:11px 18px;display:flex;align-items:center;gap:8px}
.dot{width:10px;height:10px;border-radius:50%}
.dr{background:#ff5f57}.dy{background:#febc2e}.dg{background:#28c840}
.card-bar-lbl{margin-left:auto;font-size:.68rem;letter-spacing:.07em;color:var(--muted)}
.gen-body{padding:36px;display:grid;grid-template-columns:1fr 1fr;gap:36px}
@media(max-width:700px){.gen-body{grid-template-columns:1fr}}
.form-lbl{font-size:.7rem;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-bottom:7px;display:block}
.form-group{margin-bottom:18px}
.inp{width:100%;background:var(--bg2);border:1px solid var(--border);color:var(--text);padding:11px 14px;font-family:'DM Mono',monospace;font-size:.83rem;outline:none;transition:border-color .2s}
.inp:focus{border-color:var(--accent)}
.tag-row{display:flex;gap:7px;flex-wrap:wrap;margin-top:9px}
.tag{background:var(--surface);border:1px solid var(--border);padding:4px 11px;font-size:.7rem;color:var(--muted);cursor:pointer;transition:all .15s;font-family:'DM Mono',monospace}
.tag:hover,.tag.on{border-color:var(--accent);color:var(--accent);background:rgba(106,255,142,.06)}
.gen-btn{width:100%;background:var(--accent);color:#000;border:none;padding:13px;font-family:'Syne',sans-serif;font-weight:700;font-size:.87rem;cursor:pointer;margin-top:6px;transition:all .2s;display:flex;align-items:center;justify-content:center;gap:8px}
.gen-btn:hover:not(:disabled){box-shadow:0 8px 28px rgba(106,255,142,.28)}
.gen-btn:disabled{opacity:.6;cursor:not-allowed}

/* OUTPUT */
.out-pane{border-left:1px solid var(--border);padding-left:36px;display:flex;flex-direction:column;min-height:340px}
@media(max-width:700px){.out-pane{border-left:none;padding-left:0;border-top:1px solid var(--border);padding-top:28px}}
.out-empty{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;text-align:center;color:var(--muted);font-size:.8rem;line-height:1.7;border:1px dashed var(--border);padding:32px}
.out-stream{display:none;flex-direction:column;gap:0}
.out-stream.show{display:flex;animation:fadeIn .4s ease}
@keyframes fadeIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}
.out-proj-name{font-family:'Syne',sans-serif;font-weight:800;font-size:1.45rem;letter-spacing:-0.02em;color:var(--accent);margin-bottom:4px;min-height:2rem}
.out-sec-lbl{font-size:.67rem;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin:14px 0 7px}
.out-feature{display:flex;align-items:flex-start;gap:8px;font-size:.79rem;color:var(--text);line-height:1.5;margin-bottom:5px;opacity:0;transition:all .3s ease}
.out-feature.show{opacity:1}
.out-feature::before{content:'→';color:var(--accent);flex-shrink:0}
.out-divider{height:1px;background:var(--border);margin:10px 0}
.week-row{display:flex;gap:10px;align-items:flex-start;margin-bottom:7px;opacity:0;transition:opacity .3s ease}
.week-row.show{opacity:1}
.wk{background:var(--surface);border:1px solid var(--border);padding:2px 8px;font-size:.66rem;color:var(--muted);flex-shrink:0;letter-spacing:.05em}
.wk-txt{font-size:.76rem;color:var(--muted);line-height:1.5}
.stack-chips{display:flex;gap:6px;flex-wrap:wrap;margin-top:4px}
.chip{background:rgba(106,255,142,.07);border:1px solid rgba(106,255,142,.2);color:var(--accent);padding:3px 10px;font-size:.68rem;letter-spacing:.04em}
.sync-btn{margin-top:14px;background:transparent;color:var(--accent);border:1px solid rgba(106,255,142,.3);padding:10px;font-family:'Syne',sans-serif;font-weight:700;font-size:.82rem;cursor:pointer;transition:all .2s;width:100%}
.sync-btn:hover{background:rgba(106,255,142,.08)}

/* DEBUGGER */
.debug-grid{margin-top:52px;display:grid;grid-template-columns:1fr 1fr;gap:0;border:1px solid var(--border)}
@media(max-width:720px){.debug-grid{grid-template-columns:1fr}}
.t-pane{background:#080b0f}
.t-head,.ai-head{background:var(--surface);border-bottom:1px solid var(--border);padding:10px 16px;display:flex;align-items:center;gap:8px}
.t-head span,.ai-head span{font-size:.68rem;color:var(--muted);margin-left:8px;letter-spacing:.06em}
.t-body{padding:20px;min-height:300px;display:flex;flex-direction:column;gap:8px}
.t-inp{width:100%;background:transparent;border:none;color:#ff8a80;font-family:'DM Mono',monospace;font-size:.77rem;outline:none;resize:none;line-height:1.7;flex:1;min-height:180px}
.t-inp::placeholder{color:rgba(255,138,128,.3)}
.t-prompt{color:var(--muted);font-size:.77rem;display:flex;gap:6px}
.t-prompt::before{content:'$';color:var(--accent)}
.debug-btn{width:100%;background:rgba(255,106,106,.1);color:#ff8a80;border:1px solid rgba(255,106,106,.25);padding:10px;font-family:'Syne',sans-serif;font-weight:700;font-size:.82rem;cursor:pointer;transition:all .2s}
.debug-btn:hover:not(:disabled){background:rgba(255,106,106,.2)}
.debug-btn:disabled{opacity:.5;cursor:not-allowed}
.ai-pane{border-left:1px solid var(--border);background:var(--card)}
.ai-d{width:8px;height:8px;background:var(--accent);border-radius:50%;animation:pulse 2s infinite}
.ai-body{padding:20px;font-size:.79rem;line-height:1.75;min-height:300px}
.ai-lbl{font-size:.67rem;letter-spacing:.1em;text-transform:uppercase;color:var(--accent);margin-bottom:7px}
.ai-txt{color:var(--muted);margin-bottom:14px}
.code-block{background:var(--surface);border:1px solid var(--border);border-left:3px solid var(--accent);padding:13px;font-size:.74rem;color:#b4d0f5;line-height:1.65;overflow-x:auto;white-space:pre-wrap;font-family:'DM Mono',monospace}
.kw{color:#ff9fd0}.str{color:#b5e98a}.fn{color:#7ec8e3}.cm{color:var(--muted)}
.ai-placeholder{display:flex;flex-direction:column;justify-content:center;align-items:center;height:260px;color:var(--muted);font-size:.78rem;text-align:center;line-height:1.8;padding:20px}

/* FEATURES */
.feat-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(280px,1fr));gap:1px;background:var(--border);margin-top:56px;border:1px solid var(--border)}
.feat-card{background:var(--bg2);padding:36px 32px;position:relative;overflow:hidden;transition:background .3s}
.feat-card:hover{background:var(--card)}
.feat-card::before{content:'';position:absolute;top:0;left:0;width:3px;height:0;background:var(--accent);transition:height .3s}
.feat-card:hover::before{height:100%}
.feat-n{font-family:'Syne',sans-serif;font-weight:800;font-size:2.8rem;color:var(--border);line-height:1;margin-bottom:16px;letter-spacing:-0.04em}
.feat-ico{font-size:1.5rem;margin-bottom:14px}
.feat-ttl{font-family:'Syne',sans-serif;font-weight:700;font-size:1.05rem;letter-spacing:-0.02em;margin-bottom:10px}
.feat-desc{font-size:.8rem;color:var(--muted);line-height:1.7}
.feat-tag{display:inline-block;margin-top:14px;font-size:.66rem;letter-spacing:.08em;text-transform:uppercase;color:var(--accent);border:1px solid rgba(106,255,142,.2);padding:3px 9px}

/* PHASES */
.phases-grid{display:grid;grid-template-columns:repeat(4,1fr);gap:0;margin-top:56px;border:1px solid var(--border);overflow:hidden}
@media(max-width:800px){.phases-grid{grid-template-columns:1fr 1fr}}
@media(max-width:460px){.phases-grid{grid-template-columns:1fr}}
.phase-card{padding:32px 26px;border-right:1px solid var(--border);position:relative;overflow:hidden}
.phase-card:last-child{border-right:none}
.phase-bg{position:absolute;bottom:-16px;right:-8px;font-family:'Syne',sans-serif;font-weight:800;font-size:5.5rem;color:var(--border);line-height:1;pointer-events:none;opacity:.4}
.ph-status{font-size:.66rem;letter-spacing:.1em;text-transform:uppercase;padding:3px 9px;margin-bottom:18px;display:inline-block}
.s-active{background:rgba(106,255,142,.1);color:var(--accent);border:1px solid rgba(106,255,142,.3)}
.s-next{background:rgba(61,139,255,.08);color:var(--accent2);border:1px solid rgba(61,139,255,.2)}
.s-plan{background:transparent;color:var(--muted);border:1px solid var(--border)}
.phase-ttl{font-family:'Syne',sans-serif;font-weight:700;font-size:.95rem;margin-bottom:10px}
.phase-items{list-style:none}
.phase-items li{font-size:.76rem;color:var(--muted);padding:3px 0;display:flex;gap:7px;align-items:flex-start;line-height:1.5}
.phase-items li::before{content:'─';color:var(--border);flex-shrink:0}

/* TICKER */
.ticker-bg{padding:56px 20px;background:var(--surface);overflow:hidden}
.ticker-wrap{display:flex;gap:14px;overflow:hidden;-webkit-mask-image:linear-gradient(90deg,transparent,black 10%,black 90%,transparent);margin-top:32px}
.ticker-inner{display:flex;gap:14px;animation:ticker 22s linear infinite;flex-shrink:0}
@keyframes ticker{from{transform:translateX(0)}to{transform:translateX(-50%)}}
.t-pill{background:var(--bg2);border:1px solid var(--border);padding:9px 22px;white-space:nowrap;font-size:.78rem;color:var(--muted);display:flex;align-items:center;gap:7px;flex-shrink:0}

/* SOCIAL */
.social-cards{display:grid;grid-template-columns:repeat(3,1fr);gap:18px;margin-top:44px}
@media(max-width:580px){.social-cards{grid-template-columns:1fr}}
.s-card{background:var(--bg2);border:1px solid var(--border);padding:26px;transition:all .2s}
.s-card:hover{border-color:var(--muted);transform:translateY(-3px)}
.s-ico{font-size:1.7rem;margin-bottom:11px}
.s-ttl{font-family:'Syne',sans-serif;font-weight:700;font-size:.93rem;margin-bottom:7px}
.s-desc{font-size:.77rem;color:var(--muted);line-height:1.6}

/* METRICS */
.metrics-inner{max-width:860px;margin:0 auto;display:grid;grid-template-columns:repeat(3,1fr);gap:1px;background:var(--border);border:1px solid var(--border)}
@media(max-width:560px){.metrics-inner{grid-template-columns:1fr}}
.m-card{background:var(--bg2);padding:40px 28px;text-align:center}
.m-ico{font-size:1.8rem;margin-bottom:14px}
.m-val{font-family:'Syne',sans-serif;font-weight:800;font-size:2.2rem;letter-spacing:-0.04em}
.m-val em{color:var(--accent);font-style:normal}
.m-key{font-size:.7rem;letter-spacing:.1em;text-transform:uppercase;color:var(--muted);margin-top:5px}
.m-desc{font-size:.76rem;color:var(--muted);margin-top:7px;line-height:1.5}

/* CTA */
.cta-sec{padding:110px 20px;text-align:center;position:relative;overflow:hidden}
.cta-glow{position:absolute;width:600px;height:600px;background:radial-gradient(circle,rgba(106,255,142,.07) 0%,transparent 70%);top:50%;left:50%;transform:translate(-50%,-50%);pointer-events:none}
.cta-h{font-family:'Syne',sans-serif;font-weight:800;font-size:clamp(2.4rem,6vw,5rem);letter-spacing:-0.04em;line-height:.98;position:relative}
.cta-h em{font-family:'Instrument Serif',serif;font-style:italic;font-weight:400;color:var(--accent)}
.cta-sub{color:var(--muted);font-size:.88rem;margin:18px auto 36px;max-width:440px;line-height:1.75;position:relative}
.email-row{display:flex;max-width:420px;margin:0 auto;position:relative}
.email-inp{flex:1;background:var(--surface);border:1px solid var(--border);border-right:none;color:var(--text);padding:13px 18px;font-family:'DM Mono',monospace;font-size:.83rem;outline:none}
.email-inp:focus{border-color:var(--accent)}
.email-btn{background:var(--accent);color:#000;border:none;padding:13px 26px;font-family:'Syne',sans-serif;font-weight:700;font-size:.83rem;cursor:pointer;transition:all .2s;white-space:nowrap}
.email-btn:hover{box-shadow:0 7px 26px rgba(106,255,142,.28)}

/* FOOTER */
footer{padding:36px 40px;border-top:1px solid var(--border);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:14px}
.f-logo{font-family:'Syne',sans-serif;font-weight:800;color:var(--muted)}
.f-logo em{color:var(--accent);font-family:'Instrument Serif',serif;font-style:italic;font-weight:400}
.f-links{display:flex;gap:22px;list-style:none}
.f-links a{color:var(--muted);font-size:.72rem;text-decoration:none;letter-spacing:.06em;text-transform:uppercase;transition:color .2s}
.f-links a:hover{color:var(--text)}
.f-copy{font-size:.7rem;color:var(--muted)}

/* UTILS */
.fade-up{opacity:0;transform:translateY(26px);transition:opacity .55s ease,transform .55s ease}
.fade-up.vis{opacity:1;transform:translateY(0)}
.spinner{display:inline-block;width:14px;height:14px;border:2px solid rgba(0,0,0,.3);border-top-color:#000;border-radius:50%;animation:spin .7s linear infinite}
.spinner-w{display:inline-block;width:14px;height:14px;border:2px solid rgba(106,255,142,.3);border-top-color:var(--accent);border-radius:50%;animation:spin .7s linear infinite}
@keyframes spin{to{transform:rotate(360deg)}}
.toast{position:fixed;bottom:28px;right:28px;background:var(--surface);border:1px solid var(--border);color:var(--text);padding:12px 20px;font-size:.8rem;z-index:999;opacity:0;transform:translateY(10px);transition:all .3s;pointer-events:none}
.toast.show{opacity:1;transform:translateY(0)}
.toast.ok{border-color:rgba(106,255,142,.4);color:var(--accent)}
.toast.err{border-color:rgba(255,106,106,.4);color:#ff8a80}
@media(max-width:640px){nav{padding:12px 18px}.nav-links{display:none}footer{flex-direction:column;text-align:center}}
</style>
</head>
<body>

<nav>
  <div class="nav-logo" onclick="scrollTo(0,0)">Project<em>Gen</em></div>
  <ul class="nav-links">
    <li><a href="#generator">Generator</a></li>
    <li><a href="#debugger">Debugger</a></li>
    <li><a href="#features">Features</a></li>
    <li><a href="#phases">Roadmap</a></li>
  </ul>
  <button class="nav-cta" onclick="document.querySelector('.cta-sec').scrollIntoView({behavior:'smooth'})">Early Access →</button>
</nav>

<!-- HERO -->
<section class="hero">
  <div class="hero-grid"></div>
  <div class="badge"><div class="badge-dot"></div>Phase 1 MVP — AI Generator Live</div>
  <h1>Your idea.<br><em>Deployed.</em></h1>
  <p class="hero-sub">The GitHub + IDE + Mentor for B.Tech students. Go from "I have an idea" to a live project with a public link — powered by Claude AI, built for college devs.</p>
  <div class="hero-btns">
    <button class="btn-p" onclick="document.getElementById('generator').scrollIntoView({behavior:'smooth'})">Generate My Project ↗</button>
    <button class="btn-g" onclick="document.getElementById('debugger').scrollIntoView({behavior:'smooth'})">Try Debugger</button>
  </div>
  <div class="stat-row">
    <div><div class="stat-num">14<em>d</em></div><div class="stat-lbl">Idea to Deployed</div></div>
    <div><div class="stat-num">4<em>+</em></div><div class="stat-lbl">Tech Stacks</div></div>
    <div><div class="stat-num">1<em>-click</em></div><div class="stat-lbl">GitHub + Deploy</div></div>
    <div><div class="stat-num">0<em>$</em></div><div class="stat-lbl">To Start</div></div>
  </div>
</section>

<!-- GENERATOR -->
<section class="sec" id="generator">
  <div class="sec-inner">
    <div class="sec-tag fade-up">// AI Idea Generator — Powered by Claude</div>
    <h2 class="sec-h fade-up">Generate your project<br><em>in under 30 seconds</em></h2>
    <div class="gen-card fade-up">
      <div class="card-bar">
        <div class="dot dr"></div><div class="dot dy"></div><div class="dot dg"></div>
        <span class="card-bar-lbl">projectgen.ai — idea_generator</span>
      </div>
      <div class="gen-body">
        <div>
          <div class="form-group">
            <label class="form-lbl">Your Domain / Interest</label>
            <input id="inp-interest" class="inp" placeholder="e.g. AI in Healthcare, Smart Cities…" />
          </div>
          <div class="form-group">
            <label class="form-lbl">Tech Stack</label>
            <input id="inp-stack" class="inp" placeholder="e.g. Python, React, Node.js…" />
            <div class="tag-row">
              <span class="tag" data-val="Python" onclick="toggleTag(this)">Python</span>
              <span class="tag" data-val="React" onclick="toggleTag(this)">React</span>
              <span class="tag" data-val="Node.js" onclick="toggleTag(this)">Node.js</span>
              <span class="tag" data-val="Machine Learning" onclick="toggleTag(this)">ML</span>
              <span class="tag" data-val="Next.js" onclick="toggleTag(this)">Next.js</span>
              <span class="tag" data-val="Flutter" onclick="toggleTag(this)">Flutter</span>
            </div>
          </div>
          <div class="form-group">
            <label class="form-lbl">Project Type</label>
            <div class="tag-row">
              <span class="tag on" id="type-mini" onclick="setType('mini')">Mini Project</span>
              <span class="tag" id="type-major" onclick="setType('major')">Major Project</span>
            </div>
          </div>
          <button class="gen-btn" id="gen-btn" onclick="generateProject()">
            <span id="gen-btn-content">✦ Generate Project + Roadmap</span>
          </button>
        </div>
        <div class="out-pane">
          <div class="out-empty" id="out-empty">
            <div style="font-size:2rem;margin-bottom:10px;opacity:.4">✦</div>
            Fill in your interest &amp; stack,<br>then hit Generate to see<br>your project come to life.
          </div>
          <div class="out-stream" id="out-stream">
            <div id="out-name" class="out-proj-name"></div>
            <div class="out-sec-lbl">Core Features</div>
            <div id="out-features"></div>
            <div class="out-divider"></div>
            <div class="out-sec-lbl">4-Week Roadmap</div>
            <div id="out-weeks"></div>
            <div class="out-divider"></div>
            <div class="out-sec-lbl">Suggested Stack</div>
            <div id="out-stack" class="stack-chips"></div>
            <button class="sync-btn" onclick="showToast('GitHub sync coming in Phase 3! 🚀','ok')">↗ Sync to GitHub</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- DEBUGGER -->
<section class="sec" id="debugger" style="background:var(--bg2)">
  <div class="sec-inner">
    <div class="sec-tag fade-up">// AI Debugger — Paste Error, Get Fix</div>
    <h2 class="sec-h fade-up">No more 2am<br><em>Stack Overflow</em></h2>
    <div class="debug-grid fade-up">
      <div class="t-pane">
        <div class="t-head">
          <div class="dot dr"></div><div class="dot dy"></div><div class="dot dg"></div>
          <span>terminal — paste your error here</span>
        </div>
        <div class="t-body">
          <div class="t-prompt">Paste your error below</div>
          <textarea id="debug-inp" class="t-inp" placeholder="ValueError: Input contains NaN, infinity or a value too large for dtype('float64').
Traceback (most recent call last):
  File &quot;app.py&quot;, line 14, in module
    model.fit(X_train, y_train)

Or any Python / JS / React / Node error…"></textarea>
          <button class="debug-btn" id="debug-btn" onclick="debugError()">
            <span id="debug-btn-content">⚡ Diagnose &amp; Fix with AI</span>
          </button>
        </div>
      </div>
      <div class="ai-pane">
        <div class="ai-head">
          <div class="ai-d"></div>
          <span>ProjectGen AI — Debugger</span>
        </div>
        <div class="ai-body" id="ai-debug-body">
          <div class="ai-placeholder">
            <div style="font-size:1.8rem;margin-bottom:10px;opacity:.4">🤖</div>
            Paste an error in the terminal<br>and I'll explain what went wrong<br>— then fix it for you.
          </div>
        </div>
      </div>
    </div>
  </div>
</section>

<!-- FEATURES -->
<section class="sec" id="features" style="background:var(--bg2)">
  <div class="sec-inner">
    <div class="sec-tag fade-up">// Core Features</div>
    <h2 class="sec-h fade-up">Everything a student<br><em>actually needs</em></h2>
    <div class="feat-grid fade-up">
      <div class="feat-card"><div class="feat-n">01</div><div class="feat-ico">🧠</div><div class="feat-ttl">Idea &amp; Roadmap Generator</div><div class="feat-desc">Enter domain and stack. Get a unique project name, feature list, tech advice, and week-by-week roadmap powered by Claude AI.</div><span class="feat-tag">Live Now</span></div>
      <div class="feat-card"><div class="feat-n">02</div><div class="feat-ico">🏗️</div><div class="feat-ttl">AI Architect &amp; Boilerplate</div><div class="feat-desc">Generates your full folder structure — /frontend, /backend, /ml_models — with ready-to-go core files like App.js, main.py, requirements.txt.</div><span class="feat-tag">Phase 2</span></div>
      <div class="feat-card"><div class="feat-n">03</div><div class="feat-ico">🐛</div><div class="feat-ttl">Integrated AI Debugger</div><div class="feat-desc">Paste your error. AI explains what went wrong and gives you corrected code. Works with Python, JS, React, Node — any stack.</div><span class="feat-tag">Live Now</span></div>
      <div class="feat-card"><div class="feat-n">04</div><div class="feat-ico">🐙</div><div class="feat-ttl">One-Click GitHub Sync</div><div class="feat-desc">Auto-creates your repo, pushes boilerplate, and keeps your commit streak alive with GitHub Pulse — green squares on autopilot.</div><span class="feat-tag">Phase 3</span></div>
      <div class="feat-card"><div class="feat-n">05</div><div class="feat-ico">🚀</div><div class="feat-ttl">One-Click Deploy</div><div class="feat-desc">Frontend to Vercel, backend to Railway. Every project gets a live URL + AI-generated README + public showcase page.</div><span class="feat-tag">Phase 3</span></div>
      <div class="feat-card"><div class="feat-n">06</div><div class="feat-ico">📣</div><div class="feat-ttl">Social Milestones</div><div class="feat-desc">Share milestones to LinkedIn or X with AI-written captions. Turn your college project into a public portfolio piece instantly.</div><span class="feat-tag">Phase 4</span></div>
    </div>
  </div>
</section>

<!-- TECH TICKER -->
<div class="ticker-bg">
  <div class="sec-inner"><div class="sec-tag fade-up">// Tech Stack</div><h2 class="sec-h fade-up" style="font-size:1.8rem">Production-grade tech<br><em>under the hood</em></h2></div>
  <div class="ticker-wrap">
    <div class="ticker-inner">
      <div class="t-pill"><span>⚡</span>Next.js</div><div class="t-pill"><span>🤖</span>Claude AI</div><div class="t-pill"><span>🖊️</span>Monaco Editor</div><div class="t-pill"><span>⚙️</span>FastAPI</div><div class="t-pill"><span>🗄️</span>Supabase</div><div class="t-pill"><span>🐙</span>GitHub API</div><div class="t-pill"><span>🚀</span>Vercel SDK</div><div class="t-pill"><span>🛤️</span>Railway</div><div class="t-pill"><span>🔷</span>TypeScript</div><div class="t-pill"><span>🐘</span>PostgreSQL</div><div class="t-pill"><span>🐍</span>Python</div><div class="t-pill"><span>⚛️</span>React</div>
      <div class="t-pill"><span>⚡</span>Next.js</div><div class="t-pill"><span>🤖</span>Claude AI</div><div class="t-pill"><span>🖊️</span>Monaco Editor</div><div class="t-pill"><span>⚙️</span>FastAPI</div><div class="t-pill"><span>🗄️</span>Supabase</div><div class="t-pill"><span>🐙</span>GitHub API</div><div class="t-pill"><span>🚀</span>Vercel SDK</div><div class="t-pill"><span>🛤️</span>Railway</div><div class="t-pill"><span>🔷</span>TypeScript</div><div class="t-pill"><span>🐘</span>PostgreSQL</div><div class="t-pill"><span>🐍</span>Python</div><div class="t-pill"><span>⚛️</span>React</div>
    </div>
  </div>
</div>

<!-- SOCIAL -->
<section class="sec" style="background:var(--surface)">
  <div class="sec-inner">
    <div class="sec-tag fade-up">// Community</div>
    <h2 class="sec-h fade-up">Build in public.<br><em>Grow your reputation.</em></h2>
    <div class="social-cards fade-up">
      <div class="s-card"><div class="s-ico">🟩</div><div class="s-ttl">GitHub Pulse</div><div class="s-desc">Auto-logs commits to keep your contribution graph green every day you work on your project.</div></div>
      <div class="s-card"><div class="s-ico">📢</div><div class="s-ttl">Social Share</div><div class="s-desc">One-click milestone sharing to LinkedIn or X with AI-written captions that actually sound like you.</div></div>
      <div class="s-card"><div class="s-ico">👥</div><div class="s-ttl">Peer Review</div><div class="s-desc">A comment section on every showcase page where students give feedback and suggest features.</div></div>
    </div>
  </div>
</section>

<!-- PHASES -->
<section class="sec" id="phases">
  <div class="sec-inner">
    <div class="sec-tag fade-up">// Development Roadmap</div>
    <h2 class="sec-h fade-up">Building in phases,<br><em>shipping fast</em></h2>
    <div class="phases-grid fade-up">
      <div class="phase-card"><div class="phase-bg">1</div><span class="ph-status s-active">✓ Active</span><div class="phase-ttl">Phase 1 — MVP</div><ul class="phase-items"><li>AI Idea Generator</li><li>Roadmap generation</li><li>AI Debugger</li><li>User auth + dashboard</li></ul></div>
      <div class="phase-card"><div class="phase-bg">2</div><span class="ph-status s-next">→ Next</span><div class="phase-ttl">Phase 2 — Code</div><ul class="phase-items"><li>Monaco code editor</li><li>Boilerplate generator</li><li>AI code assistant</li><li>File structure view</li></ul></div>
      <div class="phase-card"><div class="phase-bg">3</div><span class="ph-status s-plan">Planned</span><div class="phase-ttl">Phase 3 — Launch</div><ul class="phase-items"><li>GitHub API sync</li><li>One-click deploy</li><li>Showcase page</li><li>AI README gen</li></ul></div>
      <div class="phase-card"><div class="phase-bg">4</div><span class="ph-status s-plan">Planned</span><div class="phase-ttl">Phase 4 — Social</div><ul class="phase-items"><li>Social feed</li><li>Peer review system</li><li>GitHub Pulse</li><li>LinkedIn / X share</li></ul></div>
    </div>
  </div>
</section>

<!-- METRICS -->
<section class="sec" style="background:var(--bg2)">
  <div class="metrics-inner">
    <div class="m-card"><div class="m-ico">📅</div><div class="m-val">14<em>d</em></div><div class="m-key">Retention Goal</div><div class="m-desc">Students finishing a project within 14 days</div></div>
    <div class="m-card"><div class="m-ico">🌐</div><div class="m-val">80<em>%</em></div><div class="m-key">Deployment Rate</div><div class="m-desc">Projects moving from idea to live public link</div></div>
    <div class="m-card"><div class="m-ico">📈</div><div class="m-val">5k<em>+</em></div><div class="m-key">Social Reach</div><div class="m-desc">Project links shared on LinkedIn &amp; X monthly</div></div>
  </div>
</section>

<!-- CTA -->
<section class="cta-sec">
  <div class="cta-glow"></div>
  <h2 class="cta-h">Your next project<br><em>starts today</em></h2>
  <p class="cta-sub">Join hundreds of B.Tech students turning ideas into deployed projects. Early access is free.</p>
  <div class="email-row">
    <input class="email-inp" type="email" placeholder="your@email.com" id="email-inp" />
    <button class="email-btn" onclick="submitEmail()">Get Early Access →</button>
  </div>
</section>

<footer>
  <div class="f-logo">Project<em>Gen</em> AI</div>
  <ul class="f-links"><li><a href="#features">Features</a></li><li><a href="#phases">Roadmap</a></li><li><a href="#">GitHub</a></li><li><a href="#">Twitter</a></li></ul>
  <span class="f-copy">© 2025 ProjectGen AI. Built for B.Tech students.</span>
</footer>

<div class="toast" id="toast"></div>

<script>
const API_URL = "https://api.anthropic.com/v1/messages";
const MODEL = "claude-sonnet-4-20250514";

let selectedStack = [];
let projectType = 'mini';

function toggleTag(el) {
  const val = el.dataset.val;
  el.classList.toggle('on');
  if (selectedStack.includes(val)) {
    selectedStack = selectedStack.filter(t => t !== val);
  } else {
    selectedStack.push(val);
  }
  document.getElementById('inp-stack').value = selectedStack.join(', ');
}

function setType(t) {
  projectType = t;
  document.getElementById('type-mini').classList.toggle('on', t === 'mini');
  document.getElementById('type-major').classList.toggle('on', t === 'major');
}

function showToast(msg, type = '') {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.className = 'toast show ' + type;
  setTimeout(() => { t.className = 'toast'; }, 3200);
}

async function callClaude(prompt) {
  const res = await fetch(API_URL, {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify({
      model: MODEL,
      max_tokens: 1000,
      messages: [{ role: 'user', content: prompt }]
    })
  });
  if (!res.ok) {
    const err = await res.json().catch(() => ({}));
    throw new Error(err.error?.message || 'API error ' + res.status);
  }
  const data = await res.json();
  return data.content.map(b => b.text || '').join('');
}

async function generateProject() {
  const interest = document.getElementById('inp-interest').value.trim();
  const stack = document.getElementById('inp-stack').value.trim();
  if (!interest) { showToast('Enter your domain / interest first', 'err'); return; }

  const btn = document.getElementById('gen-btn');
  btn.disabled = true;
  document.getElementById('gen-btn-content').innerHTML = '<div class="spinner"></div>&nbsp;Generating with AI…';

  document.getElementById('out-empty').style.display = 'none';
  const streamEl = document.getElementById('out-stream');
  streamEl.classList.add('show');
  document.getElementById('out-name').textContent = '…';
  document.getElementById('out-features').innerHTML = '';
  document.getElementById('out-weeks').innerHTML = '';
  document.getElementById('out-stack').innerHTML = '';

  const prompt = `You are ProjectGen AI helping a B.Tech college student.
Generate a creative project idea based on:
- Domain: "${interest}"
- Stack: "${stack || 'any modern stack'}"
- Type: ${projectType === 'mini' ? 'Mini Project (2-4 weeks, simpler scope)' : 'Major Project (8-12 weeks, complex scope)'}

Respond ONLY with a JSON object. No markdown fences, no extra text, just the raw JSON:
{"name":"Creative project name (2-4 words)","tagline":"One sentence pitch","features":["Feature 1 (max 10 words)","Feature 2 (max 10 words)","Feature 3 (max 10 words)","Feature 4 (max 10 words)"],"weeks":[{"week":"W1","task":"Task description (max 8 words)"},{"week":"W2","task":"Task description (max 8 words)"},{"week":"W3","task":"Task description (max 8 words)"},{"week":"W4","task":"Task description (max 8 words)"}],"stack":["Tech1","Tech2","Tech3","Tech4"]}`;

  try {
    const raw = await callClaude(prompt);
    const clean = raw.replace(/```json|```/g, '').trim();
    const d = JSON.parse(clean);

    // Animate name char by char
    const nameEl = document.getElementById('out-name');
    nameEl.textContent = '';
    let i = 0;
    const ni = setInterval(() => {
      nameEl.textContent = d.name.slice(0, ++i);
      if (i >= d.name.length) clearInterval(ni);
    }, 45);

    // Features with stagger
    d.features.forEach((f, idx) => {
      setTimeout(() => {
        const el = document.createElement('div');
        el.className = 'out-feature';
        el.textContent = f;
        document.getElementById('out-features').appendChild(el);
        requestAnimationFrame(() => requestAnimationFrame(() => el.classList.add('show')));
      }, 300 + idx * 130);
    });

    // Weeks with stagger
    d.weeks.forEach((w, idx) => {
      setTimeout(() => {
        const el = document.createElement('div');
        el.className = 'week-row';
        el.innerHTML = `<span class="wk">${w.week}</span><span class="wk-txt">${w.task}</span>`;
        document.getElementById('out-weeks').appendChild(el);
        requestAnimationFrame(() => requestAnimationFrame(() => el.classList.add('show')));
      }, 900 + idx * 100);
    });

    // Stack chips
    d.stack.forEach((s, idx) => {
      setTimeout(() => {
        const el = document.createElement('span');
        el.className = 'chip';
        el.textContent = s;
        document.getElementById('out-stack').appendChild(el);
      }, 1300 + idx * 80);
    });

    showToast('Project generated! 🎉', 'ok');
  } catch (e) {
    document.getElementById('out-name').textContent = 'Error — ' + e.message;
    showToast('Generation failed: ' + e.message, 'err');
  } finally {
    btn.disabled = false;
    document.getElementById('gen-btn-content').textContent = '✦ Regenerate';
  }
}

async function debugError() {
  const error = document.getElementById('debug-inp').value.trim();
  if (!error) { showToast('Paste an error message first', 'err'); return; }

  const btn = document.getElementById('debug-btn');
  btn.disabled = true;
  document.getElementById('debug-btn-content').innerHTML = '<div class="spinner-w"></div>&nbsp;Analyzing…';

  const body = document.getElementById('ai-debug-body');
  body.innerHTML = `<div class="ai-placeholder"><div class="spinner-w" style="width:24px;height:24px;border-width:3px"></div><div style="margin-top:14px;font-size:.8rem">Diagnosing your error…</div></div>`;

  const prompt = `You are an expert debugger helping a college student.
Their error:
${error}

Respond ONLY with raw JSON (no markdown fences, no preamble):
{"language":"Python/JavaScript/etc","cause":"2-3 sentence plain English root cause explanation","fix":"1-2 sentence fix instructions","code":"The corrected code snippet only (relevant fixed lines)"}`;

  try {
    const raw = await callClaude(prompt);
    const clean = raw.replace(/```json|```/g, '').trim();
    const d = JSON.parse(clean);

    body.innerHTML = `
      <div class="ai-lbl">Root Cause — ${esc(d.language)}</div>
      <div class="ai-txt">${esc(d.cause)}</div>
      <div class="ai-lbl">How to Fix</div>
      <div class="ai-txt">${esc(d.fix)}</div>
      <div class="ai-lbl">Fixed Code</div>
      <div class="code-block">${highlight(esc(d.code))}</div>
    `;
    showToast('Error diagnosed! 🐛→✓', 'ok');
  } catch (e) {
    body.innerHTML = `<div class="ai-placeholder" style="color:#ff8a80">Failed: ${esc(e.message)}<br><br><span style="color:var(--muted);font-size:.75rem">Check connection and try again.</span></div>`;
    showToast('Diagnosis failed', 'err');
  } finally {
    btn.disabled = false;
    document.getElementById('debug-btn-content').innerHTML = '⚡ Diagnose &amp; Fix with AI';
  }
}

function esc(s) {
  if (!s) return '';
  return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');
}

function highlight(code) {
  return code
    .replace(/\b(import|from|def|class|return|if|else|elif|for|while|try|except|with|as|in|not|and|or|True|False|None|const|let|var|function|async|await|throw|new|export|default)\b/g,'<span class="kw">$1</span>')
    .replace(/(&#39;[^&#39;]*&#39;|&quot;[^&quot;]*&quot;)/g,'<span class="str">$1</span>')
    .replace(/#[^\n]*/g,'<span class="cm">$&</span>')
    .replace(/(\/\/[^\n]*)/g,'<span class="cm">$1</span>');
}

function submitEmail() {
  const v = document.getElementById('email-inp').value.trim();
  if (!v || !v.includes('@')) { showToast('Enter a valid email', 'err'); return; }
  showToast('✓ Added to early access list!', 'ok');
  document.getElementById('email-inp').value = '';
}

// Scroll animations
const obs = new IntersectionObserver(es => es.forEach(e => { if (e.isIntersecting) e.target.classList.add('vis'); }), { threshold: 0.12 });
document.querySelectorAll('.fade-up').forEach(el => obs.observe(el));

// Enter key support
document.getElementById('inp-interest').addEventListener('keydown', e => { if (e.key === 'Enter') generateProject(); });
document.getElementById('inp-stack').addEventListener('keydown', e => { if (e.key === 'Enter') generateProject(); });
</script>
</body>
</html>
