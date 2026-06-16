<!DOCTYPE html>
<html lang="de">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
<meta name="apple-mobile-web-app-title" content="Lernkarten">
<meta name="theme-color" content="#0f1117">
<title>Lernkarten · Altenburg</title>
<script>document.documentElement.classList.add('js-ok');</script>
<style>
:root{
  --bg:#0f1117;--surf:#1a1d27;--surf2:#22263a;--border:#2e3450;
  --acc:#4f7cff;--acc2:#7c9fff;--green:#22c55e;--red:#ef4444;--yellow:#f59e0b;--purple:#a78bfa;
  --text:#e8eaf6;--dim:#8892b0;--dimmer:#4a5578;--r:14px;--rs:9px;
}
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent}
html{height:100%}
body{background:var(--bg);color:var(--text);font-family:'Segoe UI',system-ui,-apple-system,sans-serif;min-height:100vh;min-height:100dvh;display:flex;flex-direction:column;overflow-x:hidden;-webkit-text-size-adjust:100%}
.screen{display:none;flex-direction:column;min-height:100vh;min-height:100dvh}
.js-ok .screen.active{display:flex}

/* no-JS notice */
#js-warning{display:flex;flex-direction:column;gap:14px;align-items:center;justify-content:center;text-align:center;padding:32px 24px;min-height:100vh;min-height:100dvh;background:radial-gradient(ellipse at 50% 0%,#1a2a5e 0%,var(--bg) 60%)}
.js-ok #js-warning{display:none}
#js-warning .jw-ic{font-size:46px}
#js-warning h2{font-size:19px;font-weight:800;max-width:340px;letter-spacing:-.3px}
#js-warning p{font-size:13.5px;color:var(--dim);line-height:1.6;max-width:340px}
#js-warning .jw-step{background:var(--surf);border:1px solid var(--border);border-radius:12px;padding:13px 15px;font-size:13.5px;line-height:1.55;text-align:left;max-width:340px;color:var(--text)}
#js-warning .jw-step b{color:var(--acc2)}

/* START */
#start{align-items:center;justify-content:center;padding:28px 20px;gap:0;background:radial-gradient(ellipse at 50% 0%,#1a2a5e 0%,var(--bg) 60%)}
.logo{display:flex;flex-direction:column;align-items:center;gap:10px;margin-bottom:26px}
.logo-icon{width:68px;height:68px;background:linear-gradient(135deg,#3a5fd9,#6b48d0);border-radius:20px;display:flex;align-items:center;justify-content:center;font-size:32px;box-shadow:0 8px 32px rgba(79,124,255,.35)}
.app-title{font-size:23px;font-weight:800;letter-spacing:-.5px;text-align:center}
.app-sub{font-size:13px;color:var(--dim);margin-top:3px;text-align:center}
.stats-row{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;width:100%;max-width:400px;margin-bottom:22px}
.stat{background:var(--surf);border:1px solid var(--border);border-radius:var(--rs);padding:12px 8px;text-align:center}
.stat-n{font-size:22px;font-weight:700;color:var(--acc2);line-height:1}
.stat-l{font-size:11px;color:var(--dim);margin-top:3px}
.sect{width:100%;max-width:400px;margin-bottom:16px}
.sect-lbl{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.8px;color:var(--dim);margin-bottom:8px}
.btn-row{display:flex;gap:7px}
.tog{flex:1;padding:11px 6px;background:var(--surf);border:2px solid var(--border);border-radius:var(--rs);color:var(--dim);font-size:12px;font-weight:600;cursor:pointer;text-align:center;transition:all .12s}
.tog.on{background:rgba(79,124,255,.14);border-color:var(--acc);color:var(--acc2)}
.btn-big{width:100%;max-width:400px;padding:17px;border:none;border-radius:var(--r);color:#fff;font-size:16px;font-weight:700;cursor:pointer;transition:transform .1s;margin-top:4px}
.btn-big:active{transform:scale(.97)}
.btn-primary{background:linear-gradient(135deg,#3a5fd9,#6b48d0);box-shadow:0 4px 20px rgba(79,124,255,.4)}
.btn-test{background:linear-gradient(135deg,#b45309,#92400e);box-shadow:0 4px 16px rgba(245,158,11,.3);margin-top:8px}

/* HEADER */
.qhdr{padding:14px 16px 10px;background:var(--surf);border-bottom:1px solid var(--border);display:flex;align-items:center;gap:10px;flex-shrink:0;padding-top:max(14px,env(safe-area-inset-top))}
.btn-back{background:none;border:none;color:var(--dim);font-size:24px;cursor:pointer;padding:4px;line-height:1}
.prog-area{flex:1}
.prog-top{font-size:11px;color:var(--dim);margin-bottom:5px;display:flex;justify-content:space-between;align-items:center}
.prog-bar{height:5px;background:var(--border);border-radius:3px;overflow:hidden}
.prog-fill{height:100%;background:linear-gradient(90deg,#3a5fd9,#6b48d0);border-radius:3px;transition:width .35s ease}
.score-hdr{display:flex;gap:8px;font-size:13px;font-weight:700}
.sg{color:var(--green)} .sr{color:var(--red)}

/* TIMER */
.timer-wrap{width:100%;background:var(--surf);border-bottom:1px solid var(--border);padding:6px 16px;display:none;flex-shrink:0}
.timer-bar{height:6px;background:var(--border);border-radius:3px;overflow:hidden}
.timer-fill{height:100%;border-radius:3px;transition:width .1s linear;background:var(--green)}
.timer-fill.warn{background:var(--yellow)}
.timer-fill.danger{background:var(--red)}
.timer-label{font-size:10px;color:var(--dim);text-align:right;margin-top:3px}

/* CARD */
.card-area{flex:1;min-height:0;padding:16px;overflow-y:auto;-webkit-overflow-scrolling:touch;display:flex;flex-direction:column;gap:13px}
@keyframes slideIn{from{opacity:0;transform:translateX(20px)}to{opacity:1;transform:translateX(0)}}
.card-area{animation:slideIn .18s ease}
.type-badge{display:inline-flex;align-items:center;gap:5px;padding:4px 10px;border-radius:20px;font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.6px;width:fit-content}
.tb-mc{background:rgba(79,124,255,.15);color:var(--acc2);border:1px solid rgba(79,124,255,.3)}
.tb-yn{background:rgba(167,139,250,.15);color:var(--purple);border:1px solid rgba(167,139,250,.3)}
.tb-open{background:rgba(34,197,94,.12);color:var(--green);border:1px solid rgba(34,197,94,.25)}
.q-card{background:var(--surf);border:1px solid var(--border);border-radius:var(--r);padding:18px}
.q-text{font-size:15px;line-height:1.55;font-weight:500}
.multi-hint{margin-top:10px;font-size:12px;color:var(--acc2);font-weight:600}

/* MC OPTIONS */
.opts{display:flex;flex-direction:column;gap:9px}
.opt{width:100%;background:var(--surf);border:2px solid var(--border);border-radius:var(--r);padding:13px 14px;color:var(--text);font-size:14px;line-height:1.4;cursor:pointer;text-align:left;display:flex;align-items:flex-start;gap:11px;word-break:break-word;transition:all .1s}
.opt:active{transform:scale(.985)}
.opt-ltr{min-width:24px;height:24px;background:var(--surf2);border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:11px;font-weight:700;color:var(--dim);flex-shrink:0;margin-top:1px}
.opt.sel{background:rgba(79,124,255,.12);border-color:var(--acc)} .opt.sel .opt-ltr{background:var(--acc);color:#fff}
.opt.ok{background:rgba(34,197,94,.12);border-color:var(--green)} .opt.ok .opt-ltr{background:var(--green);color:#fff}
.opt.bad{background:rgba(239,68,68,.1);border-color:var(--red)} .opt.bad .opt-ltr{background:var(--red);color:#fff}
.opt.missed{background:rgba(34,197,94,.06);border-color:rgba(34,197,94,.35);border-style:dashed}
.opt:disabled{cursor:default}

/* YN */
.yn-row{display:flex;gap:10px}
.yn-btn{flex:1;padding:22px 10px;border:2px solid var(--border);border-radius:var(--r);font-size:17px;font-weight:800;cursor:pointer;background:var(--surf);transition:all .12s;display:flex;flex-direction:column;align-items:center;gap:5px;color:var(--text)}
.yn-btn:active{transform:scale(.96)}
.yn-btn span.ico{font-size:26px}
.yn-btn.ok-ja{background:rgba(34,197,94,.18);border-color:var(--green);color:var(--green)}
.yn-btn.ok-nein{background:rgba(239,68,68,.15);border-color:var(--red);color:var(--red)}
.yn-btn.wrong{opacity:.35}
.yn-btn:disabled{cursor:default}

/* ANSWER reveal */
.answer-box{background:var(--surf);border:1px solid var(--border);border-left:3px solid var(--green);border-radius:var(--r);padding:15px 16px}
.answer-lbl{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:.8px;color:var(--green);margin-bottom:8px}
.answer-txt{font-size:14.5px;line-height:1.55}

/* ACTIONS */
.act-row{padding:12px 16px;display:flex;gap:9px;flex-shrink:0;padding-bottom:max(12px,env(safe-area-inset-bottom))}
.btn-act{flex:1;padding:15px;border:none;border-radius:var(--r);font-size:15px;font-weight:700;cursor:pointer;transition:transform .1s;color:#fff}
.btn-act:active{transform:scale(.97)}
.btn-act:disabled{opacity:.35;cursor:default}
.btn-blue{background:linear-gradient(135deg,#3a5fd9,#6b48d0)}
.btn-grey{background:var(--surf2);border:2px solid var(--border);color:var(--text)}
.btn-green{background:rgba(34,197,94,.16);border:2px solid var(--green);color:var(--green)}
.btn-redo{background:rgba(239,68,68,.12);border:2px solid var(--red);color:var(--red)}

/* FEEDBACK */
.fb{display:none;padding:11px 16px;border-radius:var(--r);margin:0 16px;font-size:13px;font-weight:700;align-items:center;gap:7px;flex-shrink:0}
.fb.show{display:flex}
.fb.ok{background:rgba(34,197,94,.14);color:var(--green);border:1px solid rgba(34,197,94,.3)}
.fb.bad{background:rgba(239,68,68,.1);color:var(--red);border:1px solid rgba(239,68,68,.3)}

/* RESULTS */
#results{align-items:center;justify-content:center;padding:28px 20px;gap:16px;background:radial-gradient(ellipse at 50% 0%,#1a2a5e 0%,var(--bg) 60%)}
.res-emoji{font-size:60px}
.res-title{font-size:26px;font-weight:800;text-align:center;background:linear-gradient(135deg,#7c9fff,#b48cff);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.res-sub{font-size:14px;color:var(--dim);text-align:center}
.score-circle{width:130px;height:130px;position:relative}
.score-circle svg{transform:rotate(-90deg);width:100%;height:100%}
.sc-track{fill:none;stroke:var(--border);stroke-width:8}
.sc-fill{fill:none;stroke-width:8;stroke-linecap:round;transition:stroke-dashoffset 1s ease}
.score-inner{position:absolute;inset:0;display:flex;flex-direction:column;align-items:center;justify-content:center}
.score-pct{font-size:32px;font-weight:800;line-height:1}
.score-lbl{font-size:10px;color:var(--dim);margin-top:2px}
.res-grid{display:grid;grid-template-columns:1fr 1fr;gap:9px;width:100%;max-width:320px}
.res-box{background:var(--surf);border:1px solid var(--border);border-radius:var(--rs);padding:12px;text-align:center}
.res-n{font-size:26px;font-weight:700;line-height:1}
.res-l{font-size:11px;color:var(--dim);margin-top:3px}
.res-box.g .res-n{color:var(--green)} .res-box.r .res-n{color:var(--red)}
.test-badge{display:inline-flex;align-items:center;gap:5px;background:rgba(245,158,11,.15);border:1px solid rgba(245,158,11,.35);color:var(--yellow);border-radius:20px;font-size:11px;font-weight:700;padding:3px 9px;letter-spacing:.5px}

/* CATEGORY */
.cat-grid{display:grid;grid-template-columns:1fr 1fr;gap:7px}
.cat-btn{padding:11px 10px;background:var(--surf);border:2px solid var(--border);border-radius:var(--rs);color:var(--dim);font-size:12.5px;font-weight:600;cursor:pointer;text-align:left;display:flex;justify-content:space-between;align-items:center;gap:6px;transition:all .12s}
.cat-btn:active{transform:scale(.98)}
.cat-btn.on{background:rgba(79,124,255,.14);border-color:var(--acc);color:var(--acc2)}
.cat-cnt{font-size:11px;font-weight:700;color:var(--dimmer);background:var(--surf2);border-radius:10px;padding:1px 7px;min-width:22px;text-align:center;flex-shrink:0}
.cat-btn.on .cat-cnt{color:var(--acc2)}
.badge-row{display:flex;gap:8px;align-items:center;flex-wrap:wrap}
.cat-pill{display:inline-flex;align-items:center;padding:4px 10px;border-radius:20px;font-size:11px;font-weight:700;letter-spacing:.4px;background:var(--surf2);color:var(--dim);border:1px solid var(--border)}
</style>
</head>
<body>

<div id="js-warning">
  <div class="jw-ic">&#9888;&#65039;</div>
  <h2>Bitte in Safari oder Chrome &ouml;ffnen</h2>
  <p>Diese Ansicht (Datei-Vorschau, WhatsApp oder Mail) f&uuml;hrt kein JavaScript aus &mdash; darum reagieren die Kn&ouml;pfe nicht.</p>
  <div class="jw-step"><b>iPhone:</b> Teilen-Symbol antippen &rarr; &bdquo;In Safari &ouml;ffnen&ldquo;. Danach Teilen &rarr; &bdquo;Zum Home-Bildschirm&ldquo; f&uuml;r ein App-Icon.</div>
  <div class="jw-step"><b>Android:</b> Men&uuml; &#8942; &rarr; &bdquo;In Chrome &ouml;ffnen&ldquo;.</div>
</div>

<!-- START -->
<div id="start" class="screen active">
  <div class="logo">
    <div class="logo-icon">&#127959;&#65039;</div>
    <div><div class="app-title">Altenburg Lernkarten</div>
    <div class="app-sub">VOB &middot; Baurecht &middot; B-Plan &middot; Baustelle</div></div>
  </div>
  <div class="stats-row">
    <div class="stat"><div class="stat-n" id="s-total">0</div><div class="stat-l">Karten</div></div>
    <div class="stat"><div class="stat-n" id="s-last">&mdash;</div><div class="stat-l">Letzter Score</div></div>
    <div class="stat"><div class="stat-n" id="s-best">&mdash;</div><div class="stat-l">Bestleistung</div></div>
  </div>
  <div class="sect">
    <div class="sect-lbl">Kategorie</div>
    <div class="cat-grid" id="cat-grid"></div>
  </div>
  <div class="sect">
    <div class="sect-lbl">Kartentyp</div>
    <div class="btn-row">
      <button class="tog on" data-mode="all" onclick="setMode(this)">Alle</button>
      <button class="tog" data-mode="ankreuzen" onclick="setMode(this)">Ankreuzen</button>
      <button class="tog" data-mode="abfragen" onclick="setMode(this)">Abfragen</button>
    </div>
  </div>
  <div class="sect">
    <div class="sect-lbl">Reihenfolge</div>
    <div class="btn-row">
      <button class="tog on" data-order="shuffle" onclick="setOrder(this)">Zuf&auml;llig</button>
      <button class="tog" data-order="fixed" onclick="setOrder(this)">Original</button>
    </div>
  </div>
  <button class="btn-big btn-primary" onclick="startQuiz(false)">Lernen starten &rarr;</button>
  <button class="btn-big btn-test" onclick="startQuiz(true)">&#9201; Testmodus (30s/Karte)</button>
</div>

<!-- QUIZ -->
<div id="quiz" class="screen">
  <div class="qhdr">
    <button class="btn-back" onclick="goHome()">&#8249;</button>
    <div class="prog-area">
      <div class="prog-top">
        <span id="q-cnt">1 / 1</span>
        <span id="q-badge"></span>
      </div>
      <div class="prog-bar"><div class="prog-fill" id="prog"></div></div>
    </div>
    <div class="score-hdr">
      <span class="sg">&#10003;<span id="h-ok">0</span></span>
      <span class="sr">&#10007;<span id="h-bad">0</span></span>
    </div>
  </div>
  <div class="timer-wrap" id="timer-wrap">
    <div class="timer-bar"><div class="timer-fill" id="timer-fill"></div></div>
    <div class="timer-label" id="timer-lbl">30s</div>
  </div>
  <div class="card-area" id="card-area"></div>
  <div class="fb" id="fb"></div>
  <div class="act-row" id="actions"></div>
</div>

<!-- RESULTS -->
<div id="results" class="screen">
  <div class="res-emoji" id="r-emoji">&#127881;</div>
  <div class="res-title" id="r-title">Ergebnis</div>
  <div class="res-sub" id="r-sub"></div>
  <div class="score-circle">
    <svg viewBox="0 0 120 120">
      <circle class="sc-track" cx="60" cy="60" r="52"/>
      <circle class="sc-fill" id="sc-arc" cx="60" cy="60" r="52" stroke="#4f7cff" stroke-dasharray="326.7" stroke-dashoffset="326.7"/>
    </svg>
    <div class="score-inner">
      <div class="score-pct" id="r-pct">0%</div>
      <div class="score-lbl">Richtig</div>
    </div>
  </div>
  <div class="res-grid">
    <div class="res-box g"><div class="res-n" id="r-ok">0</div><div class="res-l">Richtig / Gewusst</div></div>
    <div class="res-box r"><div class="res-n" id="r-bad">0</div><div class="res-l">Falsch / Offen</div></div>
  </div>
  <button class="btn-big btn-primary" onclick="startQuiz(isTestMode)" style="max-width:320px">Nochmal &rarr;</button>
  <button class="btn-big" onclick="goHome()" style="max-width:320px;background:none;border:2px solid var(--border);color:var(--dim);margin-top:6px">Startseite</button>
</div>

<script>
window.onerror=function(m,s,l){try{var b=document.createElement('div');b.style.cssText='position:fixed;left:0;right:0;bottom:0;z-index:99999;background:#7f1d1d;color:#fff;font:13px/1.45 -apple-system,system-ui,sans-serif;padding:12px 14px;white-space:pre-wrap';b.textContent='Fehler: '+m+(l?' (Zeile '+l+')':'');document.body.appendChild(b);}catch(e){}};

const CARDS = JSON.parse("[{\"type\":\"open\",\"q\":\"Nennen Sie die drei zentralen Vergabearten der VOB/A und beschreiben Sie in Stichworten die wesentlichen Unterschiede\",\"a\":\"Beschränkt - bis 100.000, nur Ausgewählte dürfen Angebot abgeben\\nÖffentlich - ab 100.000, jeder darf ein Angebot abgeben\\nFreihändig - bis 10.000, wird direkt vergeben\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Eine Vergabefrist nach VOB/A\",\"options\":[\"dient zur zur rechnerischen Kontrolle der angebotenen Endsumme\",\"dient zur telefonischen Erläuterung der abgegebenen Angebotspreise\",\"dauert 5 Wochen nach der Submission\"],\"correct\":[0],\"a\":\"dient zur zur rechnerischen Kontrolle der angebotenen Endsumme\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Bei der Submission nach VOB/A\",\"options\":[\"spricht der Architekt mit dem Bauherrn die Auftragsvergabe ab\",\"öffnet die ausschreibende Stelle die Angebote und fertigt ein Protokoll\",\"werden die Einheitspreise der Anbieter verlesen\"],\"correct\":[1],\"a\":\"öffnet die ausschreibende Stelle die Angebote und fertigt ein Protokoll\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Aus den Angebotsunterlagen:\",\"options\":[\"darf jeder Interessierte den Endpreis erfahren\",\"dürfen Bieter die Endsumme der Mitbieter erfahren\",\"dürfen jederzeit Kopien veröffentlicht werden\"],\"correct\":[1],\"a\":\"Aus den Angebotsunterlagen:\\ndürfen Bieter die Endsumme der Mitbieter erfahren\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Für den Bau einer Polizeidienststelle für ca. 3 Mio. Euro wählt der Architekt\",\"options\":[\"die freihändige Vergabe\",\"die öffentliche Ausschreibung\",\"die beschränkte Ausschreibung\"],\"correct\":[1],\"a\":\"Für den Bau einer Polizeidienststelle für ca. 3 Mio. Euro wählt der Architekt\\ndie öffentliche Ausschreibung\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Nach welchen Grundsätzen soll vergeben werden?\",\"options\":[\"der Auftragnehmer mit den besten Mitarbeitern erhält den Zuschlag\",\"der Auftragnehmer mit der billigsten Endsumme erhält den Zuschlag\",\"der fachkundigste, zuverlässigste und sachkuundigste Unternehmer erhält den Zuschlag zu angemessenen Preisen\"],\"correct\":[2],\"a\":\"Nach welchen Grundsätzen soll vergeben werden?\\nder fachkundigste, zuverlässigste und sachkuundigste Unternehmer erhält den Zuschlag zu angemessenen Preisen\",\"cat\":\"vob_a\"},{\"type\":\"open\",\"q\":\"Wofür eignet sich eine beschränkte Ausschreibung nach VOB/A besonders gut? Nennen Sie ein Beispiel\",\"a\":\"Besondere / dringende Dienstleistungen unter 100.000€, kleine Um und Erweitertungsarbeiten\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Warum sollen Bauleistungen mit der Lieferung der zur Leistung gehörigen Baustoffe vergeben werden?\",\"options\":[\"weil dann die Gewährleistung weniger problematisch ist\",\"weil der Endpreis billiger wird\",\"weil bei der Lieferung der Baustoffe die Frachtkosten entfallen\"],\"correct\":[0],\"a\":\"weil dann die Gewährleistung weniger problematisch ist\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Großaufträge sollen nach Losen vergeben werden\",\"options\":[\"weil die Prüfung und Abrechnung dadurch einfacher wird\",\"weil die Firmen sich dabei gegenseitig Geräte und Maschinen ausleihen können\",\"weil dadurch die Bauwirtschaft insgesamt nicht durch ruinösen Wettbewerb geschädigt wird\"],\"correct\":[2],\"a\":\"weil dadurch die Bauwirtschaft insgesamt nicht durch ruinösen Wettbewerb geschädigt wird\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Warum darf z.B. die Bundeswehr nicht am Wettbewerb für Bauleistungen (z.B. Abbrucharbeiten) teilnehmen?\",\"options\":[\"weil sie die Frauenquote immer noch nicht erfüllt\",\"weil sie über kein entsprechendes Arbeitsgerät verfügt\",\"weil die Bundeswehr aus Steuern finanziert wird und dadurch Vorteile beim Wettbewerb hat\"],\"correct\":[2],\"a\":\"weil die Bundeswehr aus Steuern finanziert wird und dadurch Vorteile beim Wettbewerb hat\",\"cat\":\"vob_a\"},{\"type\":\"open\",\"q\":\"Wer ist bei eine Bauvergabe nach VOB/A an diese Vergabevorschriften gebunden?\",\"a\":\"der öffentliche Auftraggeber\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Wann kann eine beschränke Ausschreibung nach VOB/A aufgehoben werden?\\nWenn:\",\"options\":[\"Kein Angebot eingegangen ist, das den Ausschreibungsbedingungen entspricht\",\"Kein Bieter die erforderliche Leistungsfähigkeit besitzt\",\"Die Vergabeunterlagen grundlegend geändert werden müssen\",\"Andere schwerwiegende Gründe bestehen.\"],\"correct\":[0,2,3],\"a\":\"Wenn:\\nKein Angebot eingegangen ist, das den Ausschreibungsbedingungen entspricht\\nDie Vergabeunterlagen grundlegend geändert werden müssen\\nAndere schwerwiegende Gründe bestehen.\",\"cat\":\"vob_a\"},{\"type\":\"yn\",\"q\":\"Kann ein privater Bauherr bei der Vergabe von Bauleistungen die Einhaltung der VOB/A von seinem Bauleiter verlangen?\",\"yn\":\"JA\",\"a\":\"JA\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Der Angebotspreis wird ermittelt\",\"options\":[\"über die geschätzten Mengeneinheiten x Einzelpreis\",\"über die errechneten Mengen x Sonderangebotspreis\",\"über die Einheitspreise x errechneter Menge\"],\"correct\":[2],\"a\":\"über die Einheitspreise x errechneter Menge\",\"cat\":\"vob_a\"},{\"type\":\"open\",\"q\":\"Wofür eignet sich eine beschränkte Ausschreibung nach VOB/A besonders gut? Nennen Sie ein Beispiel.\",\"a\":\"Reperatur\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"Die Angebote sind zu einem bestimmten Termin einzureichen. Wie nennt man diesen Termin?\",\"options\":[\"Angebotsvorlagetermin\",\"Eröffnungstermin (Submissionstermin)\",\"Angebote können jederzeit bis zum Baubeginn vorgelegt werden\"],\"correct\":[1],\"a\":\"Eröffnungstermin (Submissionstermin)\",\"cat\":\"vob_a\"},{\"type\":\"mc\",\"q\":\"In den Vergabeunterlagen sind grundsätzliche Fristen bekannt zu geben, Welche Fristen wären unbedingt zu nennen?\",\"options\":[\"Voranmeldungsfrist\",\"Angebotsfrist\",\"Preisfrist\",\"Ausführungsfrist\",\"Zuschlagsfrist\"],\"correct\":[1,3,4],\"a\":\"Angebotsfrist\\nAusführungsfrist\\nZuschlagsfrist\",\"cat\":\"vob_a\"},{\"type\":\"open\",\"q\":\"Worin liegt der zentrale Unterschied zwischen einer öffentlichen AUsschreibung und einer beschränkten Ausschreibung?\",\"a\":\"Öffentliche Ausschreibung richtet sich an jedermann\\nBeschränkte Ausschreibung richtet sich an ausgewählten Bieterkreis\",\"cat\":\"vob_a\"},{\"type\":\"open\",\"q\":\"Was versteht man unter Ausgewogenheit der VOB und welches Ereignis ist hierbei von besonderer Bedeutung?\",\"a\":\"Die Abnahme. Vorher schuldet der AN ein mangelfreies Bauwerk, danch muss AG Mangel als vor der Abnahme beweisen\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"In den zusätzlichen Vertragsunterlagen wird geregelt\",\"options\":[\"wie die Kosten für den Verbrauch des Bauwassers abgerechnet werden\",\"wer den Bauzaun aufstellen muss\",\"wer die Kosten für die Unfallversicherung der Arbeitnehmer übernimmt\"],\"correct\":[0],\"a\":\"wie die Kosten für den Verbrauch des Bauwassers abgerechnet werden\",\"cat\":\"vob_b\"},{\"type\":\"yn\",\"q\":\"Kann der Auftraggeber in einem VOB/B Vertrag bis zur Vollendung der Leistung jederzeit den Vertrag kündigen?\",\"yn\":\"JA\",\"a\":\"JA\",\"cat\":\"vob_b\"},{\"type\":\"yn\",\"q\":\"Ist der private Bauherr in einem Bauvertrag nach VOB/B an die VOB/C gebunden?\",\"yn\":\"JA\",\"a\":\"JA\",\"cat\":\"vob_b\"},{\"type\":\"open\",\"q\":\"Bis zu welchem Prozentsatz gemäß VOB/B gelten die vereinbarten Einheitspreise bei Abweichungen von der vorgesehenen Leistung?\",\"a\":\"10 %\",\"cat\":\"vob_b\"},{\"type\":\"yn\",\"q\":\"Hat der AN bei Schäden seiner erbrachten Leistung auf Grund von höherer Gewalt Anspruch auf Vergütung vor der vereinbarten Abnahme?\",\"yn\":\"JA\",\"a\":\"JA\",\"cat\":\"vob_b\"},{\"type\":\"yn\",\"q\":\"Darf der AN den Vertrag kündigen, wenn der AG eine ihm obliegenden Handlung unterlässt?\",\"yn\":\"JA\",\"a\":\"JA\",\"cat\":\"vob_b\"},{\"type\":\"yn\",\"q\":\"Kann eine vereinbarte Abnahme durch den AG verweigert werden wenn wesentliche Mängel bestehen?\",\"yn\":\"JA\",\"a\":\"JA\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Wozu dienen Sicherheitsleitungen im VOB/B Vertrag?\",\"options\":[\"Vor Insolvenz des AN\",\"Zur Sicherung von Mängelansprüchen\",\"Zur Abgleichung von Überzahlungen\"],\"correct\":[1],\"a\":\"Zur Sicherung von Mängelansprüchen\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Was gilt bei Widersprüchen in VOB Vertrag?\",\"options\":[\"Die Leistungsbeschreibung\",\"Die besonderen Vertragsbedingungen\",\"Die allgemeinen Geschäftsbedingungen\",\"Die Vergabe gemäß § 310 BGB\",\"Etwaige zusätzliche Vertragsbedingungen\"],\"correct\":[0,1,4],\"a\":\"Die Leistungsbeschreibung\\nDie besonderen Vertragsbedingungen\\nEtwaige zusätzliche Vertragsbedingungen\",\"cat\":\"vob_b\"},{\"type\":\"yn\",\"q\":\"Muss der AN nicht vereinbarte Leistungen,die zur Ausführung der vertraglichen Leistung erforderlich werden Ausführen?\",\"yn\":\"JA\",\"a\":\"JA\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Wer darf Änderungen des Bauentwurfs anordnen?\",\"options\":[\"Der Bauherr\",\"Das Bauordnungsamt\",\"Die BGBau\",\"Der Nachunternehmer\"],\"correct\":[0],\"a\":\"Der Bauherr\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Wonach wird die vertragliche Leistung vergütet?\",\"options\":[\"Ggf durch Pauschalsummen\",\"Durch die Einheitspreise und den tatsächlich ausgeführten Leistungen\",\"Ggf durch Stundenlohnsätze\"],\"correct\":[1],\"a\":\"Durch die Einheitspreise und den tatsächlich ausgeführten Leistungen\",\"cat\":\"vob_b\"},{\"type\":\"yn\",\"q\":\"Muss der AG Leistungen, die vom AN ohne Anordnung erbracht wurden vergüten?\",\"yn\":\"NEIN\",\"a\":\"NEIN\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Wer hat für die Aufrechterhaltung, der allgemeine Ordnung auf der Baustelle zu sorgen?\",\"options\":[\"Der Auftragnehmer\",\"Der Handwerker vor Ort\",\"Der Auftraggeber\"],\"correct\":[2],\"a\":\"Der Auftraggeber\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Wer ist für die Erfüllung der gesetzlichen, behördlichen und berufsgenossenschaftlichen Verpflichtungen gegenüber den Arbeitnehmern verantwortlich?\",\"options\":[\"Allein der Auftraggeber\",\"Der SiGeKo\",\"Die Aufsichtsperson der BGBau\",\"Allein der Auftragnehmer\"],\"correct\":[3],\"a\":\"Allein der Auftragnehmer\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Was hat der AG, wenn nichts anderes vereinbart wurde, dem AN unentgeltlich zur Verfügung zu stellen?\",\"options\":[\"Notwendige Lager- und Arbeitsplätze auf der Baustelle\",\"Vorhandenen Zufahrtswege\",\"Vorhandenen Anschlüsse für Wasser und Energie\"],\"correct\":[0,1,2],\"a\":\"Notwendige Lager- und Arbeitsplätze auf der Baustelle\\nVorhandenen Zufahrtswege\\nVorhandenen Anschlüsse für Wasser und Energie\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Wer darf Änderungen des Bauentwurfs anordnen?\",\"options\":[\"Der Architekt\",\"Der AG\",\"Der Bauleiter\"],\"correct\":[1],\"a\":\"Der AG\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Welche Leistungen werden durch die vereinbarten Preise abgegolten?\",\"options\":[\"Nur die handwerklichen Leistungen inclusive An- und Abfahrten von der Baustelle\",\"Nur die Ausführung der Bauleistung. Die Materialkosten werden vom AG vergütet.\",\"Sämtliche Kosten die für die Erstellung der vereinbarten Leistungspositionen entstehen\"],\"correct\":[2],\"a\":\"Sämtliche Kosten die für die Erstellung der vereinbarten Leistungspositionen entstehen\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Ein AN erbringt eine Leistung ohne Auftrag. Hat der AN Anspruch auf Vergütung?\",\"options\":[\"Ja, wenn die Leistung zur Erfüllung des Auftrages notwendig war,und dem mutmaßlichen Wille des AG entsprach sowie angezeigt wurde.\",\"Ja, da erkennbar war, dass die Leistung erbracht wurde.\",\"Nein, er muss zudem die Leistung rückgängig machen und haftet für entstandenen Schäden.\"],\"correct\":[0,2],\"a\":\"Ja, wenn die Leistung zur Erfüllung des Auftrages notwendig war,und dem mutmaßlichen Wille des AG entsprach sowie angezeigt wurde.\\nNein, er muss zudem die Leistung rückgängig machen und haftet für entstandenen Schäden.\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Muss der AN Leistungen, die er an Nachunternehmer weitergibt der VOB Teil B und C zugrunde legen?\",\"options\":[\"Grundsätzlich ja\",\"Ja, wenn seinem Auftrag die VOB Teil B und C zugrunde liegt.\",\"Nein, auch wenn seinem Auftrag die VOB Teil B und C zugrunde liegt.\"],\"correct\":[1],\"a\":\"Ja, wenn seinem Auftrag die VOB Teil B und C zugrunde liegt.\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Was steht dem AN bei Kündigung durch den AG ohne sein Verschulden zu?\",\"options\":[\"Die vereinbarte Vergütung ohne Einschränkung.\",\"Die vereinbarte Vergütung abzüglich von Wagnis und Gewinn.\",\"Die vereinbarte Vergütung ohne Einschränkung für die bereits erbrachten Leistungen\",\"Die vereinbarte Vergütung ggf. jedoch mit Einschränkungen\"],\"correct\":[3],\"a\":\"Die vereinbarte Vergütung ggf. jedoch mit Einschränkungen\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Wie wird eine Fristverlängerung bei Behinderung durch den AG berechnet?\",\"options\":[\"Durch Dauer der Behinderung\",\"Durch Dauer der Behinderung abzüglich von Wochenenden und Feiertagen.\",\"Durch Dauer der Behinderung zuzüglich eines Aufschlages für die Wiederaufnahme\"],\"correct\":[2],\"a\":\"Durch Dauer der Behinderung zuzüglich eines Aufschlages für die Wiederaufnahme\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Der AN hat ohne ein Verschulden des AG den Vertrag gekündigt. Was steht dem AN in diesem besonderen Fall zu und was hat er ggf. zu leisten?\",\"options\":[\"Die bisherigen Leistungen sind nach den Vertragspreisen abzurechnen.\",\"Der AG hat Anspruch auf eine angemessene Entschädigung\",\"Dem AN steht bei schuldhafter Kündigung nichts zu und ist zu Schadensersatz gegenüber dem AG verpflichtet\"],\"correct\":[1],\"a\":\"Der AG hat Anspruch auf eine angemessene Entschädigung\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Wer haftet gegenüber dem AG für die zu erbringenden Leistungen bei Einschaltung eines Nachunternehmers dem der AG zugestimmt hat?\",\"options\":[\"Da der AG der Einschaltung eines Nachunternehmers zugestimmt hat haftet der Nachunternehmer.\",\"Weiterhin der AN.\",\"AN und Nachunternehmer zu gleichen Teilen\"],\"correct\":[1],\"a\":\"Weiterhin der AN.\",\"cat\":\"vob_b\"},{\"type\":\"yn\",\"q\":\"Ist eine Kündigung durch den AN rechtsgültig wenn der AG eine fällige Zahlung nicht leistet?\",\"yn\":\"NEIN\",\"a\":\"NEIN\",\"cat\":\"vob_b\"},{\"type\":\"yn\",\"q\":\"Kann der AG Kosten für notwendige Unterlagen zur Erfüllung des Auftrags dem AN in Rechnung stellen?\",\"yn\":\"NEIN\",\"a\":\"NEIN er muss diese Unterlagen gebührenfrei zur Verfügung stellen\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Muss der AN grundsätzlich Anordungen des AG, die zur Vertragserfüllung notwendig sind, befolgen?\",\"options\":[\"Ja\",\"Nein, wenn er die Anordnung nicht für notwendig hält\",\"Nein, wenn er die Anordnung nicht für notwendig hält und Bedenken angemeldet hat\",\"Ja, auch wenn er die Anwendung nicht für notwendig hält und Bedenken angemeldet hat\"],\"correct\":[3],\"a\":\"Ja, auch wenn er die Anwendung nicht für notwendig hält und Bedenken angemeldet hat\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"Kann der AG vereinbarte Vertragsstrafen bei Verschulden durch den AN auch nach der Abnahme noch verlangen?\",\"options\":[\"Ja auch nach der Abnahme kann der AG die vereinbarte Vertragsstrafe noch verlangen\",\"Nein, nach der Abnahme kann der AG keine Forderungen mehr stellen\",\"Ja, wenn der AG die bei der Abnahme vorbehalten hat\"],\"correct\":[1],\"a\":\"Nein, nach der Abnahme kann der AG keine Forderungen mehr stellen\",\"cat\":\"vob_b\"},{\"type\":\"open\",\"q\":\"Wie lange können Sicherheitsleistungen einbehalten werden?\",\"a\":\"Bis zum Ablauf der Gewährleistung\",\"cat\":\"vob_b\"},{\"type\":\"mc\",\"q\":\"In einem Vertrag wir eine nicht vereinbarte Leistung gefordert. Die Leistung wird vom AN erbracht. Hat der AN Anspruch auf Vergütung der Leistung?\",\"options\":[\"Ja, da der An erkennbar die Leistung erbracht hat.\",\"Ja. wenn der AN vor Beginn der Leistung seine Asprüche ankündigt.\"],\"correct\":[1],\"a\":\"Ja , wenn der AN vor Beginn der Leistung seine ANsprüche ankündigt\",\"cat\":\"vob_b\"},{\"type\":\"open\",\"q\":\"Wo sind Allgemeine technischen Vertragsbedingungen für Bauleistungen geregelt?\",\"a\":\"VOB Teil C\",\"cat\":\"vob_c\"},{\"type\":\"open\",\"q\":\"Wo sind Nebenleistungen für Baugewerke in Durchführung geregelt?\",\"a\":\"VOB / C\",\"cat\":\"vob_c\"},{\"type\":\"open\",\"q\":\"Wie nennt man die Vertragsart die üblicherweise bei Bauarbeiten vorliegt?\",\"a\":\"Werkvertrag\",\"cat\":\"bgb\"},{\"type\":\"mc\",\"q\":\"Wer hat das Entdeckerrecht nach § 984 BGB bei der Entdeckung von z.B. Kunstschätzen auf der Baustelle?\",\"options\":[\"Der jeweilige Handwerker der den Kunstschatz entdeckt\",\"Der jeweilige AN der zu dem Zeitpunkt auf der Baustelle ist.\",\"Der Bauleiter nach LBO\",\"Der AG\"],\"correct\":[3],\"a\":\"Der AG\",\"cat\":\"bgb\"},{\"type\":\"open\",\"q\":\"Nennen Sie den wesentlichen Unterschied zwischen einem Rahmenterminplan und einem Bauzeitenplan\",\"a\":\"Rahmenterminplan: Grundlagen sind Leistungsphasen der HOAI\\nBauzeitenplan: Bezieht sich nur auf die Bauleistung\",\"cat\":\"hoai\"},{\"type\":\"open\",\"q\":\"In einem B-Plan finden sie in einem \\\"Kasten\\\" folgende Angaben. Beschreiben Sie kurz, was diese aussagen.\\nWA?\\nGRZ 0,25\\nI?\\nO?\",\"a\":\"WA? = allgemeines Wohngebiet\\nGRZ 0,25 = Grundflächenzahl, 0,25 % darf bebaut werden\\nI? = ein Vollgeschoss ist erlaubt\\nO? = offene Bauweise\",\"cat\":\"bauplanung\"},{\"type\":\"open\",\"q\":\"In welcher Verordnung ist die bauliche Nutzung der Grundstücke geregelt?\",\"a\":\"Baunutzungsverordnung\",\"cat\":\"bauplanung\"},{\"type\":\"open\",\"q\":\"Weiterhin können Sie folgene Buchstaben in dem Kasten (B-Plan) finden. Welche Bedeutung haben diese Buchstaben?\\nE\\nR\\nD\\nO\",\"a\":\"E Einfamilienhaus\\nR Reihenhaus\\nD Doppelhaus\\nO Offene Bauweise\",\"cat\":\"bauplanung\"},{\"type\":\"open\",\"q\":\"Beschreiben Sie kurz den Unterschied zwischen einer Baugrenze und Baulinie innerhalb eines B-Plans.\",\"a\":\"An die Baulinie muss gebaut werden\\nDie Baugrenze darf nicht überschritten werden\",\"cat\":\"bauplanung\"},{\"type\":\"open\",\"q\":\"Was bedeuten die nachfolgenden Angaben in einem B-Plan?\\nWS\\nWR\\nWA\\nWB\\nMD\\nMK\\nSO\",\"a\":\"WS Kleinsiedlungsgebiet\\nWR Reines Wohngebiet\\nWA Allgemeines Wohngebiet\\nWB Besonderes Wohngebiet\\nMD Dorfgebiet\\nMK Kerngebiet\\nSO Sondergebiet\",\"cat\":\"bauplanung\"},{\"type\":\"open\",\"q\":\"In einem B-Plan ist grundsätzlich ein \\\"Kasten\\\" zu finden mit Angaben zum Grundstück. In diesem Kästchen finden Sie zum Beispiel:\\nRömische Zahlen. Welche Bedeutung haben sie?\\nZ.B. die Angabe GRZ 0,35 welche Bedeutung hat diese Angabe?\\nEine Winkelangabe. Auf was bezieht sich diese?\\nZ.B. die Angabe SD. Was bedeutet diese?\",\"a\":\"Römische Zahlen = ANzahl der Vollgeschosse\\nGRZ = Grundflächenzahl 35% des Grundstücks dürfen bebaut werden\\nWinkelangabe = Dachneigung\\nSD ) Satteldach\",\"cat\":\"bauplanung\"},{\"type\":\"open\",\"q\":\"Welchen Rechtscharakter hat ein B-Plan?\",\"a\":\"binden\",\"cat\":\"bauplanung\"},{\"type\":\"open\",\"q\":\"Welcher Plan ist vor einem B-Plan vorzuschalten?\",\"a\":\"Flächennutzungsplan\",\"cat\":\"bauplanung\"},{\"type\":\"open\",\"q\":\"Welchen Rechtscharakter hat dieser Plan? (Flächennuutzungsplan)\",\"a\":\"nicht verbindlich\",\"cat\":\"bauplanung\"},{\"type\":\"open\",\"q\":\"Welches Gesetz legt die Vorgaben für eine Bebauung außerhalb eines B-Plans fest?\",\"a\":\"Baugesetzbuch\",\"cat\":\"bauplanung\"},{\"type\":\"open\",\"q\":\"Wie groß ist der erlaubte minimaler Abstand zwischen Wohngebäude und Nachbarschaftsgrenze?\",\"a\":\"3 m\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"Welche Gebäudearten sind innerhalb dieser Fläche ( 3 m Abstand zwischen Wohngebäude und Nachbarschaftsgrenze) erlaubt? Nennen Sie zwei Beispiele sowie die maximale Länge und Höhe an der Nachbarschaftsgrenze.\",\"a\":\"Erlaubt sind nicht bewohnbare Anbauten wie Carport oder Schuppen\\nLänge 9m\\nHöhe 3 m\",\"cat\":\"bauordnung\"},{\"type\":\"mc\",\"q\":\"Welche der folgenden Maßnahme sind Antrags bzw. Bauantragspflichtig?\",\"options\":[\"Umfangreiche Renovierungsarbeiten an bestehenden Gebäude\",\"Einbau einer neuen Dachgaube\",\"Änderung der Nutzung eines Wohnhauses\",\"Herkömmliche Garagen innerhalb eines B-Plans\",\"Abriss eines abgängigen alten Hauses\"],\"correct\":[1,2,4],\"a\":\"Einbau einer neuen Dachgaube\\nÄnderung der Nutzung eines Wohnhauses\\nAbriss eines abgängigen alten Hauses\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"In welcher Verordnung werden die Aufgaben der am Bau Beteiligten geregelt?\",\"a\":\"Landesbauordnung\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"Wer hat gegenüber einem Bauleiter auf Baustellen ein Weisungsrecht?\",\"a\":\"Bauherr\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"Wer unterschreibt Bauaufträge für die Ausführung einer Baumaßnahme?\",\"a\":\"Bauherr\",\"cat\":\"bauordnung\"},{\"type\":\"mc\",\"q\":\"Welche Verordnungen sind ggf. bei der Planung eines Dorfgemeinschaftshauses zu beachten?\",\"options\":[\"Versammlungsstättenverordnung\",\"Arbeitsstättenverordnung\",\"Baununtzungsverordnung\"],\"correct\":[0,1,2],\"a\":\"Versammlungsstättenverordnung\\nArbeitsstättenverordnung\\nBaununtzungsverordnung\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"In welcher Verordnung ist vorgegeben, wer Bauvorlageberechtigt ist?\",\"a\":\"Landesbauordnung\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"In welcher Verordnung sind die Abstandsflächen und Abstände einer Bebauung geregelt?\",\"a\":\"Landesbauordnung\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"In welcher Verordnung sind die erforderlichen Unterlagen für einen Bauantrag vorgegeben?\",\"a\":\"Bauvorlageverordnung\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"Welche der nach LBO am Bau beteiligten darf Änderungen an den Bauantragsunterlagen vornehmen?\",\"a\":\"bauvorlageberechtigter Entwurfsverfasser (Planer)\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"Nenne Sie die Vier gemäß LBO am Bau Beteiligten.\",\"a\":\"Bauherr\\nEntwurfsverfasser (Planer)\\nBauleiter\\nBauunternehmer\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"Nach welcher Verordnung sind SIe als Hochbautechniker für einen Bauantrag Vorlageberechtigt?\",\"a\":\"LBO Paragraph 65\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"In welcher Verordnung ist der Mindestabstand von 3 Metern zur Nachbarschaftsgrenze festgelegt?\",\"a\":\"Landesbauordnung\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"Wem sind in Schleswig-Holstein die Anträge für Baumaßnahmen zur Genehmigung vorzulegen?\",\"a\":\"untere Bauaufsichtsbehörde / Bauordnungsamt\",\"cat\":\"bauordnung\"},{\"type\":\"open\",\"q\":\"Nach welchem Recht ist die Baustellenverordnung geregelt?\",\"a\":\"EG-Recht\",\"cat\":\"arbeitsschutz\"},{\"type\":\"open\",\"q\":\"Wer muss die Maßnahmen zur Umsetzung der BaustellVo treffen?\",\"a\":\"Der Bauherr oder der von ihm beauftragte Dritte\",\"cat\":\"arbeitsschutz\"},{\"type\":\"open\",\"q\":\"Wer ist verantwortlich für die allgemeine Sicherheit auf Baustellen und wer ggf. noch?\",\"a\":\"Der Bauherr oder der von ihm beauftragte Dritte (SiGeKo)\",\"cat\":\"arbeitsschutz\"},{\"type\":\"open\",\"q\":\"In welcher Verordnung finden Sie die Vorgaben zur Vorhaltung und Einrichtung von Sozialräumen auf Baustellen?\",\"a\":\"Arbeitsstättenverordnung\",\"cat\":\"arbeitsschutz\"},{\"type\":\"open\",\"q\":\"Bei der Durchführung eines Bauvorhabens im Bestand nehmen Sie als zuständiger Bauleiter in einem Raum einen süßlichen Marzipanartigen Geruch war. Um was könnte es sich handeln und wie reagieren Sie im ersten Schritt?\",\"a\":\"PAK, Bauarbeiten sofort stoppen, Baustelle räumen und schließen und Beprobung durchführen\",\"cat\":\"arbeitsschutz\"},{\"type\":\"open\",\"q\":\"Wer von den am Bau Beteilitgten ist zuständig für die Abnahme von Gerüsten?\",\"a\":\"Der Gerüstbauer\",\"cat\":\"arbeitsschutz\"},{\"type\":\"yn\",\"q\":\"Kann ein Bauherr das Tragen von der PSA Bauhelm grundsätzlich verlangen?\",\"yn\":\"JA\",\"a\":\"JA\",\"cat\":\"arbeitsschutz\"},{\"type\":\"mc\",\"q\":\"Wen hat der Bauherr zur Umsetzung der BaustellVo zu beauftragen?\",\"options\":[\"Das Bauordnungsamt\",\"Die Berufsgenossenschaft\",\"Den SiGeKo\"],\"correct\":[2],\"a\":\"Den SiGeKo\",\"cat\":\"arbeitsschutz\"},{\"type\":\"open\",\"q\":\"Nenne vier klassische Bauschadstoffe im Hochbau\",\"a\":\"Blei\\nAsbest\\nPAK\\nKMF\",\"cat\":\"arbeitsschutz\"}]");

/* ---- safe storage (iOS file:// throws) ---- */
var _mem={};
var Store={
  get:function(k){try{var v=localStorage.getItem(k);return v===null?(_mem.hasOwnProperty(k)?_mem[k]:null):v;}catch(e){return _mem.hasOwnProperty(k)?_mem[k]:null;}},
  set:function(k,v){_mem[k]=String(v);try{localStorage.setItem(k,v);}catch(e){}}
};

/* ---- helpers ---- */
function esc(s){return String(s).replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;').replace(/"/g,'&quot;');}
function nl2br(s){return esc(s).replace(/\n/g,'<br>');}
function shuffle(a){const r=a.slice();for(let i=r.length-1;i>0;i--){const j=Math.floor(Math.random()*(i+1));const t=r[i];r[i]=r[j];r[j]=t;}return r;}
function $(id){return document.getElementById(id);}

/* ---- state ---- */
let cards=[],idx=0,correct=0,wrong=0,mode='all',order='shuffle';
let sel=new Set(),answered=false,isTestMode=false,category='all';
let timerInt=null,timerLeft=0;const TIMER_SECS=30;

function setMode(b){document.querySelectorAll('[data-mode]').forEach(x=>x.classList.remove('on'));b.classList.add('on');mode=b.dataset.mode;}
function setOrder(b){document.querySelectorAll('[data-order]').forEach(x=>x.classList.remove('on'));b.classList.add('on');order=b.dataset.order;}

const CATS=[
  {k:'vob_a',label:'VOB/A · Vergabe',short:'VOB/A'},
  {k:'vob_b',label:'VOB/B · Bauvertrag',short:'VOB/B'},
  {k:'vob_c',label:'VOB/C · Techn. Bedingungen',short:'VOB/C'},
  {k:'bgb',label:'BGB · Werkvertrag',short:'BGB'},
  {k:'hoai',label:'HOAI · Termine',short:'HOAI'},
  {k:'bauplanung',label:'Bauplanungsrecht · B-Plan',short:'Bauplanung'},
  {k:'bauordnung',label:'Bauordnungsrecht · LBO',short:'Bauordnung'},
  {k:'arbeitsschutz',label:'Arbeitsschutz & Sicherheit',short:'Arbeitsschutz'}
];
function catShort(k){const c=CATS.find(x=>x.k===k);return c?c.short:k;}
function catPill(card){return '<span class="cat-pill">'+esc(catShort(card.cat))+'</span>';}
function buildCatGrid(){
  const counts={};CARDS.forEach(c=>counts[c.cat]=(counts[c.cat]||0)+1);
  let h='<button class="cat-btn on" data-cat="all" onclick="selectCat(this)" style="grid-column:1/-1">Alle Kategorien <span class="cat-cnt">'+CARDS.length+'</span></button>';
  CATS.forEach(c=>{const n=counts[c.k]||0;if(!n)return;h+='<button class="cat-btn" data-cat="'+c.k+'" onclick="selectCat(this)">'+esc(c.short)+' <span class="cat-cnt">'+n+'</span></button>';});
  document.getElementById('cat-grid').innerHTML=h;
}
function selectCat(b){document.querySelectorAll('[data-cat]').forEach(x=>x.classList.remove('on'));b.classList.add('on');category=b.dataset.cat;}

function poolForMode(){
  let p=CARDS;
  if(category!=='all')p=p.filter(c=>c.cat===category);
  if(mode==='ankreuzen')return p.filter(c=>c.type==='mc'||c.type==='yn');
  if(mode==='abfragen')return p.filter(c=>c.type==='open');
  return p;
}

function startQuiz(testMode){
  isTestMode=!!testMode;
  const pool=poolForMode();
  cards=order==='shuffle'?shuffle(pool):pool.slice();
  idx=0;correct=0;wrong=0;
  if(cards.length===0){alert('Keine Karten in dieser Auswahl.');return;}
  showScreen('quiz');renderCard();
}

function goHome(){clearTimer();saveStats();updateHomeStats();showScreen('start');}
function showScreen(id){document.querySelectorAll('.screen').forEach(s=>s.classList.remove('active'));$(id).classList.add('active');}

/* ---- stats ---- */
function saveStats(){
  if(correct+wrong>0){
    const pct=Math.round(correct/(correct+wrong)*100);
    Store.set('lastScore',pct+'%');
    const best=parseInt(Store.get('bestScore')||'0',10);
    if(pct>best)Store.set('bestScore',pct);
  }
}
function updateHomeStats(){
  $('s-total').textContent=CARDS.length;
  $('s-last').textContent=Store.get('lastScore')||'\u2014';
  const b=Store.get('bestScore');
  $('s-best').textContent=b?b+'%':'\u2014';
}

/* ---- timer ---- */
function startTimer(){
  clearTimer();timerLeft=TIMER_SECS;
  $('timer-wrap').style.display='block';updateTimerUI();
  timerInt=setInterval(()=>{
    timerLeft-=0.1;
    if(timerLeft<=0){timerLeft=0;updateTimerUI();clearTimer();timeUp();}
    else updateTimerUI();
  },100);
}
function clearTimer(){clearInterval(timerInt);timerInt=null;$('timer-wrap').style.display='none';}
function updateTimerUI(){
  const pct=(timerLeft/TIMER_SECS)*100;
  const f=$('timer-fill');f.style.width=pct+'%';
  f.className='timer-fill'+(pct<33?' danger':pct<60?' warn':'');
  $('timer-lbl').textContent=Math.ceil(timerLeft)+'s';
}
function timeUp(){
  if(answered)return;
  const card=cards[idx];
  if(card.type==='mc'){gradeMC(true);}
  else if(card.type==='yn'){revealYN(null);}
  else{revealOpen(true);}
}

/* ---- render ---- */
function setActions(html){$('actions').innerHTML=html;}
function clearFb(){const fb=$('fb');fb.className='fb';fb.innerHTML='';}
function showFb(ok,msg){const fb=$('fb');fb.className='fb show '+(ok?'ok':'bad');fb.innerHTML=msg;}
function updateScoreHdr(){$('h-ok').textContent=correct;$('h-bad').textContent=wrong;}

function renderCard(){
  answered=false;sel=new Set();
  const card=cards[idx];
  $('q-cnt').textContent=(idx+1)+' / '+cards.length;
  $('prog').style.width=(idx/cards.length*100)+'%';
  updateScoreHdr();
  $('q-badge').innerHTML=isTestMode?'<span class="test-badge">&#9201; Test</span>':'';
  clearFb();
  const ca=$('card-area');
  ca.style.animation='none';void ca.offsetHeight;ca.style.animation='';
  if(card.type==='mc')renderMC(card,ca);
  else if(card.type==='yn')renderYN(card,ca);
  else renderOpen(card,ca);
  ca.scrollTop=0;
  if(isTestMode)startTimer();
}

function renderMC(card,ca){
  const L='ABCDEFGHIJ';
  const multi=card.correct.length>1;
  let h='<div class="badge-row">'+catPill(card)+'<span class="type-badge tb-mc">&#10022; Multiple Choice</span></div>';
  h+='<div class="q-card"><div class="q-text">'+nl2br(card.q)+'</div>';
  h+=multi?'<div class="multi-hint">&#10022; '+card.correct.length+' richtige Antworten w&auml;hlen</div>':'';
  h+='</div><div class="opts" id="opts">';
  card.options.forEach((o,i)=>{
    h+='<button class="opt" id="o'+i+'" onclick="toggleOpt('+i+')"><span class="opt-ltr">'+L[i]+'</span><span>'+nl2br(o)+'</span></button>';
  });
  h+='</div>';
  ca.innerHTML=h;
  setActions('<button class="btn-act btn-blue" id="btn-check" onclick="gradeMC(false)" disabled>Pr&uuml;fen</button>');
}

let _lastTap=0;
function toggleOpt(i){
  if(answered)return;
  const now=Date.now();if(now-_lastTap<150)return;_lastTap=now;
  const card=cards[idx];const multi=card.correct.length>1;const btn=$('o'+i);
  if(multi){
    if(sel.has(i)){sel.delete(i);btn.classList.remove('sel');}
    else{sel.add(i);btn.classList.add('sel');}
  }else{
    sel.forEach(j=>{const b=$('o'+j);if(b)b.classList.remove('sel');});
    sel.clear();sel.add(i);btn.classList.add('sel');
  }
  $('btn-check').disabled=sel.size===0;
}

function gradeMC(timedOut){
  if(answered)return;answered=true;clearTimer();
  const card=cards[idx];const cSet=new Set(card.correct);
  let ok=sel.size===cSet.size;sel.forEach(i=>{if(!cSet.has(i))ok=false;});
  if(timedOut)ok=false;
  card.options.forEach((_,i)=>{
    const btn=$('o'+i);if(!btn)return;
    btn.disabled=true;btn.classList.remove('sel');
    const isSel=sel.has(i),isRight=cSet.has(i);
    if(isSel&&isRight)btn.classList.add('ok');
    else if(isSel&&!isRight)btn.classList.add('bad');
    else if(!isSel&&isRight)btn.classList.add('missed');
  });
  if(ok)correct++;else wrong++;updateScoreHdr();
  showFb(ok,ok?'&#10003; Richtig!':(timedOut?'&#9201; Zeit abgelaufen':'&#10007; Leider falsch &mdash; richtige L&ouml;sung markiert'));
  showNext();
}

function renderYN(card,ca){
  let h='<div class="badge-row">'+catPill(card)+'<span class="type-badge tb-yn">&#9673; Ja / Nein</span></div>';
  h+='<div class="q-card"><div class="q-text">'+nl2br(card.q)+'</div></div>';
  h+='<div class="yn-row">';
  h+='<button class="yn-btn" id="yn-ja" onclick="revealYN(\'JA\')"><span class="ico">&#10003;</span><span>JA</span></button>';
  h+='<button class="yn-btn" id="yn-nein" onclick="revealYN(\'NEIN\')"><span class="ico">&#10007;</span><span>NEIN</span></button>';
  h+='</div>';
  ca.innerHTML=h;
  setActions('');
}

function revealYN(choice){
  if(answered)return;answered=true;clearTimer();
  const card=cards[idx];
  const ja=$('yn-ja'),ne=$('yn-nein');ja.disabled=true;ne.disabled=true;
  const right=card.yn;
  (right==='JA'?ja:ne).classList.add(right==='JA'?'ok-ja':'ok-nein');
  if(choice&&choice!==right){(choice==='JA'?ja:ne).classList.add('wrong');}
  const ok=choice===right;
  if(choice===null){wrong++;}else if(ok){correct++;}else{wrong++;}
  updateScoreHdr();
  // explanation if answer has more than the bare JA/NEIN
  const bare=card.a.replace(/[^A-Za-zÄÖÜ]/g,'').toUpperCase();
  if(bare!=='JA'&&bare!=='NEIN'){
    const ca=$('card-area');
    const d=document.createElement('div');d.className='answer-box';
    d.innerHTML='<div class="answer-lbl">Erl&auml;uterung</div><div class="answer-txt">'+nl2br(card.a)+'</div>';
    ca.appendChild(d);
  }
  showFb(ok,choice===null?('&#9201; Zeit abgelaufen &mdash; Antwort: '+right):(ok?'&#10003; Richtig!':'&#10007; Falsch &mdash; Antwort: '+right));
  showNext();
}

function renderOpen(card,ca){
  let h='<div class="badge-row">'+catPill(card)+'<span class="type-badge tb-open">&#9998; Frage / Merksatz</span></div>';
  h+='<div class="q-card"><div class="q-text">'+nl2br(card.q)+'</div></div>';
  ca.innerHTML=h;
  setActions('<button class="btn-act btn-blue" id="btn-reveal" onclick="revealOpen(false)">Antwort zeigen</button>');
}

function revealOpen(timedOut){
  if(answered)return;
  clearTimer();
  const card=cards[idx];
  if(!$('open-answer')){
    const ca=$('card-area');
    const d=document.createElement('div');d.className='answer-box';d.id='open-answer';
    d.innerHTML='<div class="answer-lbl">Antwort</div><div class="answer-txt">'+nl2br(card.a)+'</div>';
    ca.appendChild(d);ca.scrollTop=ca.scrollHeight;
  }
  if(timedOut){
    answered=true;wrong++;updateScoreHdr();
    showFb(false,'&#9201; Zeit abgelaufen');
    showNext();
  }else{
    // self-assessment
    setActions('<button class="btn-act btn-redo" onclick="rateOpen(false)">&#10007; Nicht gewusst</button>'+
               '<button class="btn-act btn-green" onclick="rateOpen(true)">&#10003; Gewusst</button>');
  }
}

function rateOpen(knew){
  if(answered)return;answered=true;
  if(knew)correct++;else wrong++;updateScoreHdr();
  showFb(knew,knew?'&#10003; Stark!':'&#10007; Markiert zum Wiederholen');
  showNext();
}

function showNext(){
  const last=idx>=cards.length-1;
  setActions('<button class="btn-act btn-grey" onclick="nextCard()">'+(last?'Ergebnis ansehen':'Weiter &rarr;')+'</button>');
}

function nextCard(){clearTimer();idx++;if(idx>=cards.length)showResults();else renderCard();}

function showResults(){
  clearTimer();
  const tot=correct+wrong;const pct=tot>0?Math.round(correct/tot*100):0;
  saveStats();updateHomeStats();
  let emoji='\uD83D\uDE13',title='Weiter \u00FCben!',sub='Mehr Wiederholungen helfen.';
  if(pct>=90){emoji='\uD83C\uDFC6';title='Ausgezeichnet!';sub='Klasse Ergebnis!';}
  else if(pct>=70){emoji='\uD83C\uDFAF';title='Gut gemacht!';sub='Noch ein bisschen \u00FCben.';}
  else if(pct>=50){emoji='\uD83D\uDCAA';title='Solide!';sub='Du kommst gut voran.';}
  $('r-emoji').textContent=emoji;$('r-title').textContent=title;
  $('r-sub').textContent=sub+(isTestMode?' \u00B7 Testmodus':'');
  $('r-pct').textContent=pct+'%';$('r-ok').textContent=correct;$('r-bad').textContent=wrong;
  const C=2*Math.PI*52;const arc=$('sc-arc');
  const color=pct>=70?'#22c55e':pct>=50?'#f59e0b':'#ef4444';
  arc.style.stroke=color;arc.style.strokeDashoffset=C;$('r-pct').style.color=color;
  showScreen('results');
  setTimeout(()=>{arc.style.strokeDashoffset=C-(pct/100)*C;},80);
}

try{updateHomeStats();buildCatGrid();}catch(e){console.error(e);}
</script>
</body>
</html>
