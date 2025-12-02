
<html lang="hu">
<head>
        <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Focusly - A Hallgatói Siker Kulcsa</title>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700;800;900&display=swap" rel="stylesheet">
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Javított Lucide script forrás -->
    <script src="https://unpkg.com/lucide@latest"></script>
    
    <style>
        /* --- GLOBAL STYLES --- */
        html {
            scroll-behavior: smooth;
        }
        
        body {
            overflow-x: hidden;
            overflow-y: auto;
        }

        /* --- IPHONE 12 STYLE (Scoped to .phone-frame) --- */
        :root {
            --text-pink: #e07a86;
            --icon-light: #e2d9f0;
            --bg-btn: rgba(255, 255, 255, 0.08);
            --border-btn: rgba(255, 255, 255, 0.12);
        }

        .phone-stage {
            display: flex;
            justify-content: center;
            align-items: center;
            padding-top: 20px;
            padding-bottom: 20px;
            width: 100%;
        }

        /* --- IPHONE 12 FORMÁJÚ KERET --- */
        .phone-frame {
            width: 380px;
            height: 820px;
            background-color: #111;
            border-radius: 50px;
            box-shadow: 
                inset 0 0 0 4px #333,
                0 0 0 10px #111,     
                20px 30px 50px rgba(0,0,0,0.3);
            padding: 0; 
            position: relative;
            z-index: 10;
            flex-shrink: 0;
            margin: 0 auto;
            transition: all 0.3s ease;
        }

        /* Notch (Sziget) */
        .phone-frame .phone-notch {
            position: absolute;
            top: 0;
            left: 50%;
            transform: translateX(-50%);
            width: 160px;
            height: 32px;
            background-color: #111;
            border-bottom-left-radius: 18px;
            border-bottom-right-radius: 18px;
            z-index: 20;
        }

        /* Képernyő */
        .phone-frame .phone-screen {
            width: 100%;
            height: 100%;
            background-color: #3b1578;
            background: 
                radial-gradient(circle at 80% 20%, #6e3ba6 0%, transparent 50%),
                radial-gradient(circle at 20% 80%, #2d0e55 0%, transparent 50%),
                linear-gradient(135deg, #4b1f8f 0%, #301060 100%);
            border-radius: 42px; 
            overflow: hidden;
            position: relative;
        }

        /* --- TARTALOM (Scoped) --- */
        .phone-frame .app-container {
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            padding: 50px 24px 30px 24px; 
            position: relative;
            font-family: 'Inter', sans-serif;
            color: white;
        }

        .phone-frame header {
            margin-bottom: 20px;
            display: flex;
            flex-direction: column;
            gap: 20px;
            flex-shrink: 0;
        }

        .phone-frame .logo {
            font-family: 'Inter', sans-serif;
            font-size: 42px;
            font-weight: 900;
            color: #ffffff;
            letter-spacing: -1px;
            line-height: 1;
            margin-bottom: 5px;
        }

        .phone-frame .top-nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .phone-frame .icon-group {
            display: flex;
            gap: 10px;
        }

        .phone-frame .nav-btn {
            width: 42px;
            height: 42px;
            border-radius: 50%;
            background: var(--bg-btn);
            border: 1px solid var(--border-btn);
            display: flex;
            justify-content: center;
            align-items: center;
            cursor: pointer;
            transition: all 0.2s;
            color: var(--icon-light);
        }
        
        .phone-frame .nav-btn:hover { background: rgba(255, 255, 255, 0.15); }

        .phone-frame .nav-btn svg {
            stroke: currentColor;
            stroke-width: 2;
            fill: none;
            stroke-linecap: round;
            stroke-linejoin: round;
        }

        .phone-frame .points-pill {
            background: #4e2a6e;
            border: 1px solid #7a5a48;
            height: 42px;
            padding: 0 14px;
            border-radius: 21px;
            display: flex;
            align-items: center;
            gap: 8px;
            box-shadow: 0 4px 12px rgba(0,0,0,0.2);
        }

        .phone-frame .points-value {
            font-family: 'Inter', sans-serif;
            font-weight: 800; 
            font-size: 15px;
            color: #fff;
            padding-top: 0; 
            line-height: 1;
        }

        .phone-frame .glass-card {
            flex-grow: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: space-between;
            background: linear-gradient(180deg, rgba(255, 255, 255, 0.07) 0%, rgba(255, 255, 255, 0.02) 100%);
            border: 1px solid;
            border-image-source: linear-gradient(180deg, rgba(255,255,255,0.2) 0%, rgba(255,255,255,0.05) 100%);
            border-radius: 36px;
            padding: 30px 20px 40px 20px;
            backdrop-filter: blur(15px);
            box-shadow: 0 20px 50px rgba(0,0,0,0.2);
            margin-bottom: 10px;
        }

        .phone-frame .card-title {
            font-family: 'Inter', sans-serif;
            font-size: 20px;
            font-weight: 800;
            letter-spacing: -0.3px;
            color: #fff;
            margin-top: 5px;
        }

        .phone-frame .timer-wrapper {
            position: relative;
            width: 280px;
            height: 280px;
            display: flex;
            justify-content: center;
            align-items: center;
            margin-top: auto;
            margin-bottom: auto;
        }

        .phone-frame .timer-content {
            position: absolute;
            display: flex;
            flex-direction: column;
            align-items: center;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
        }

        .phone-frame .time-digits {
            font-family: system-ui, -apple-system, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
            font-size: 60px;
            font-weight: 200;
            letter-spacing: -2px; 
            line-height: 1;
            margin-bottom: 8px;
            font-variant-numeric: tabular-nums;
            margin-top: -5px; 
            color: white;
        }

        .phone-frame .focus-label {
            font-size: 12px;
            letter-spacing: 2px;
            font-weight: 600;
            color: rgba(255, 255, 255, 0.6);
            text-transform: uppercase;
        }

        .phone-frame svg.ring-svg {
            transform: rotate(-90deg);
            width: 100%;
            height: 100%;
        }

        .phone-frame .ring-bg {
            fill: none;
            stroke: rgba(255, 255, 255, 0.03);
            stroke-width: 13; 
            stroke-linecap: round;
        }

        .phone-frame .ring-progress {
            fill: none;
            stroke: url(#gradientPink);
            stroke-width: 13;
            stroke-linecap: round;
            stroke-dasharray: 880;
            stroke-dashoffset: 572;
            transition: stroke-dashoffset 1s linear;
        }
        
        /* Animáció a gyűrűhöz */
        @keyframes ringLoad {
            from { stroke-dashoffset: 880; }
            to { stroke-dashoffset: 572; }
        }
        .animating-ring {
            animation: ringLoad 2s ease-out forwards;
        }

        .phone-frame .stop-btn {
            background: #fff;
            color: var(--text-pink);
            border: none;
            padding: 16px 48px;
            border-radius: 30px;
            font-size: 18px;
            font-family: 'Inter', sans-serif;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 12px;
            cursor: pointer;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.15);
            transition: all 0.2s;
        }

        .phone-frame .stop-btn:active { transform: scale(0.95); }
        .phone-frame .stop-btn.stopped {
            background: #e07a86;
            color: white;
        }

        .phone-frame .stop-icon-svg {
            width: 20px;
            height: 20px;
            stroke: currentColor;
            stroke-width: 2.5;
            fill: none;
            rx: 3px;
        }

        .phone-frame .home-indicator {
            position: absolute;
            bottom: 8px;
            left: 50%;
            transform: translateX(-50%);
            width: 130px;
            height: 5px;
            background-color: rgba(255,255,255,0.3);
            border-radius: 10px;
            z-index: 100;
        }

        /* --- LANDING PAGE STYLES --- */
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8fafc;
            color: #1e293b;
        }
        
        .blob {
            position: absolute;
            filter: blur(80px);
            z-index: -1;
            opacity: 0.5;
        }
        
        .blob-purple {
            background-color: #d8b4fe;
            width: 400px;
            height: 400px;
            border-radius: 50%;
            top: -100px;
            right: -100px;
        }

        .blob-pink {
            background-color: #fbcfe8;
            width: 300px;
            height: 300px;
            border-radius: 50%;
            bottom: 0;
            left: -50px;
        }

        .feature-card:hover {
            transform: translateY(-5px);
        }
    </style>
</head>
<body class="antialiased">

    <!-- Navigation -->
    <nav class="sticky top-0 z-50 w-full bg-white/90 backdrop-blur-md border-b border-gray-100 shadow-sm transition-all duration-300">
        <div class="max-w-7xl mx-auto px-6 md:px-12 py-4 flex flex-col md:flex-row justify-between items-center gap-4 md:gap-0">
            
            <!-- Logo és Mobil Gomb sor -->
            <div class="w-full md:w-auto flex justify-between items-center">
                <div class="text-2xl font-black tracking-tighter text-[#3b1578] cursor-pointer" onclick="window.scrollTo(0,0)">Focusly</div>
                
                <!-- Mobil Kapcsolat Gomb (Csak mobilon látszik) -->
                <a href="#contact" class="md:hidden bg-[#3b1578] text-white px-5 py-2 rounded-lg font-bold text-sm hover:bg-[#2d0e55] transition smooth-scroll">
                    Kapcsolat
                </a>
            </div>

            <!-- Linkek -->
            <div class="w-full md:w-auto pt-3 md:pt-0 flex flex-wrap justify-center items-center gap-4 md:gap-8 font-bold text-[#3b1578] text-sm md:text-base">
                <a href="#why-us" class="hover:text-[#e07a86] transition smooth-scroll relative group">
                    Miért a Focusly?
                    <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-[#e07a86] transition-all group-hover:w-full"></span>
                </a>
                
                <!-- ELVÁLASZTÓ VONAL -->
                <span class="w-px h-4 bg-gray-300"></span>

                <a href="#benefits" class="hover:text-[#e07a86] transition smooth-scroll relative group">
                    Előnyök
                    <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-[#e07a86] transition-all group-hover:w-full"></span>
                </a>

                <!-- ELVÁLASZTÓ VONAL -->
                <span class="w-px h-4 bg-gray-300"></span>

                <a href="#how-it-works" class="hover:text-[#e07a86] transition smooth-scroll relative group">
                    Integráció
                    <span class="absolute -bottom-1 left-0 w-0 h-0.5 bg-[#e07a86] transition-all group-hover:w-full"></span>
                </a>
            </div>

            <!-- Asztali Kapcsolat Gomb (Csak asztali nézetben látszik) -->
            <a href="#contact" class="hidden md:inline-block bg-[#3b1578] text-white px-6 py-2.5 rounded-lg font-bold hover:bg-[#2d0e55] transition shadow-lg hover:shadow-xl transform hover:-translate-y-0.5 smooth-scroll">
                Kapcsolatfelvétel
            </a>
        </div>
    </nav>

    <!-- Hero Section -->
    <section class="relative pt-10 pb-20 md:pt-16 md:pb-32 overflow-hidden">
        
        <div class="max-w-7xl mx-auto px-6 md:px-12 flex flex-col gap-10 items-center">
            
            <!-- Text Content -->
            <div class="space-y-6 relative z-20 text-center max-w-4xl mx-auto">
                <div class="inline-flex items-center gap-2 px-4 py-2 rounded-full bg-purple-100 text-[#3b1578] text-sm font-bold uppercase tracking-wider justify-center">
                    <span class="w-2 h-2 rounded-full bg-[#3b1578] animate-pulse"></span>
                    Innovatív oktatási megoldás
                </div>
                
                <h1 class="text-5xl md:text-6xl lg:text-7xl font-black leading-tight tracking-tight text-gray-900">
                    Segítjük és jutalmazzuk <br>
                    <span class="text-transparent bg-clip-text bg-gradient-to-r from-[#3b1578] to-[#e07a86]">a hatékony tanulást.</span>
                </h1>
                
                <!-- Új konténer a szövegnek és a kiscímnek, elválasztva a főcímtől -->
                <div class="mt-8 pt-6">
                    <h3 class="text-[#e07a86] font-bold text-sm md:text-base tracking-widest uppercase mb-3">Hogyan működik?</h3>
                    <p class="text-lg md:text-xl text-gray-600 leading-relaxed max-w-2xl mx-auto">
                        Segítünk a hallgatóknak legyőzni a digitális zajt. A felhasználók elindítják a fókuszidőt, a Focusly pedig blokkolja a zavaró appokat. A fókuszidőért pontokat kapnak, amelyek beválthatóak lesznek különböző kuponokra.
                    </p>
                </div>

                <div class="flex flex-col sm:flex-row gap-4 items-center justify-center">
                    <!-- GOMB TÖRÖLVE -->
                </div>
            </div>

            <!-- The Interactive Phone -->
            <div class="relative z-20 flex justify-center w-full scale-75 md:scale-90 lg:scale-100 transform origin-center">
                <div class="phone-stage">
                    
                    <!-- INSERTED PHONE FRAME CODE START -->
                    <div class="phone-frame">
                        <div class="phone-notch"></div>
                        
                        <div class="phone-screen">
                            <div class="app-container">
                                <header>
                                    <div class="logo">Focusly</div>
                                    
                                    <div class="top-nav">
                                        <div class="icon-group">
                                            <div class="nav-btn">
                                                <svg width="22" height="22" viewBox="0 0 24 24">
                                                    <circle cx="12" cy="12" r="3"></circle>
                                                    <path d="M19.4 15a1.65 1.65 0 0 0 .33 1.82l.06.06a2 2 0 0 1 0 2.83 2 2 0 0 1-2.83 0l-.06-.06a1.65 1.65 0 0 0-1.82-.33 1.65 1.65 0 0 0-1 1.51V21a2 2 0 0 1-2 2 2 2 0 0 1-2-2v-.09A1.65 1.65 0 0 0 9 19.4a1.65 1.65 0 0 0-1.82.33l-.06.06a2 2 0 0 1-2.83 0 2 2 0 0 1 0-2.83l.06-.06a1.65 1.65 0 0 0 .33-1.82 1.65 1.65 0 0 0-1.51-1H3a2 2 0 0 1-2-2 2 2 0 0 1 2-2h.09A1.65 1.65 0 0 0 4.6 9a1.65 1.65 0 0 0-.33-1.82l-.06-.06a2 2 0 0 1 0-2.83 2 2 0 0 1 2.83 0l.06.06a1.65 1.65 0 0 0 1.82.33H9a1.65 1.65 0 0 0 1-1.51V3a2 2 0 0 1 2-2 2 2 0 0 1 2 2v.09a1.65 1.65 0 0 0 1.51 1H15a1.65 1.65 0 0 0 1.82-.33l.06-.06a2 2 0 0 1 2.83 0 2 2 0 0 1 0 2.83l-.06.06a1.65 1.65 0 0 0-.33 1.82V9a1.65 1.65 0 0 0 1.51 1H21a2 2 0 0 1 2 2 2 2 0 0 1-2 2h-.09a1.65 1.65 0 0 0-1.51 1z"></path>
                                                </svg>
                                            </div>
        
                                            <div class="nav-btn">
                                                <svg width="22" height="22" viewBox="0 0 24 24">
                                                    <path d="M6 9a6 6 0 0 0 12 0V5H6z"></path>
                                                    <path d="M18 9h1a2 2 0 0 0 2-2v-1a2 2 0 0 0-2-2h-1"></path>
                                                    <path d="M6 9H5a2 2 0 0 1-2-2V6a2 2 0 0 1 2-2h1"></path>
                                                    <path d="M12 15 Q 11 19 8 21 H 16 Q 13 19 12 15"></path>
                                                </svg>
                                            </div>
        
                                            <div class="nav-btn">
                                                <svg width="22" height="22" viewBox="0 0 24 24">
                                                    <path d="M3 3v16a2 2 0 0 0 2 2h16"></path>
                                                    <line x1="8" y1="17" x2="8" y2="12"></line>
                                                    <line x1="13" y1="17" x2="13" y2="8"></line>
                                                    <line x1="18" y1="17" x2="18" y2="12"></line>
                                                </svg>
                                            </div>
        
                                            <div class="nav-btn">
                                                <svg width="22" height="22" viewBox="0 0 24 24">
                                                    <path d="M17 21v-2a4 4 0 0 0-4-4H5a4 4 0 0 0-4 4v2"></path>
                                                    <circle cx="9" cy="7" r="4"></circle>
                                                    <path d="M23 21v-2a4 4 0 0 0-3-3.87"></path>
                                                    <path d="M16 3.13a4 4 0 0 1 0 7.75"></path>
                                                </svg>
                                            </div>
                                        </div>
        
                                        <div class="points-pill">
                                            <svg width="24" height="24" viewBox="0 0 24 24" fill="none">
                                                <circle cx="15" cy="12" r="8" fill="#cba22d" stroke="#e8c966" stroke-width="1"/>
                                                <circle cx="11" cy="12" r="8" fill="#dbb538" stroke="#fce68a" stroke-width="1"/>
                                                <text x="11" y="15.5" font-family="Inter" font-weight="900" font-size="10" fill="#604010" text-anchor="middle">1</text>
                                            </svg>
                                            <span class="points-value">307</span>
                                        </div>
                                    </div>
                                </header>
        
                                <main class="glass-card">
                                    <h2 class="card-title">Focus Session</h2>
        
                                    <div class="timer-wrapper">
                                        <svg class="ring-svg" viewBox="0 0 320 320">
                                            <defs>
                                                <linearGradient id="gradientPink" x1="0%" y1="0%" x2="100%" y2="100%">
                                                    <stop offset="0%" stop-color="#ce3bca" />
                                                    <stop offset="100%" stop-color="#f45d8d" />
                                                </linearGradient>
                                            </defs>
                                            <circle class="ring-bg" cx="160" cy="160" r="140" />
                                            <circle class="ring-progress animating-ring" id="progressRing" cx="160" cy="160" r="140" />
                                        </svg>
        
                                        <div class="timer-content">
                                            <div class="time-digits" id="timerDigits">23:19</div>
                                            <div class="focus-label" id="focusLabel">FOCUSING</div>
                                        </div>
                                    </div>
        
                                    <button class="stop-btn" id="stopButton" onclick="toggleTimer()">
                                        <div id="stopIconContainer">
                                            <svg class="stop-icon-svg" viewBox="0 0 24 24">
                                                <rect x="5" y="5" width="14" height="14" rx="3" ry="3" />
                                            </svg>
                                        </div>
                                        <span id="stopText">Stop</span>
                                    </button>
                                </main>
                            </div>
                            
                            <div class="home-indicator"></div>
                        </div>
                    </div>
                    <!-- INSERTED PHONE FRAME CODE END -->

                </div>
            </div>
        </div>
    </section>

    <!-- Why Us / Stats Section -->
    <section id="why-us" class="scroll-mt-28 bg-white py-20 border-y border-gray-100">
        <div class="max-w-7xl mx-auto px-6">
            <div class="text-center mb-16">
                <h2 class="text-3xl md:text-4xl font-black text-[#3b1578] mb-4">Miért probléma a digitális zaj?</h2>
                <p class="text-gray-600 max-w-2xl mx-auto">Kutatások szerint a hallgatók átlagosan 3-4 percenként nyúlnak a telefonjukhoz tanulás közben. Ez drasztikusan csökkenti a hatékonyságot.</p>
            </div>

            <div class="grid md:grid-cols-3 gap-8">
                <!-- 1. Kártya: Figyelemzavar -->
                <div class="p-8 rounded-3xl bg-gray-50 hover:bg-purple-50 transition feature-card">
                    <div class="w-14 h-14 bg-red-100 rounded-2xl flex items-center justify-center mb-6 text-red-600">
                        <!-- JAVÍTOTT ÉS TESZTELT ÁTHÚZOTT CSENGŐ IKON (BELL-OFF) -->
                        <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <path d="M13.73 21a2 2 0 0 1-3.46 0"></path>
                            <path d="M18.63 13A17.89 17.89 0 0 1 18 8"></path>
                            <path d="M6.26 6.26A5.86 5.86 0 0 0 6 8c0 7-3 9-3 9h14"></path>
                            <path d="M18 8a6 6 0 0 0-9.33-5"></path>
                            <line x1="1" y1="1" x2="23" y2="23"></line>
                        </svg>
                    </div>
                    <h3 class="text-xl font-bold mb-3">Figyelemzavar</h3>
                    <p class="text-gray-600">A közösségi média értesítések megszakítják a "flow" élményt, ami elengedhetetlen a mély tanuláshoz.</p>
                </div>

                <!-- 2. Kártya: Halogatás (ÁTHELYEZVE IDE) -->
                <div class="p-8 rounded-3xl bg-gray-50 hover:bg-purple-50 transition feature-card">
                    <div class="w-14 h-14 bg-blue-100 rounded-2xl flex items-center justify-center mb-6 text-blue-600">
                        <!-- ÓRA IKON (CLOCK) -->
                        <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <circle cx="12" cy="12" r="10"></circle>
                            <polyline points="12 6 12 12 16 14"></polyline>
                        </svg>
                    </div>
                    <h3 class="text-xl font-bold mb-3">Halogatás</h3>
                    <p class="text-gray-600">A "csak még 5 perc" görgetésből órák lesznek, így a tanulás gyakran az utolsó pillanatra marad, növelve a stresszt.</p>
                </div>

                <!-- 3. Kártya: Romló eredmények (ÁTHELYEZVE IDE) -->
                <div class="p-8 rounded-3xl bg-gray-50 hover:bg-purple-50 transition feature-card">
                    <div class="w-14 h-14 bg-orange-100 rounded-2xl flex items-center justify-center mb-6 text-orange-600">
                        <!-- JAVÍTOTT LEFELÉ MUTATÓ GRAFIKON (TRENDING-DOWN) -->
                        <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                            <polyline points="22 17 13.5 8.5 8.5 13.5 2 7"></polyline>
                            <polyline points="16 17 22 17 22 11"></polyline>
                        </svg>
                    </div>
                    <h3 class="text-xl font-bold mb-3">Romló eredmények</h3>
                    <p class="text-gray-600">Kutatások szerint a multitasking akár 40%-kal is csökkentheti a hatékonyságot, ami rosszabb vizsgaeredményekhez vezet.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- Value Proposition for University -->
    <section id="benefits" class="scroll-mt-28 py-20 relative">
        <!-- BLOB REMOVED -->
        <div class="max-w-7xl mx-auto px-6">
            <div class="grid md:grid-cols-2 gap-16 items-center">
                <!-- Kártya konténer: md:order-2 (Jobb oldalra kerül asztalon) -->
                <div class="order-2 md:order-2">
                    <!-- KÁRTYA TARTALMA LECSERÉLVE -->
                    <div class="relative bg-gradient-to-br from-[#3b1578] to-[#2d0e55] rounded-3xl p-8 md:p-12 text-white shadow-2xl text-left border border-white/10">
                        <div class="absolute top-0 right-0 p-6 opacity-10">
                            <i data-lucide="users" width="120" height="120"></i>
                        </div>
                        
                        <i data-lucide="trending-up" class="w-12 h-12 mb-6 text-[#e07a86]"></i>
                        
                        <h3 class="text-2xl font-bold mb-4">Szerezzen behozhatatlan előnyt a felvételin!</h3>
                        
                        <p class="opacity-90 leading-relaxed mb-4 text-lg">
                            Felmérésünk sokkoló eredményt hozott: a végzős középiskolások <span class="font-bold text-[#e07a86] text-xl">42,7%-a</span> előnyben részesítené azt az egyetemet, amely rendelkezik ilyen innovatív hallgatói támogató rendszerrel.
                        </p>
                        
                        <!-- MÓDOSÍTOTT KIEMELÉS: Piaci Előny Doboz -->
                        <div class="my-8 bg-[#3b1578]/50 p-6 rounded-2xl border border-[#e07a86]/30 shadow-[0_0_20px_rgba(224,122,134,0.1)] hover:shadow-[0_0_25px_rgba(224,122,134,0.2)] transition-shadow duration-300">
                            <div class="flex items-start gap-4">
                                <div class="bg-[#e07a86] p-3 rounded-xl text-white flex-shrink-0 shadow-lg">
                                    <!-- ZAP / Villám ikon -->
                                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                                        <polygon points="13 2 3 14 12 14 11 22 21 10 12 10 13 2"></polygon>
                                    </svg>
                                </div>
                                <div>
                                    <h4 class="text-[#e07a86] font-bold text-xs uppercase tracking-widest mb-1">Stratégiai előny</h4>
                                    <p class="text-white text-lg font-medium leading-snug">
                                        Jelenleg az Önök versenytársai még nem rendelkeznek ezzel a szolgáltatással. 
                                        <span class="block mt-1 font-bold text-white">Ez az Önök lehetősége.</span>
                                    </p>
                                </div>
                            </div>
                        </div>

                        <!-- MÓDOSÍTÁS: text-lg hozzáadva a méretezéshez -->
                        <p class="opacity-90 leading-relaxed mb-6 text-lg">
                            Ne hagyja, hogy más intézmények elcsábítsák a legmotiváltabb diákokat! Legyenek Önök az első partnereink, és tűnjenek ki a tömegből egy olyan szolgáltatással, amire a Z generáció valóban vágyik.
                        </p>
                    </div>
                </div>
                
                <!-- Szöveg konténer: md:order-1 (Bal oldalra kerül asztalon) -->
                <div class="order-1 md:order-1 space-y-6 text-center md:text-left">
                    <h2 class="text-4xl font-black text-[#3b1578]">Miért jó ez a Karnak?</h2>
                    <p class="text-lg text-gray-600">
                        A Focusly nem csak egy app, hanem egy eszköz a hallgatói jólét növelésére. A modern egyetemek felismerik, hogy a hallgatók mentális egészsége és tanulási szokásai közvetlen hatással vannak az intézmény hírnevére.
                    </p>
                    <div class="space-y-4 pt-4">
                        
                        <!-- 1. elem: Középre igazítva mobilon -->
                        <div class="flex gap-4 justify-center md:justify-start text-left">
                            <div class="flex-shrink-0 w-12 h-12 rounded-full bg-green-100 flex items-center justify-center text-green-600 font-bold">1</div>
                            <div>
                                <h4 class="font-bold text-lg">Jobb tanulmányi átlagok</h4>
                                <!-- MÓDOSÍTVA: Szöveg átírva -->
                                <p class="text-sm text-gray-500">A fókuszált tanulás közvetlenül javítja a vizsgaeredményeket.</p>
                            </div>
                        </div>
                        
                        <!-- 2. elem: MÓDOSÍTVA -->
                        <div class="flex gap-4 justify-center md:justify-start text-left">
                            <div class="flex-shrink-0 w-12 h-12 rounded-full bg-purple-100 flex items-center justify-center text-purple-600 font-bold">2</div>
                            <div>
                                <h4 class="font-bold text-lg">Mentális egészség védelme</h4>
                                <p class="text-sm text-gray-500">A tudatos digitális szokások kialakítása csökkenti a stresszt és a halogatást.</p>
                            </div>
                        </div>
                        
                        <!-- 3. elem: Középre igazítva mobilon -->
                        <div class="flex gap-4 justify-center md:justify-start text-left">
                            <div class="flex-shrink-0 w-12 h-12 rounded-full bg-pink-100 flex items-center justify-center text-pink-600 font-bold">3</div>
                            <div>
                                <h4 class="font-bold text-lg">Innovatív arculat</h4>
                                <p class="text-sm text-gray-500">Mutassa meg, hogy egyeteme törődik a diákok digitális jólétével.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- How it works -->
    <section id="how-it-works" class="scroll-mt-28 py-20 bg-[#111] text-white">
        <div class="max-w-7xl mx-auto px-6">
            <div class="text-center mb-16">
                <span class="text-[#e07a86] font-bold tracking-widest uppercase text-sm">Egyszerű integráció</span>
                <h2 class="text-3xl md:text-4xl font-black mt-2">Hogyan vezethetik be?</h2>
            </div>

            <div class="grid md:grid-cols-3 gap-12 text-center">
                <div class="relative">
                    <div class="w-20 h-20 mx-auto bg-gradient-to-br from-[#3b1578] to-[#4b1f8f] rounded-full flex items-center justify-center text-2xl font-bold mb-6 border-4 border-[#1a1a1a] relative z-10">1</div>
                    <div class="absolute top-10 left-1/2 w-full h-1 bg-[#333] -z-0 hidden md:block"></div>
                    <h3 class="text-xl font-bold mb-2">Szerződéskötés</h3>
                    <!-- MÓDOSÍTOTT SZÖVEG -->
                    <p class="text-gray-400 text-sm">A hallgatói létszám alapján megállapítjuk a licencbérlés díját, meghatározzuk az időtartamát, majd integráljuk az egyetemi bejelentkezést (SSO).</p>
                </div>
                <div class="relative">
                    <div class="w-20 h-20 mx-auto bg-gradient-to-br from-[#3b1578] to-[#4b1f8f] rounded-full flex items-center justify-center text-2xl font-bold mb-6 border-4 border-[#1a1a1a] relative z-10">2</div>
                    <div class="absolute top-10 left-1/2 w-full h-1 bg-[#333] -z-0 hidden md:block"></div>
                    <h3 class="text-xl font-bold mb-2">Kuponok beállítása</h3>
                    <!-- MÓDOSÍTOTT SZÖVEG -->
                    <p class="text-gray-400 text-sm">Hosszú távú célunk országos márkák (pl. H&M, dm, Wolt) bevonása, a bevezetéskor azonban az Intézmény is szabadon meghatározhatja a saját, helyi kedvezményeit.</p>
                </div>
                <div class="relative">
                    <div class="w-20 h-20 mx-auto bg-gradient-to-br from-[#3b1578] to-[#4b1f8f] rounded-full flex items-center justify-center text-2xl font-bold mb-6 border-4 border-[#1a1a1a] relative z-10">3</div>
                    <h3 class="text-xl font-bold mb-2">Start</h3>
                    <p class="text-gray-400 text-sm">A diákok letöltik az appot az egyetemi belső linkről, és elkezdik a fókuszálást.</p>
                </div>
            </div>
        </div>
    </section>

    <!-- CTA / Contact - MODIFIED SECTION -->
    <section id="contact" class="scroll-mt-28 py-24 bg-gradient-to-br from-[#f8fafc] to-[#f1f5f9]">
        <div class="max-w-4xl mx-auto px-6 text-center">
            <h2 class="text-4xl font-black text-[#3b1578] mb-6">Vegye fel velünk a kapcsolatot!</h2>
            <p class="text-lg text-gray-600 mb-8">
                Kérdése van? Keressen minket bizalommal az alábbi e-mail címen:
            </p>

            <!-- Kiemelt Email Cím -->
            <div class="inline-flex items-center gap-3 bg-white px-8 py-4 rounded-2xl shadow-lg border border-gray-100 mb-16 group hover:border-[#3b1578]/30 transition-all">
                <div class="bg-[#3b1578]/10 p-2 rounded-full text-[#3b1578]">
                    <i data-lucide="mail" width="24" height="24"></i>
                </div>
                <a href="mailto:team.focusly@gmail.com" class="text-xl md:text-2xl font-bold text-[#3b1578] group-hover:underline">
                    team.focusly@gmail.com
                </a>
            </div>
            
            <div class="grid md:grid-cols-2 gap-8 text-left">
                
                <!-- 1. Kártya: Intézményeknek -->
                <div class="bg-white p-8 rounded-3xl shadow-xl border border-gray-100 hover:shadow-2xl transition-all duration-300 group">
                    <div class="w-12 h-12 bg-purple-100 text-[#3b1578] rounded-xl flex items-center justify-center mb-6 group-hover:bg-[#3b1578] group-hover:text-white transition-colors">
                        <i data-lucide="school" width="24" height="24"></i>
                    </div>
                    <h3 class="text-2xl font-bold text-[#3b1578] mb-4">Intézményi Integráció</h3>
                    <p class="text-gray-600 mb-6 text-sm">
                        Szeretné bevezetni a Focusly-t intézményében? Kérjük, küldjön egy e-mailt a fenti címre az alábbi adatokkal:
                    </p>
                    <ul class="space-y-3 mb-8">
                        <li class="flex items-start gap-3 text-gray-700">
                            <i data-lucide="check-circle" class="w-5 h-5 text-green-500 mt-0.5 flex-shrink-0"></i>
                            <span>Kapcsolattartó neve és beosztása</span>
                        </li>
                        <li class="flex items-start gap-3 text-gray-700">
                            <i data-lucide="check-circle" class="w-5 h-5 text-green-500 mt-0.5 flex-shrink-0"></i>
                            <span>Intézmény pontos megnevezése</span>
                        </li>
                        <li class="flex items-start gap-3 text-gray-700">
                            <i data-lucide="check-circle" class="w-5 h-5 text-green-500 mt-0.5 flex-shrink-0"></i>
                            <span>Érintett kar(ok) neve</span>
                        </li>
                        <li class="flex items-start gap-3 text-gray-700">
                            <i data-lucide="check-circle" class="w-5 h-5 text-green-500 mt-0.5 flex-shrink-0"></i>
                            <span>Becsült hallgatói létszám</span>
                        </li>
                    </ul>
                    <!-- GOMB TÖRÖLVE -->
                </div>

                <!-- 2. Kártya: Befektetőknek -->
                <div class="bg-white p-8 rounded-3xl shadow-xl border border-gray-100 hover:shadow-2xl transition-all duration-300 group">
                    <div class="w-12 h-12 bg-pink-100 text-[#e07a86] rounded-xl flex items-center justify-center mb-6 group-hover:bg-[#e07a86] group-hover:text-white transition-colors">
                        <i data-lucide="briefcase" width="24" height="24"></i>
                    </div>
                    <h3 class="text-2xl font-bold text-[#3b1578] mb-4">Befektetés & Támogatás</h3>
                    <p class="text-gray-600 mb-6 text-sm">
                        Lát fantáziát a projektben és támogatná a jövő generációjának sikerét? Várjuk jelentkezését az alábbi információkkal:
                    </p>
                    <ul class="space-y-3 mb-8">
                        <li class="flex items-start gap-3 text-gray-700">
                            <i data-lucide="check-circle" class="w-5 h-5 text-[#e07a86] mt-0.5 flex-shrink-0"></i>
                            <span>Név vagy Cég megnevezése</span>
                        </li>
                        <li class="flex items-start gap-3 text-gray-700">
                            <i data-lucide="check-circle" class="w-5 h-5 text-[#e07a86] mt-0.5 flex-shrink-0"></i>
                            <span>Támogatás típusa vagy mértéke</span>
                        </li>
                        <li class="flex items-start gap-3 text-gray-700">
                            <i data-lucide="check-circle" class="w-5 h-5 text-[#e07a86] mt-0.5 flex-shrink-0"></i>
                            <span>Közvetlen elérhetőség (Tel/Email)</span>
                        </li>
                        <li class="flex items-start gap-3 text-gray-700">
                            <i data-lucide="check-circle" class="w-5 h-5 text-[#e07a86] mt-0.5 flex-shrink-0"></i>
                            <span>Rövid bemutatkozás / célok</span>
                        </li>
                    </ul>
                    <!-- GOMB TÖRÖLVE -->
                </div>

            </div>
        </div>
    </section>

    <footer class="bg-white py-12 border-t border-gray-100">
        <div class="max-w-7xl mx-auto px-6 flex flex-col md:flex-row justify-between items-center gap-6">
            <div class="text-2xl font-black text-[#3b1578]">Focusly</div>
            <div class="text-gray-500 text-sm">
                © 2024 Focusly App. Minden jog fenntartva.
            </div>
            <div class="flex gap-6 text-gray-400">
                <a href="#" class="hover:text-[#3b1578]">Adatvédelem</a>
                <a href="#" class="hover:text-[#3b1578]">ÁSZF</a>
                <a href="#" class="hover:text-[#3b1578]">Impresszum</a>
            </div>
        </div>
    </footer>

    <script>
        // Biztosítjuk, hogy a DOM betöltődjön a szkript futtatása előtt
        document.addEventListener("DOMContentLoaded", function() {
            if (typeof lucide !== 'undefined') {
                lucide.createIcons();
            } else {
                console.warn("Lucide library could not be loaded.");
            }
        });

        function toggleTimer() {
            const btn = document.getElementById('stopButton');
            const label = document.getElementById('focusLabel');
            const ring = document.getElementById('progressRing');
            const iconContainer = document.getElementById('stopIconContainer');
            const text = document.getElementById('stopText');
            
            if (btn.classList.contains('stopped')) {
                btn.classList.remove('stopped');
                label.innerText = 'FOCUSING';
                label.style.color = 'rgba(255,255,255,0.6)';
                ring.style.animationPlayState = 'running';
                text.innerText = 'Stop';
                iconContainer.innerHTML = '<svg class="stop-icon-svg" viewBox="0 0 24 24"><rect x="5" y="5" width="14" height="14" rx="3" ry="3" /></svg>';
            } else {
                btn.classList.add('stopped');
                label.innerText = 'PAUSED';
                label.style.color = '#e07a86';
                ring.style.animationPlayState = 'paused';
                text.innerText = 'Resume';
                iconContainer.innerHTML = '<svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"><polygon points="5 3 19 12 5 21 5 3"></polygon></svg>';
            }
        }

        document.querySelectorAll('a[href^="#"]').forEach(anchor => {
            anchor.addEventListener('click', function (e) {
                e.preventDefault();
                const targetId = this.getAttribute('href');
                const targetElement = document.querySelector(targetId);
                
                if (targetElement) {
                    targetElement.scrollIntoView({
                        behavior: 'smooth',
                        block: 'start'
                    });
                }
            });
        });
    </script>
</body>
</html>
