<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>9BCLOTHES — Archive Store</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Space+Grotesk:wght@400;500;700&family=Space+Mono:wght@400;700&display=swap" rel="stylesheet">
<style>
  :root{
    --ink:#0b0b0c;
    --paper:#f5f1e8;
    --red:#c8102e;
    --gold:#c9a227;
    --grey:#8b8d8f;
    --blue:#1e5aa8;
    --line: rgba(245,241,232,0.14);
    --line-strong: rgba(245,241,232,0.28);
    --card:#131315;
  }
  *{box-sizing:border-box;}
  html{scroll-behavior:smooth;}
  body{
    margin:0;
    background:var(--ink);
    color:var(--paper);
    font-family:'Space Grotesk',sans-serif;
    -webkit-font-smoothing:antialiased;
  }
  .mono{font-family:'Space Mono',monospace;}
  h1,h2,.display{
    font-family:'Anton',sans-serif;
    font-weight:400;
    letter-spacing:0.01em;
    text-transform:uppercase;
    margin:0;
  }
  a{color:inherit;}
  img,svg{display:block;}

  /* ===== Header ===== */
  header{
    position:sticky; top:0; z-index:50;
    display:flex; align-items:center; justify-content:space-between;
    padding:18px 32px;
    background:rgba(11,11,12,0.9);
    backdrop-filter:blur(10px);
    border-bottom:1px solid var(--line);
  }
  .logo{
    display:flex; align-items:center; gap:10px;
  }
  .logo .mark{
    width:38px;height:38px;
    background:var(--paper); color:var(--ink);
    display:flex;align-items:center;justify-content:center;
    font-family:'Anton',sans-serif; font-size:19px;
    transform:rotate(-4deg);
  }
  .logo .word{
    font-family:'Anton',sans-serif; font-size:20px; letter-spacing:0.06em;
  }
  .logo .word span{color:var(--red);}

  nav.tabs{
    display:flex; gap:4px;
    background:var(--card);
    border:1px solid var(--line);
    padding:4px;
    border-radius:999px;
  }
  nav.tabs button{
    font-family:'Space Mono',monospace;
    font-size:11px; letter-spacing:0.08em; text-transform:uppercase;
    background:transparent; border:none; color:var(--grey);
    padding:9px 16px; border-radius:999px; cursor:pointer;
    transition:all .2s ease;
  }
  nav.tabs button.active{
    background:var(--paper); color:var(--ink); font-weight:700;
  }
  nav.tabs button:hover:not(.active){color:var(--paper);}

  .cart-btn{
    display:flex; align-items:center; gap:8px;
    background:var(--red); color:var(--paper);
    border:none; padding:11px 18px; border-radius:999px;
    font-family:'Space Mono',monospace; font-size:12px; letter-spacing:.05em;
    cursor:pointer; text-transform:uppercase;
  }
  .cart-btn:hover{background:#a80d24;}

  /* ===== Hero ===== */
  .hero{
    position:relative;
    padding:90px 32px 70px;
    border-bottom:1px solid var(--line);
    overflow:hidden;
  }
  .hero-inner{max-width:1200px;margin:0 auto;}
  .eyebrow{
    font-family:'Space Mono',monospace; font-size:12px; letter-spacing:.18em;
    color:var(--gold); text-transform:uppercase; margin-bottom:18px;
    display:flex; align-items:center; gap:10px;
  }
  .eyebrow::before{content:"";width:22px;height:1px;background:var(--gold);}
  .hero h1{
    font-size:clamp(48px,9vw,118px);
    line-height:0.92;
    max-width:900px;
  }
  .hero h1 em{font-style:normal;color:var(--red);}
  .hero p.sub{
    max-width:520px; margin-top:24px; color:var(--grey);
    font-size:16px; line-height:1.6;
  }
  .hero-cta{
    margin-top:34px; display:flex; gap:14px; flex-wrap:wrap;
  }
  .btn-primary{
    background:var(--paper); color:var(--ink); border:none;
    padding:16px 30px; font-family:'Space Mono',monospace; font-size:13px;
    letter-spacing:.06em; text-transform:uppercase; cursor:pointer; border-radius:2px;
  }
  .btn-ghost{
    background:transparent; color:var(--paper); border:1px solid var(--line-strong);
    padding:16px 30px; font-family:'Space Mono',monospace; font-size:13px;
    letter-spacing:.06em; text-transform:uppercase; cursor:pointer; border-radius:2px;
  }
  .btn-primary:hover{background:var(--gold);}
  .btn-ghost:hover{border-color:var(--paper);}

  /* barcode label strip */
  .label-strip{
    margin-top:56px; border:1px solid var(--line-strong);
    display:flex; align-items:stretch; max-width:640px;
  }
  .label-strip .barcode{
    flex:0 0 150px; padding:14px;
    background-image:repeating-linear-gradient(90deg,var(--paper) 0 2px, transparent 2px 4px, var(--paper) 4px 5px, transparent 5px 9px, var(--paper) 9px 12px, transparent 12px 14px);
    background-color:transparent;
  }
  .label-strip .meta{
    flex:1; padding:14px 18px; border-left:1px solid var(--line-strong);
    font-family:'Space Mono',monospace; font-size:11px; color:var(--grey);
    display:flex; flex-direction:column; justify-content:center; gap:4px;
    letter-spacing:.03em;
  }
  .label-strip .meta b{color:var(--paper);}

  /* ===== Catalog ===== */
  .catalog{max-width:1280px; margin:0 auto; padding:70px 32px 40px;}
  .catalog-head{
    display:flex; align-items:baseline; justify-content:space-between;
    border-bottom:1px solid var(--line); padding-bottom:18px; margin-bottom:36px;
    flex-wrap:wrap; gap:12px;
  }
  .catalog-head h2{font-size:clamp(30px,4vw,46px);}
  .catalog-head .count{
    font-family:'Space Mono',monospace; font-size:12px; color:var(--grey);
  }

  .grid{
    display:grid;
    grid-template-columns:repeat(auto-fill,minmax(260px,1fr));
    gap:22px;
  }
  .card{
    background:var(--card);
    border:1px solid var(--line);
    display:flex; flex-direction:column;
    transition:border-color .2s ease, transform .2s ease;
    position:relative;
  }
  .card:hover{border-color:var(--line-strong); transform:translateY(-3px);}
  .card .tag{
    position:absolute; top:12px; left:12px;
    background:var(--ink); border:1px solid var(--line-strong);
    font-family:'Space Mono',monospace; font-size:10px; letter-spacing:.06em;
    padding:4px 8px; color:var(--grey); text-transform:uppercase; z-index:2;
  }
  .card .icon-wrap{
    padding:26px 20px 10px; aspect-ratio:5/3;
    display:flex; align-items:center; justify-content:center;
    background:
      radial-gradient(circle at 30% 20%, rgba(255,255,255,0.05), transparent 60%);
  }
  .card .icon-wrap svg{width:100%; height:100%;}
  .card .info{padding:16px 18px 20px; border-top:1px solid var(--line); display:flex; flex-direction:column; gap:10px;}
  .card .name{font-family:'Space Grotesk',sans-serif; font-weight:700; font-size:15.5px; line-height:1.3;}
  .card .sku{font-family:'Space Mono',monospace; font-size:10.5px; color:var(--grey); letter-spacing:.04em;}
  .card .swatches{display:flex; gap:6px;}
  .card .swatch{width:14px;height:14px;border-radius:50%;border:1px solid var(--line-strong);}
  .card .bottom-row{
    display:flex; align-items:center; justify-content:space-between; margin-top:4px;
  }
  .card .price{font-family:'Space Mono',monospace; font-size:16px; font-weight:700; color:var(--paper);}
  .card .add{
    background:transparent; border:1px solid var(--line-strong); color:var(--paper);
    font-family:'Space Mono',monospace; font-size:11px; letter-spacing:.05em;
    padding:9px 14px; cursor:pointer; text-transform:uppercase; border-radius:2px;
  }
  .card .add:hover{background:var(--paper); color:var(--ink); border-color:var(--paper);}
  .card .add.added{background:var(--red); border-color:var(--red); color:var(--paper);}

  /* ===== Footer ===== */
  footer{
    border-top:1px solid var(--line);
    padding:60px 32px 40px;
    margin-top:50px;
  }
  .footer-inner{
    max-width:1280px; margin:0 auto;
    display:flex; justify-content:space-between; flex-wrap:wrap; gap:30px;
  }
  footer .col{max-width:340px;}
  footer .word{font-family:'Anton',sans-serif;font-size:22px;letter-spacing:.05em;margin-bottom:12px;}
  footer p{color:var(--grey); font-size:13.5px; line-height:1.6;}
  footer .cols-right{display:flex; gap:60px; flex-wrap:wrap;}
  footer .col h4{
    font-family:'Space Mono',monospace; font-size:11px; letter-spacing:.08em;
    text-transform:uppercase; color:var(--gold); margin-bottom:14px;
  }
  footer ul{list-style:none;padding:0;margin:0;display:flex;flex-direction:column;gap:9px;}
  footer li{font-size:13.5px; color:var(--grey);}
  .fine-print{
    max-width:1280px; margin:50px auto 0; padding-top:20px;
    border-top:1px solid var(--line);
    font-family:'Space Mono',monospace; font-size:10.5px; color:#555;
    display:flex; justify-content:space-between; flex-wrap:wrap; gap:8px;
  }

  /* ===== Cart Drawer ===== */
  .overlay{
    position:fixed; inset:0; background:rgba(0,0,0,.55);
    opacity:0; pointer-events:none; transition:opacity .25s ease; z-index:60;
  }
  .overlay.open{opacity:1; pointer-events:auto;}
  .drawer{
    position:fixed; top:0; right:0; height:100%; width:min(400px,92vw);
    background:var(--ink); border-left:1px solid var(--line-strong);
    transform:translateX(100%); transition:transform .3s ease;
    z-index:61; display:flex; flex-direction:column;
  }
  .drawer.open{transform:translateX(0);}
  .drawer-head{
    padding:22px 22px 18px; border-bottom:1px solid var(--line);
    display:flex; align-items:center; justify-content:space-between;
  }
  .drawer-head h2{font-size:24px;}
  .drawer-head button{
    background:none;border:none;color:var(--paper);font-size:22px;cursor:pointer;
    line-height:1;
  }
  .drawer-items{flex:1; overflow-y:auto; padding:10px 22px;}
  .drawer-item{
    display:flex; gap:12px; padding:16px 0; border-bottom:1px solid var(--line);
  }
  .drawer-item .icon-mini{width:64px;height:44px;flex:0 0 auto;}
  .drawer-item .icon-mini svg{width:100%;height:100%;}
  .drawer-item .di-info{flex:1; display:flex; flex-direction:column; gap:6px;}
  .drawer-item .di-name{font-size:13.5px; font-weight:700;}
  .drawer-item .di-row{display:flex; justify-content:space-between; align-items:center;}
  .drawer-item .di-price{font-family:'Space Mono',monospace; font-size:13px;}
  .drawer-item .remove{
    background:none;border:none;color:var(--grey); font-family:'Space Mono',monospace;
    font-size:10.5px; text-decoration:underline; cursor:pointer; padding:0;
  }
  .drawer-item .remove:hover{color:var(--red);}
  .drawer-empty{color:var(--grey); font-size:13.5px; padding:30px 0; text-align:center;}
  .drawer-foot{padding:20px 22px 26px; border-top:1px solid var(--line);}
  .drawer-total{display:flex; justify-content:space-between; font-family:'Space Mono',monospace; font-size:15px; margin-bottom:16px;}
  .drawer-foot .btn-primary{width:100%;}

  @media (max-width:860px){
    nav.tabs{display:none;}
    header{padding:14px 18px;}
    .hero{padding:60px 18px 50px;}
    .catalog{padding:50px 18px 30px;}
    footer{padding:44px 18px 30px;}
  }
</style>
</head>
<body>

<header>
  <div class="logo">
    <div class="mark">9B</div>
    <div class="word">9B<span>CLOTHES</span></div>
  </div>
  <nav class="tabs" id="tabs">
    <button class="active" data-cat="all">All</button>
    <button data-cat="jordan">Jordan</button>
    <button data-cat="yeezy">Yeezy</button>
    <button data-cat="asics">Asics</button>
    <button data-cat="bags">Bags</button>
  </nav>
  <button class="cart-btn" onclick="openCart()">
    <span>Cart</span>
    <span class="mono" id="cartCount">0</span>
  </button>
</header>

<section class="hero">
  <div class="hero-inner">
    <div class="eyebrow">Rotation 09 — Sneaker &amp; Leather Archive</div>
    <h1>Cop the <em>heat.</em><br>Skip the line.</h1>
    <p class="sub">9BCLOTHES stocks the colorways that actually matter — Jordan retros, Yeezy, Asics runners and Goyardine leather, curated box by box. Every pair, one price.</p>
    <div class="hero-cta">
      <button class="btn-primary" onclick="document.getElementById('catalog').scrollIntoView({behavior:'smooth'})">Shop the drop</button>
      <button class="btn-ghost" onclick="setCat('bags')">View bags</button>
    </div>
    <div class="label-strip">
      <div class="barcode"></div>
      <div class="meta">
        <div><b>SHOES</b> — flat 65€ / pair</div>
        <div><b>BAGS</b> — flat 40€ / piece</div>
        <div>MADE FOR THE ROTATION · 9BC-2026</div>
      </div>
    </div>
  </div>
</section>

<section class="catalog" id="catalog">
  <div class="catalog-head">
    <h2 id="catHeading">Full catalog</h2>
    <div class="count mono"><span id="catCount">0</span> items</div>
  </div>
  <div class="grid" id="grid"></div>
</section>

<footer>
  <div class="footer-inner">
    <div class="col">
      <div class="word">9BCLOTHES</div>
      <p>An independent sneaker &amp; leather goods archive. Colorways rotate weekly — once a box sells out, it's gone.</p>
    </div>
    <div class="cols-right">
      <div class="col">
        <h4>Shop</h4>
        <ul>
          <li>Jordan</li>
          <li>Yeezy</li>
          <li>Asics</li>
          <li>Bags</li>
        </ul>
      </div>
      <div class="col">
        <h4>Info</h4>
        <ul>
          <li>Shipping</li>
          <li>Returns</li>
          <li>Size guide</li>
          <li>Contact</li>
        </ul>
      </div>
    </div>
  </div>
  <div class="fine-print">
    <span>© 2026 9BCLOTHES — Demo storefront</span>
    <span>Shoes 65€ · Bags 40€ · All prices flat rate</span>
  </div>
</footer>

<div class="overlay" id="overlay" onclick="closeCart()"></div>
<div class="drawer" id="drawer">
  <div class="drawer-head">
    <h2>Cart</h2>
    <button onclick="closeCart()">&times;</button>
  </div>
  <div class="drawer-items" id="drawerItems"></div>
  <div class="drawer-foot">
    <div class="drawer-total"><span>Total</span><span id="drawerTotal" class="mono">0€</span></div>
    <button class="btn-primary" onclick="checkout()">Checkout</button>
  </div>
</div>

<script>
/* ---------- Product data ---------- */
const PRODUCTS = [
  {id:1, cat:'jordan', name:'Air Jordan 11 "Metallic Silver"', sku:'AJ11-MSLV', price:65, colors:['#c9cdd1','#dfe2e4','#1c1c1e']},
  {id:2, cat:'jordan', name:'Air Jordan 12 "Black &amp; Varsity Red"', sku:'AJ12-BVRD', price:65, colors:['#101012','#c8102e','#3a3a3c']},
  {id:3, cat:'jordan', name:'Air Jordan 6 "All Red"', sku:'AJ6-ARED', price:65, colors:['#b3121f','#8a0f19','#1a1a1a']},
  {id:4, cat:'jordan', name:'Air Jordan 8 "Bugs Bunny"', sku:'AJ8-BUGS', price:65, colors:['#0e0e10','#3aa6a0','#e6e2d6']},
  {id:5, cat:'jordan', name:'Air Jordan 14 "Black Toe"', sku:'AJ14-BTOE', price:65, colors:['#101012','#c8102e','#f2efe6']},
  {id:6, cat:'jordan', name:'Air Jordan 5 "Black Metallic Silver"', sku:'AJ5-BMSV', price:65, colors:['#131315','#9aa0a4','#c8102e']},
  {id:7, cat:'jordan', name:'Air Jordan 5 "Metallic Silver Blue"', sku:'AJ5-SVBL', price:65, colors:['#a9adb0','#26417a','#e9e6dc']},
  {id:8, cat:'jordan', name:'Air Jordan 3 "Black Cat"', sku:'AJ3-BCAT', price:65, colors:['#0c0c0d','#232324','#3a3a3c']},
  {id:9, cat:'jordan', name:'Air Jordan 11 "Gamma Blue"', sku:'AJ11-GBLU', price:65, colors:['#0e0e10','#2f5fb0','#c9cdd1']},
  {id:10, cat:'jordan', name:'Air Jordan 11 "Gratitude"', sku:'AJ11-GRTD', price:65, colors:['#0c0c0d','#c9a227','#232324']},
  {id:11, cat:'jordan', name:'Air Jordan 14 "Black University Blue"', sku:'AJ14-BUBL', price:65, colors:['#101012','#7fb2e0','#f2efe6']},
  {id:12, cat:'jordan', name:'Air Jordan 6 "Grey"', sku:'AJ6-CGRY', price:65, colors:['#8b8d8f','#6c6e70','#e9e6dc']},
  {id:13, cat:'jordan', name:'Air Jordan 12 "Black &amp; White Taxi"', sku:'AJ12-TAXI', price:65, colors:['#0e0e10','#f2c230','#f2efe6']},
  {id:14, cat:'yeezy', name:'Yeezy 700', sku:'YZY-700-WV', price:65, colors:['#b7ac97','#7c7466','#4a4640']},
  {id:15, cat:'asics', name:'Asics GEL-NYC "Blue &amp; White"', sku:'GELNYC-BLWH', price:65, colors:['#f2efe6','#1e5aa8','#c9cdd1']},
  {id:16, cat:'asics', name:'Asics Kayano "All Black"', sku:'KYNO-BLK', price:65, colors:['#0c0c0d','#232324','#3a3a3c']},
  {id:17, cat:'asics', name:'Asics "Cloud Grey"', sku:'AS-CLOUD-GRY', price:65, colors:['#c9cdd1','#a9adb0','#e9e6dc']},
  {id:18, cat:'asics', name:'Asics GEL-NYC "Cloud Grey"', sku:'GELNYC-CGRY', price:65, colors:['#c9cdd1','#8b8d8f','#f2efe6']},
  {id:19, cat:'asics', name:'Asics Kayano "Sky Blue &amp; White"', sku:'KYNO-SKBL', price:65, colors:['#f2efe6','#6fa8d8','#c9cdd1']},
  {id:20, cat:'bags', name:'Goyardine Belvedere II', sku:'GOY-BLVD2', price:40, colors:['#0e0e10','#6c6e70','#f2efe6'], type:'bag'},
];

/* ---------- Icon builders ---------- */
function shoeIcon(colors){
  const [c1,c2,c3] = colors;
  return `
  <svg viewBox="0 0 240 120" xmlns="http://www.w3.org/2000/svg">
    <path d="M10,100 Q5,111 22,113 L202,113 Q227,113 231,95 Q233,84 214,84 L40,84 Q14,84 10,100 Z" fill="${c3}"/>
    <path d="M22,84 Q17,48 58,34 Q94,20 145,25 Q194,30 208,54 Q218,68 213,84 Z" fill="${c1}"/>
    <path d="M22,84 Q19,63 37,49 Q52,38 72,41 Q83,55 72,76 Q56,86 22,86 Z" fill="${c2}"/>
    <path d="M168,29 Q184,13 206,24 Q212,40 201,55 Z" fill="${c2}" opacity="0.9"/>
    <g stroke="${c3}" stroke-width="2.4" stroke-linecap="round" opacity="0.85">
      <line x1="96" y1="34" x2="112" y2="52"/>
      <line x1="110" y1="30" x2="126" y2="49"/>
      <line x1="124" y1="27" x2="140" y2="46"/>
      <line x1="138" y1="26" x2="154" y2="45"/>
    </g>
  </svg>`;
}
function bagIcon(colors){
  const [c1,c2,c3] = colors;
  const pid = 'chev'+Math.random().toString(36).slice(2,8);
  return `
  <svg viewBox="0 0 240 120" xmlns="http://www.w3.org/2000/svg">
    <defs>
      <pattern id="${pid}" width="14" height="14" patternTransform="rotate(45)" patternUnits="userSpaceOnUse">
        <rect width="14" height="14" fill="${c1}"/>
        <rect width="7" height="14" fill="${c2}" opacity="0.55"/>
      </pattern>
    </defs>
    <path d="M62,38 Q62,20 90,20 Q98,10 120,10 Q142,10 150,20 Q178,20 178,38 L184,104 Q184,113 174,113 L66,113 Q56,113 56,104 Z" fill="url(#${pid})" stroke="${c3}" stroke-width="2"/>
    <path d="M90,20 Q94,42 90,52" fill="none" stroke="${c3}" stroke-width="4" stroke-linecap="round"/>
    <path d="M150,20 Q146,42 150,52" fill="none" stroke="${c3}" stroke-width="4" stroke-linecap="round"/>
    <rect x="108" y="55" width="24" height="16" rx="2" fill="${c3}" opacity="0.9"/>
  </svg>`;
}

/* ---------- Render ---------- */
const grid = document.getElementById('grid');
let currentCat = 'all';

function render(){
  const items = PRODUCTS.filter(p => currentCat === 'all' || p.cat === currentCat);
  document.getElementById('catCount').textContent = items.length;
  document.getElementById('catHeading').textContent =
    currentCat === 'all' ? 'Full catalog' :
    currentCat === 'bags' ? 'Bags' :
    currentCat.charAt(0).toUpperCase() + currentCat.slice(1);

  grid.innerHTML = items.map(p => `
    <div class="card">
      <div class="tag">${p.type === 'bag' ? 'Leather goods' : p.cat}</div>
      <div class="icon-wrap">${p.type === 'bag' ? bagIcon(p.colors) : shoeIcon(p.colors)}</div>
      <div class="info">
        <div class="name">${p.name}</div>
        <div class="sku mono">SKU ${p.sku}</div>
        <div class="swatches">${p.colors.map(c=>`<span class="swatch" style="background:${c}"></span>`).join('')}</div>
        <div class="bottom-row">
          <span class="price">${p.price}€</span>
          <button class="add" onclick="addToCart(${p.id}, this)">Add to cart</button>
        </div>
      </div>
    </div>
  `).join('');
}

function setCat(cat){
  currentCat = cat;
  document.querySelectorAll('#tabs button').forEach(b => b.classList.toggle('active', b.dataset.cat === cat));
  render();
}
document.getElementById('tabs').addEventListener('click', e => {
  if(e.target.tagName === 'BUTTON') setCat(e.target.dataset.cat);
});

/* ---------- Cart ---------- */
let cart = [];

function addToCart(id, btn){
  const p = PRODUCTS.find(x => x.id === id);
  cart.push(p);
  updateCartUI();
  if(btn){
    btn.textContent = 'Added ✓';
    btn.classList.add('added');
    setTimeout(()=>{ btn.textContent='Add to cart'; btn.classList.remove('added'); }, 1200);
  }
}
function removeFromCart(idx){
  cart.splice(idx,1);
  updateCartUI();
}
function updateCartUI(){
  document.getElementById('cartCount').textContent = cart.length;
  const total = cart.reduce((s,p)=>s+p.price,0);
  document.getElementById('drawerTotal').textContent = total + '€';
  const wrap = document.getElementById('drawerItems');
  if(cart.length === 0){
    wrap.innerHTML = `<div class="drawer-empty">Your cart is empty.<br>Go find something to cop.</div>`;
    return;
  }
  wrap.innerHTML = cart.map((p,idx) => `
    <div class="drawer-item">
      <div class="icon-mini">${p.type === 'bag' ? bagIcon(p.colors) : shoeIcon(p.colors)}</div>
      <div class="di-info">
        <div class="di-name">${p.name}</div>
        <div class="di-row">
          <span class="di-price mono">${p.price}€</span>
          <button class="remove" onclick="removeFromCart(${idx})">Remove</button>
        </div>
      </div>
    </div>
  `).join('');
}

function openCart(){
  document.getElementById('drawer').classList.add('open');
  document.getElementById('overlay').classList.add('open');
}
function closeCart(){
  document.getElementById('drawer').classList.remove('open');
  document.getElementById('overlay').classList.remove('open');
}
function checkout(){
  if(cart.length === 0){ alert('Your cart is empty.'); return; }
  const total = cart.reduce((s,p)=>s+p.price,0);
  alert('Demo checkout — total ' + total + '€. Hook this up to real payments when you are ready.');
}

render();
updateCartUI();
</script>

</body>
</html>
