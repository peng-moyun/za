<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>可以做我的小狗吗</title>
    <link href="https://fonts.googleapis.com/css2?family=Ma+Shan+Zheng&display=swap" rel="stylesheet">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            /* 修改背景图部分 - 使用外部图片链接 */
            background: #fff9f9 url('https://images.unsplash.com/photo-1517423568366-8b83523034fd?q=80&w=1935') center/cover no-repeat;
            background-attachment: fixed;
            font-family: 'Ma Shan Zheng', cursive, sans-serif;
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
            padding: 20px;
            color: #8B4513;
            overflow-x: hidden;
        }
        
        .container {
            background-color: rgba(255, 253, 248, 0.92);
            border-radius: 25px;
            box-shadow: 0 15px 35px rgba(139, 69, 19, 0.15);
            padding: 50px 40px;
            text-align: center;
            max-width: 700px;
            width: 90%;
            margin: 20px auto;
            border: 3px dashed #ffb6c1;
            position: relative;
            z-index: 2;
        }
        
        h1 {
            font-size: 4.5rem;
            margin-bottom: 50px;
            color: #e67a9e;
            text-shadow: 4px 4px 0 #ffd6e7;
            letter-spacing: 2px;
            position: relative;
            padding-bottom: 20px;
            animation: floatTitle 3s infinite alternate;
        }
        
        h1::after {
            content: "";
            position: absolute;
            bottom: 0;
            left: 25%;
            right: 25%;
            height: 5px;
            background: linear-gradient(to right, transparent, #f9a8d4, transparent);
            border-radius: 3px;
        }
        
        @keyframes floatTitle {
            0% { transform: translateY(0); }
            100% { transform: translateY(-10px); }
        }
        
        .buttons {
            display: flex;
            justify-content: center;
            gap: 40px;
            margin: 50px 0;
        }
        
        .btn {
            padding: 18px 60px;
            font-size: 2rem;
            font-family: inherit;
            border: none;
            border-radius: 60px;
            cursor: pointer;
            transition: all 0.3s ease;
            position: relative;
            overflow: hidden;
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.12);
            font-weight: bold;
            letter-spacing: 1px;
        }
        
        .btn:hover {
            transform: translateY(-8px) scale(1.05);
            box-shadow: 0 12px 25px rgba(0, 0, 0, 0.2);
        }
        
        .btn:active {
            transform: translateY(3px);
        }
        
        #yes-btn {
            background: linear-gradient(135deg, #a8e6cf, #7bc8a4);
            color: #2c5e4f;
        }
        
        #no-btn {
            background: linear-gradient(135deg, #ffaaa5, #ff8b94);
            color: #8b0000;
        }
        
        .btn::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(255, 255, 255, 0.3);
            transform: translateX(-100%) skewX(-20deg);
            transition: transform 0.6s ease;
        }
        
        .btn:hover::after {
            transform: translateX(200%) skewX(-20deg);
        }
        
        .dog-paws {
            position: absolute;
            width: 100%;
            height: 100%;
            top: 0;
            left: 0;
            pointer-events: none;
            z-index: 1;
        }
        
        .paw {
            position: absolute;
            font-size: 2.5rem;
            opacity: 0.15;
            animation: float 15s infinite linear;
        }
        
        @keyframes float {
            0% { transform: translateY(0) rotate(0deg); }
            100% { transform: translateY(-100vh) rotate(360deg); }
        }
        
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.7);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background: white;
            padding: 50px;
            border-radius: 25px;
            text-align: center;
            max-width: 600px;
            width: 90%;
            box-shadow: 0 20px 50px rgba(0, 0, 0, 0.3);
            position: relative;
            animation: popIn 0.5s;
            border: 4px solid #ffb6c1;
        }
        
        @keyframes popIn {
            0% { transform: scale(0.5); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }
        
        .modal-content h2 {
            font-size: 3rem;
            margin-bottom: 30px;
            color: #e67a9e;
        }
        
        .modal-content p {
            font-size: 1.8rem;
            margin-bottom: 40px;
            line-height: 1.6;
            color: #8B4513;
        }
        
        .modal-btn {
            padding: 15px 50px;
            font-size: 1.8rem;
            background: linear-gradient(to right, #ffb6c1, #ff9aac);
            color: white;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s;
            font-family: inherit;
            box-shadow: 0 5px 15px rgba(255, 150, 172, 0.4);
        }
        
        .modal-btn:hover {
            background: linear-gradient(to right, #ff9aac, #ff7d97);
            transform: scale(1.05);
        }
        
        .second-chance-btns {
            display: flex;
            gap: 20px;
            justify-content: center;
            margin-top: 30px;
        }
        
        .heart {
            position: absolute;
            font-size: 2rem;
            color: #ff6b9c;
            animation: floatHeart 8s infinite linear;
            opacity: 0.7;
        }
        
        @keyframes floatHeart {
            0% { transform: translateY(0) translateX(0) rotate(0deg); opacity: 0; }
            10% { opacity: 1; }
            90% { opacity: 1; }
            100% { transform: translateY(-100vh) translateX(50px) rotate(360deg); opacity: 0; }
        }
        
        @media (max-width: 768px) {
            h1 {
                font-size: 3rem;
            }
            
            .buttons {
                flex-direction: column;
                gap: 25px;
            }
            
            .btn {
                width: 100%;
                padding: 15px;
                font-size: 1.8rem;
            }
            
            .modal-content {
                padding: 30px;
            }
            
            .modal-content h2 {
                font-size: 2.2rem;
            }
            
            .modal-content p {
                font-size: 1.4rem;
            }
            
            .modal-btn {
                padding: 12px 30px;
                font-size: 1.4rem;
            }
            
            .second-chance-btns {
                flex-direction: column;
                gap: 15px;
            }
        }
    </style>
</head>
<body>
    <!-- 飘落的爪印 -->
    <div class="dog-paws">
        <div class="paw" style="top: 10%; left: 15%; animation-delay: 0s;">🐾</div>
        <div class="paw" style="top: 20%; left: 80%; animation-delay: -2s;">🐾</div>
        <div class="paw" style="top: 40%; left: 5%; animation-delay: -4s;">🐾</div>
        <div class="paw" style="top: 60%; left: 90%; animation-delay: -6s;">🐾</div>
        <div class="paw" style="top: 80%; left: 20%; animation-delay: -8s;">🐾</div>
        <div class="paw" style="top: 30%; left: 50%; animation-delay: -10s;">🐾</div>
        
        <!-- 飘落的心形 -->
        <div class="heart" style="left: 5%; animation-delay: -1s;">❤️</div>
        <div class="heart" style="left: 20%; animation-delay: -3s;">❤️</div>
        <div class="heart" style="left: 40%; animation-delay: -5s;">❤️</div>
        <div class="heart" style="left: 60%; animation-delay: -7s;">❤️</div>
        <div class="heart" style="left: 80%; animation-delay: -9s;">❤️</div>
        <div class="heart" style="left: 95%; animation-delay: -11s;">❤️</div>
    </div>

    <div class="container">
        <h1>可以做我的小狗吗</h1>
        
        <div class="buttons">
            <button id="yes-btn" class="btn">Yes</button>
            <button id="no-btn" class="btn">No</button>
        </div>
    </div>
    
    <!-- 恭喜模态框 -->
    <div id="congrats-modal" class="modal">
        <div class="modal-content">
            <h2>恭喜！</h2>
            <p>你获得了一个永远爱你的主人！❤️</p>
            <button class="modal-btn" onclick="closeModal('congrats-modal')">太棒了</button>
        </div>
    </div>
    
    <!-- 重新考虑模态框 -->
    <div id="reconsider-modal" class="modal">
        <div class="modal-content">
            <h2>等一下！</h2>
            <p>不再仔细想想了吗，确定吗？</p>
        </div>
    </div>
    
    <!-- 第二次选择模态框 -->
    <div id="second-chance-modal" class="modal">
        <div class="modal-content">
            <h2>请再考虑一下</h2>
            <p>你真的要拒绝这么可爱的请求吗？</p>
            <div class="second-chance-btns">
                <button class="modal-btn" onclick="showCongrats()">Yes</button>
                <button class="modal-btn" onclick="showCongrats()">Yes</button>
            </div>
        </div>
    </div>

    <script>
        // 获取DOM元素
        const yesBtn = document.getElementById('yes-btn');
        const noBtn = document.getElementById('no-btn');
        const congratsModal = document.getElementById('congrats-modal');
        const reconsiderModal = document.getElementById('reconsider-modal');
        const secondChanceModal = document.getElementById('second-chance-modal');
        
        // 为按钮添加事件监听器
        yesBtn.addEventListener('click', () => {
            showCongrats();
        });
        
        noBtn.addEventListener('click', () => {
            // 显示重新考虑模态框
            reconsiderModal.style.display = 'flex';
            
            // 3秒后关闭重新考虑模态框并显示第二次选择模态框
            setTimeout(() => {
                reconsiderModal.style.display = 'none';
                secondChanceModal.style.display = 'flex';
            }, 3000);
        });
        
        // 显示恭喜模态框的函数
        function showCongrats() {
            // 关闭其他所有模态框
            reconsiderModal.style.display = 'none';
            secondChanceModal.style.display = 'none';
            
            // 显示恭喜模态框
            congratsModal.style.display = 'flex';
        }
        
        // 关闭模态框的函数
        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }
        
        // 点击模态框外部关闭模态框
        window.addEventListener('click', (event) => {
            if (event.target.classList.contains('modal')) {
                event.target.style.display = 'none';
            }
        });
        
        // 创建更多飘落元素
        function createFallingElements() {
            const container = document.querySelector('.dog-paws');
            for (let i = 0; i < 10; i++) {
                const paw = document.createElement('div');
                paw.classList.add('paw');
                paw.innerHTML = '🐾';
                paw.style.left = `${Math.random() * 100}%`;
                paw.style.top = `-${Math.random() * 30}%`;
                paw.style.animationDelay = `-${Math.random() * 12}s`;
                container.appendChild(paw);
                
                const heart = document.createElement('div');
                heart.classList.add('heart');
                heart.innerHTML = '❤️';
                heart.style.left = `${Math.random() * 100}%`;
                heart.style.top = `-${Math.random() * 30}%`;
                heart.style.animationDelay = `-${Math.random() * 12}s`;
                container.appendChild(heart);
            }
        }
        
        // 初始化页面
        window.addEventListener('load', () => {
            createFallingElements();
        });
    </script>
</body>
</html>
