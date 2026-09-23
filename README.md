[script.js](https://github.com/user-attachments/files/32571742/script.js)
let cart=JSON.parse(localStorage.getItem('novex-cart')||'[]');
function renderCart(){const box=document.getElementById('cartItems'),count=document.getElementById('cartCount'),total=document.getElementById('total');count.textContent=cart.length;if(!cart.length){box.innerHTML='<p class="muted">Ton panier est vide.</p>';total.textContent='0,00 €';return}let sum=0;box.innerHTML=cart.map((p,i)=>{sum+=p.price;return `<div class="cart-row"><span>${p.name}</span><strong>${p.price.toFixed(2).replace('.',',')} € <button class="remove" onclick="removeItem(${i})">×</button></strong></div>`}).join('');total.textContent=sum.toFixed(2).replace('.',',')+' €';}
function addToCart(name,price){cart.push({name,price});localStorage.setItem('novex-cart',JSON.stringify(cart));renderCart();toggleCart(true)}
function removeItem(i){cart.splice(i,1);localStorage.setItem('novex-cart',JSON.stringify(cart));renderCart()}
function toggleCart(force){const c=document.getElementById('cart'),o=document.getElementById('overlay');let open=force===true?true:!c.classList.contains('open');c.classList.toggle('open',open);o.classList.toggle('show',open)}
function checkout(){alert('Démo : connecte Stripe ou PayPal ici pour accepter les paiements.')}
function subscribe(e){e.preventDefault();document.getElementById('msg').textContent='Merci ! Tu seras prévenu du prochain drop.';e.target.reset()}
renderCart();
[style.css](https://github.com/user-attachments/files/32571749/style.css)
@import url('https://fonts.googleapis.com/css2?family=Archivo+Black&family=Inter:wght@400;500;700;800&display=swap');
:root{--bg:#080808;--card:#111;--line:#292929;--white:#f4f4f0;--muted:#999;--acid:#d8ff28}
*{box-sizing:border-box}html{scroll-behavior:smooth}body{margin:0;background:var(--bg);color:var(--white);font-family:Inter,Arial,sans-serif}a{color:inherit;text-decoration:none}
.nav{height:78px;border-bottom:1px solid var(--line);display:flex;align-items:center;justify-content:space-between;padding:0 5vw;position:sticky;top:0;background:#080808eF;backdrop-filter:blur(12px);z-index:20}.logo{font:28px 'Archivo Black',sans-serif;letter-spacing:-2px}.logo span{font:10px Inter;vertical-align:top;margin-left:3px}.nav nav{display:flex;gap:30px;font-size:11px;font-weight:800;letter-spacing:1.5px}.cart-btn{background:transparent;color:white;border:1px solid var(--line);padding:11px 15px;font-weight:800;cursor:pointer}.cart-btn b{background:var(--acid);color:#000;padding:2px 6px;margin-left:7px}
.hero{min-height:calc(100vh - 78px);display:grid;grid-template-columns:1fr 1fr;align-items:center;padding:6vw 7vw;gap:6vw;border-bottom:1px solid var(--line)}.eyebrow{font-size:11px;font-weight:800;letter-spacing:2px;color:var(--acid);margin:0 0 18px}.hero h1,h2{font:clamp(54px,8vw,115px)/.88 'Archivo Black',sans-serif;letter-spacing:-5px;margin:0}.hero h1 em,h2 em{font-style:normal;-webkit-text-stroke:1px var(--white);color:transparent}.lead{max-width:480px;color:#bbb;line-height:1.7;margin:28px 0}.btn{display:inline-flex;gap:30px;align-items:center;background:var(--acid);color:#000;font-weight:800;padding:17px 20px;font-size:12px}.hero-image{position:relative}.hero-image img{width:100%;display:block;max-height:670px;object-fit:cover;filter:saturate(.9)}.stamp{position:absolute;right:-20px;bottom:25px;background:var(--acid);color:#000;padding:15px;font:18px 'Archivo Black';transform:rotate(-5deg)}
.ticker{overflow:hidden;border-bottom:1px solid var(--line);padding:14px 0;white-space:nowrap;color:#777;font-size:11px;font-weight:800;letter-spacing:2px}.ticker div{animation:scroll 25s linear infinite}@keyframes scroll{to{transform:translateX(-40%)}}
.section{padding:110px 7vw}.section-head{display:flex;justify-content:space-between;align-items:end;margin-bottom:55px}.section-head h2{font-size:clamp(45px,6vw,80px)}.muted{color:#8d8d8d;line-height:1.7;max-width:430px}.products{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}.product{border:1px solid var(--line);background:#0d0d0d;padding:10px}.product-img{height:480px;position:relative;display:flex;align-items:center;justify-content:center;overflow:hidden}.product-img:after{content:"";width:45%;height:82%;border:3px solid white;box-shadow:0 0 30px rgba(255,255,255,.4);border-radius:35% 35% 15% 15%;opacity:.7}.product-img span{position:absolute;z-index:1;font:28px 'Archivo Black';letter-spacing:-2px}.product-img small{position:absolute;top:15px;left:15px;font-weight:800}.blue{background:linear-gradient(145deg,#071327,#142e63)}.grey{background:linear-gradient(145deg,#222,#9a9a9a)}.pink{background:linear-gradient(145deg,#351b27,#ef93b0)}.product-info{display:flex;justify-content:space-between;gap:10px;padding:20px 8px}.product h3{font-size:12px;margin:0 0 5px}.product p{font-size:11px;color:#777;margin:0}.product strong{font-size:13px;white-space:nowrap}.product>button{width:100%;padding:14px;background:transparent;border:1px solid var(--line);color:white;font-weight:800;cursor:pointer}.product>button:hover{background:var(--acid);color:#000}
.manifesto{padding:120px 12vw;display:grid;grid-template-columns:150px 1fr;gap:60px;border-top:1px solid var(--line);border-bottom:1px solid var(--line);background:#101010}.manifesto-number{font:70px 'Archivo Black';color:var(--acid)}.manifesto h2,.community h2,.newsletter h2{font-size:clamp(48px,7vw,90px)}.manifesto p:not(.eyebrow){max-width:600px;color:#aaa;line-height:1.8;margin:30px 0}.text-link{font-size:11px;font-weight:800;border-bottom:1px solid var(--acid);padding-bottom:5px}
.community{text-align:center;padding:130px 7vw}.community .quote{margin:55px auto 0;border:1px solid var(--line);padding:35px;max-width:700px;font-size:22px;font-weight:700}
.newsletter{padding:100px 7vw;background:#d8ff28;color:#000}.newsletter .eyebrow{color:#000}.newsletter h2 em{-webkit-text-stroke:1px #000}.newsletter form{display:flex;max-width:700px;margin-top:45px}.newsletter input{flex:1;padding:18px;border:0;background:#fff;font-size:15px}.newsletter button{padding:18px 25px;border:0;background:#000;color:#fff;font-weight:800}.newsletter .muted{color:#222}
footer{padding:40px 7vw;display:flex;justify-content:space-between;align-items:center;border-top:1px solid var(--line);font-size:10px;color:#777;letter-spacing:1px}
.cart{position:fixed;right:-430px;top:0;width:min(430px,100%);height:100vh;background:#0d0d0d;border-left:1px solid var(--line);z-index:40;padding:28px;transition:.3s;display:flex;flex-direction:column}.cart.open{right:0}.cart-head{display:flex;justify-content:space-between}.cart-head button{background:none;border:0;color:white;font-size:30px;cursor:pointer}.cart-items{flex:1;padding-top:30px}.cart-row{display:flex;justify-content:space-between;border-bottom:1px solid var(--line);padding:15px 0}.remove{color:#888;background:none;border:0;cursor:pointer}.cart-total{display:flex;justify-content:space-between;border-top:1px solid var(--line);padding:20px 0}.checkout{background:var(--acid);border:0;padding:17px;font-weight:800;cursor:pointer}.overlay{display:none;position:fixed;inset:0;background:#0009;z-index:30}.overlay.show{display:block}
@media(max-width:800px){.nav nav{display:none}.hero{grid-template-columns:1fr;padding:50px 6vw}.hero-image{order:-1}.hero h1{font-size:65px}.section,.community,.newsletter{padding:80px 6vw}.section-head{display:block}.products{grid-template-columns:1fr}.product-img{height:420px}.manifesto{grid-template-columns:1fr;padding:80px 6vw;gap:20px}footer{display:block}.newsletter form{display:block}.newsletter input,.newsletter button{width:100%}}
[index.html](https://github.com/user-attachments/files/32571753/index.html)
<!doctype html>
<html lang="fr"><img width="306" height="399" alt="product1" src="https://github.com/user-attachments/assets/83413897-af8b-4ba0-80c8-8877cf2a4ee7" />
<img width="745" height="765" alt="hero" src="https://github.com/user-attachments/assets/4819b262-8edc-46c1-9ff5-fb922610db76" />
<img width="254" height="601" alt="product-detail" src="https://github.com/user-attachments/assets/27c803f8-888b-4ebe-97dd-5398e0d8a7b2" />
<img width="324" height="399" alt="product4" src="https://github.com/user-attachments/assets/ede2448d-a4b1-47c4-aa81-834ed47d5f4d" />
<img width="306" height="399" alt="product2" src="https://github.com/user-attachments/assets/44272130-0c70-473e-868a-91b850326e2b" />
<img width="778" height="586" alt="universe" src="https://github.com/user-attachments/assets/26b9fed4-fb80-4d95-9d0b-4c78403f2907" />
<img width="322" height="399" alt="product3" src="https://github.com/user-attachments/assets/062e78d5-95d5-4eea-a78d-7da1f9bfd4b0" />

<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>NØVEX — Streetwear Underground</title>
<meta name="description" content="NØVEX — marque de streetwear underground, drops exclusifs et pièces réfléchissantes.">
<link rel="stylesheet" href="style.css">
</head>
<body>
<header class="nav">
  <a class="logo" href="#home">NØVEX<span>®</span></a>
  <nav>
    <a href="#drop">DROP</a>
    <a href="#collection">COLLECTION</a>
    <a href="#story">UNIVERS</a>
    <a href="#contact">CONTACT</a>
  </nav>
  <button class="cart-btn" onclick="toggleCart()">PANIER <b id="cartCount">0</b></button>
</header>

<main>
<section id="home" class="hero">
  <div class="hero-copy">
    <p class="eyebrow">NØVEX / VOL.02</p>
    <h1>STREET<br><em>IMPACT.</em></h1>
    <p class="lead">Des silhouettes urbaines. Des détails réfléchissants. Des drops pensés pour sortir du lot.</p>
    <a class="btn" href="#collection">DÉCOUVRIR LE DROP <span>↗</span></a>
  </div>
  <div class="hero-image">
    <img src="assets/novex-look.png" alt="Collection NØVEX streetwear">
    <div class="stamp">DROP<br>02</div>
  </div>
</section>

<section id="drop" class="ticker"><div>DROP 02 — NOVEX STREETWEAR — LIMITED RELEASE — DROP 02 — NOVEX STREETWEAR — LIMITED RELEASE —</div></section>

<section id="collection" class="section">
  <div class="section-head">
    <div><p class="eyebrow">01 / LA COLLECTION</p><h2>PIÈCES<br><em>FORTES.</em></h2></div>
    <p class="muted">Une sélection monochrome avec accents colorés et lignes réfléchissantes.</p>
  </div>
  <div class="products">
    <article class="product">
      <div class="product-img blue"><span>NØVEX</span><small>01</small></div>
      <div class="product-info"><div><h3>SHADOW BLUE SET</h3><p>Ensemble survêtement</p></div><strong>89,90 €</strong></div>
      <button onclick="addToCart('Shadow Blue Set',89.90)">AJOUTER</button>
    </article>
    <article class="product">
      <div class="product-img grey"><span>NØVEX</span><small>02</small></div>
      <div class="product-info"><div><h3>PHANTOM GREY SET</h3><p>Ensemble réfléchissant</p></div><strong>89,90 €</strong></div>
      <button onclick="addToCart('Phantom Grey Set',89.90)">AJOUTER</button>
    </article>
    <article class="product">
      <div class="product-img pink"><span>NØVEX</span><small>03</small></div>
      <div class="product-info"><div><h3>NEON PINK SET</h3><p>Ensemble oversize</p></div><strong>89,90 €</strong></div>
      <button onclick="addToCart('Neon Pink Set',89.90)">AJOUTER</button>
    </article>
  </div>
</section>

<section id="story" class="manifesto">
  <div class="manifesto-number">02</div>
  <div><p class="eyebrow">L'UNIVERS NØVEX</p><h2>MADE FOR<br>THE <em>UNKNOWN.</em></h2>
  <p>NØVEX mélange culture urbaine, minimalisme sombre et détails haute visibilité. Chaque drop est conçu comme une pièce d'identité.</p>
  <a class="text-link" href="#contact">NOTRE HISTOIRE ↗</a></div>
</section>

<section class="community">
  <p class="eyebrow">03 / LA COMMUNAUTÉ</p>
  <h2>PORTÉ PAR<br><em>VOUS.</em></h2>
  <div class="quote">« Pas besoin de parler fort quand ton style le fait pour toi. »</div>
</section>

<section id="contact" class="newsletter">
  <p class="eyebrow">04 / STAY IN THE LOOP</p>
  <h2>SOIS LÀ POUR<br>LE PROCHAIN <em>DROP.</em></h2>
  <form onsubmit="subscribe(event)">
    <input id="email" type="email" placeholder="ton@email.com" required>
    <button>REJOINDRE ↗</button>
  </form>
  <p id="msg" class="muted"></p>
</section>
</main>

<aside id="cart" class="cart">
  <div class="cart-head"><h2>TON PANIER</h2><button onclick="toggleCart()">×</button></div>
  <div id="cartItems" class="cart-items"><p class="muted">Ton panier est vide.</p></div>
  <div class="cart-total"><span>TOTAL</span><strong id="total">0,00 €</strong></div>
  <button class="checkout" onclick="checkout()">PASSER LA COMMANDE</button>
</aside>
<div id="overlay" class="overlay" onclick="toggleCart()"></div>

<footer><div class="logo">NØVEX<span>®</span></div><p>STREETWEAR UNDERGROUND / VOL.02</p><p>© 2026 NØVEX. Tous droits réservés.</p></footer>
<script src="script.js"></script>
</body>
</html>
