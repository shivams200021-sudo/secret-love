<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Special Proposal 💖</title>

<style>
body {
    margin:0;
    overflow:hidden;
    font-family: Arial, sans-serif;
    background:black;
    color:white;
}

.section {
    position:absolute;
    width:100%;
    height:100%;
    display:flex;
    justify-content:center;
    align-items:center;
    flex-direction:column;
    text-align:center;
    transition:1s;
}

.hidden {
    transform:translateX(100%);
    opacity:0;
}

button {
    padding:12px 30px;
    font-size:20px;
    border:none;
    border-radius:30px;
    cursor:pointer;
    margin-top:20px;
}

/* Stars */
.star {
    position:absolute;
    width:2px;
    height:2px;
    background:white;
    animation:fall 5s linear infinite;
}

@keyframes fall {
    0%{transform:translateY(-10px);opacity:1;}
    100%{transform:translateY(100vh);opacity:0;}
}
</style>
</head>

<body>

<!-- PAGE 1 -->
<div class="section" id="page1">
    <h1>Hey... 💌</h1>
    <h2>I have something special for you</h2>
    <button onclick="next('page1','page2')">Open 💖</button>
</div>

<!-- PAGE 2 -->
<div class="section hidden" id="page2">
    <h1>From the first day I saw you ❤️</h1>
    <button onclick="next('page2','page3')">Next ➜</button>
</div>

<!-- PAGE 3 -->
<div class="section hidden" id="page3">
    <h1>You make my world brighter ✨</h1>
    <button onclick="next('page3','page4')">Continue ➜</button>
</div>

<!-- PAGE 4 -->
<div class="section hidden" id="page4">
    <h1>I want you in my future 💞</h1>
    <button onclick="startCountdown()">Final Question 💍</button>
</div>

<!-- PAGE 5 -->
<div class="section hidden" id="page5">
    <h1 id="countdown">3</h1>
</div>

<script>

/* Smooth page switch */
function next(current,nextPage){
    document.getElementById(current).classList.add("hidden");
    setTimeout(()=>{
        document.getElementById(nextPage).classList.remove("hidden");
    },500);
}

/* Countdown */
function startCountdown(){
    next('page4','page5');
    let count=3;
    let el=document.getElementById("countdown");

    let interval=setInterval(()=>{
        count--;
        if(count>0){
            el.innerHTML=count;
        }else{
            clearInterval(interval);
            showProposal();
        }
    },1000);
}

function showProposal(){
    document.getElementById("page5").innerHTML=`
    <h1>Will You Be Mine Forever? 💖</h1>
    <button onclick="celebrate()" style="background:lime;color:black;">YES 😍</button>
    <button id="noBtn" style="background:red;color:white;position:absolute;">NO 😅</button>
    `;

    const noBtn=document.getElementById("noBtn");
    noBtn.addEventListener("mouseover",()=>{
        noBtn.style.left=Math.random()*window.innerWidth+"px";
        noBtn.style.top=Math.random()*window.innerHeight+"px";
    });
}

/* Falling stars */
function createStar(){
    const star=document.createElement("div");
    star.classList.add("star");
    star.style.left=Math.random()*window.innerWidth+"px";
    document.body.appendChild(star);
    setTimeout(()=>{star.remove();},5000);
}
setInterval(createStar,200);

/* Fireworks */
function celebrate(){
    document.body.innerHTML="<h1 style='margin-top:20%;font-size:60px;color:pink;'>Yayyyyy ❤️ I Love Youuuu 😍</h1>";
    for(let i=0;i<150;i++){
        const fire=document.createElement("div");
        fire.style.position="absolute";
        fire.style.width="6px";
        fire.style.height="6px";
        fire.style.background="hsl("+Math.random()*360+",100%,50%)";
        fire.style.left=Math.random()*window.innerWidth+"px";
        fire.style.top=Math.random()*window.innerHeight+"px";
        fire.style.borderRadius="50%";
        document.body.appendChild(fire);
    }
}
</script>

</body>
</html>
