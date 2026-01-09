<!DOCTYPE html>
<html lang="de">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MALIK ARSLAN // NEXUS PROTOCOL</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Rajdhani:wght@300;500;700&family=JetBrains+Mono:wght@300;500&display=swap');

        :root {
            --neon-gold: #d4af37;
            --deep-gold: #9c7b10;
            --bg-ultra: #020203;
            --panel-glass: rgba(15, 17, 26, 0.85);
            --accent-red: #ff0033;
            --text-cyan: #e2e8f0;
            --scanline-color: rgba(255, 255, 255, 0.03);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            cursor: crosshair;
        }

        body {
            background-color: var(--bg-ultra);
            color: var(--text-cyan);
            font-family: 'Rajdhani', sans-serif;
            overflow-x: hidden;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        /* Hintergrund-System-Rauschen */
        body::before {
            content: " ";
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(var(--scanline-color) 50%, transparent 50%);
            background-size: 100% 4px;
            z-index: 1000;
            pointer-events: none;
            opacity: 0.3;
        }

        .nexus-wrapper {
            width: 100%;
            max-width: 1200px;
            background: var(--panel-glass);
            backdrop-filter: blur(15px);
            border: 1px solid rgba(212, 175, 55, 0.2);
            box-shadow: 0 0 80px rgba(0, 0, 0, 0.9), inset 0 0 20px rgba(212, 175, 55, 0.05);
            position: relative;
            overflow: hidden;
            display: grid;
            grid-template-rows: auto 1fr auto;
        }

        /* Top Header Navigation HUD */
        .hud-header {
            padding: 20px 40px;
            background: rgba(0, 0, 0, 0.6);
            border-bottom: 2px solid var(--neon-gold);
            display: flex;
            justify-content: space-between;
            align-items: center;
            font-family: 'JetBrains Mono', monospace;
            letter-spacing: 2px;
        }

        .connection-status {
            color: #00ffaa;
            font-size: 0.75rem;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .connection-status span {
            width: 8px;
            height: 8px;
            background: #00ffaa;
            border-radius: 50%;
            box-shadow: 0 0 10px #00ffaa;
            animation: pulse 1.5s infinite;
        }

        @keyframes pulse {
            0% {
                opacity: 0.4;
            }

            50% {
                opacity: 1;
            }

            100% {
                opacity: 0.4;
            }
        }

        .system-clock {
            color: var(--neon-gold);
            font-weight: 700;
            font-size: 1rem;
        }

        /* Main Branding Area */
        .branding-core {
            padding: 40px;
            border-bottom: 1px solid rgba(255, 255, 255, 0.05);
            text-align: center;
        }

        h1 {
            font-family: 'Orbitron', sans-serif;
            font-size: clamp(2rem, 8vw, 5.5rem);
            letter-spacing: 15px;
            text-transform: uppercase;
            background: linear-gradient(to bottom, #fff, var(--neon-gold));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: drop-shadow(0 0 15px rgba(212, 175, 55, 0.3));
        }

        .main-layout {
            display: grid;
            grid-template-columns: 400px 1fr;
            gap: 40px;
            padding: 40px;
        }

        /* Image Architectures */
        .visual-core {
            display: flex;
            flex-direction: column;
            gap: 25px;
        }

        .img-container {
            position: relative;
            border: 1px solid rgba(212, 175, 55, 0.3);
            background: #000;
            overflow: hidden;
            padding: 10px;
        }

        .img-container::before {
            content: "SEC_ARCHIVE";
            position: absolute;
            top: 5px;
            left: 10px;
            font-size: 0.6rem;
            color: var(--neon-gold);
            z-index: 10;
        }

        .img-container img {
            width: 100%;
            height: auto;
            display: block;
            filter: grayscale(100%) brightness(0.8) contrast(1.2);
            transition: 0.5s ease;
        }

        .img-container:hover img {
            filter: grayscale(0%) brightness(1);
            transform: scale(1.03);
        }

        /* Intelligence Content */
        .intel-blocks {
            display: flex;
            flex-direction: column;
            gap: 40px;
        }

        .card {
            background: rgba(255, 255, 255, 0.02);
            border-right: 2px solid transparent;
            border-bottom: 2px solid transparent;
            padding: 30px;
            position: relative;
            transition: 0.3s;
        }

        .card:hover {
            background: rgba(255, 255, 255, 0.04);
            border-right-color: var(--neon-gold);
        }

        .card-tag {
            font-family: 'JetBrains Mono', monospace;
            font-size: 0.7rem;
            color: var(--neon-gold);
            margin-bottom: 15px;
            display: block;
        }

        h3 {
            font-family: 'Orbitron', sans-serif;
            font-size: 1.4rem;
            margin-bottom: 20px;
            color: #fff;
            letter-spacing: 2px;
        }

        .description {
            line-height: 1.8;
            font-weight: 300;
            color: var(--text-cyan);
            font-size: 1.1rem;
        }

        /* FIX: Operative Realität Master-Level Styling */
        .high-value-intel {
            margin-top: 25px;
            padding: 20px;
            background: rgba(212, 175, 55, 0.08);
            border: 1px solid var(--neon-gold);
            position: relative;
            color: #fff !important;
        }

        .high-value-intel::before {
            content: "CRITICAL DATA";
            position: absolute;
            top: -10px;
            right: 20px;
            background: var(--neon-gold);
            color: #000;
            padding: 2px 8px;
            font-size: 0.6rem;
            font-weight: 700;
        }

        /* Stats Grid */
        .stats-hud {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-top: 20px;
        }

        .stat-item {
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 15px;
            text-align: center;
        }

        .stat-label {
            font-size: 0.6rem;
            color: var(--neon-gold);
            text-transform: uppercase;
        }

        .stat-val {
            font-size: 1.2rem;
            display: block;
            font-weight: 700;
            font-family: 'JetBrains Mono', monospace;
        }

        /* Quote Section */
        .boss-quote {
            grid-column: 1 / -1;
            margin-top: 40px;
            padding: 40px;
            background: linear-gradient(90deg, transparent, rgba(212, 175, 55, 0.05), transparent);
            border-top: 1px solid rgba(212, 175, 55, 0.2);
            border-bottom: 1px solid rgba(212, 175, 55, 0.2);
            text-align: center;
        }

        .boss-quote p {
            font-size: 1.4rem;
            font-style: italic;
            font-family: 'JetBrains Mono', monospace;
            color: #fff;
        }

        .boss-quote span {
            display: block;
            margin-top: 20px;
            color: var(--neon-gold);
            font-size: 0.8rem;
            letter-spacing: 5px;
        }

        /* Footer HUD */
        .hud-footer {
            padding: 15px 40px;
            background: #000;
            display: flex;
            justify-content: space-between;
            font-size: 0.7rem;
            color: var(--deep-gold);
            font-family: 'JetBrains Mono', monospace;
        }

        @media (max-width: 1000px) {
            .main-layout {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>

<body>

    <div class="nexus-wrapper">
        <header class="hud-header">
            <div class="connection-status">
                <span></span> ENCRYPTED_NEXUS_LINK_ACTIVE
            </div>
            <div class="system-clock" id="clock">00:00:00:000</div>
        </header>

        <div class="branding-core">
            <span
                style="color: var(--neon-gold); font-family: 'JetBrains Mono'; font-size: 0.8rem; letter-spacing: 5px;">[
                SUBJECT PROFILE ]</span>
            <h1>MALIK ARSLAN</h1>
        </div>

        <main class="main-layout">
            <section class="visual-core">
                <div class="img-container">
                    <img src="portrait.jpg" alt="Portrait Alpha"
                        onerror="this.src='https://via.placeholder.com/400x500/111/d4af37?text=NO_SIGNAL';">
                </div>
                <div class="img-container">
                    <img src="body.jpg" alt="Body Beta"
                        onerror="this.src='https://via.placeholder.com/400x600/111/d4af37?text=NO_SIGNAL';">
                </div>

                <div class="stats-hud">
                    <div class="stat-item"><span class="stat-label">Code</span><span class="stat-val">GHOST</span></div>
                    <div class="stat-item"><span class="stat-label">Age</span><span class="stat-val">20</span></div>
                    <div class="stat-item"><span class="stat-label">Height</span><span class="stat-val">1.86m</span>
                    </div>
                    <div class="stat-item"><span class="stat-label">Sector</span><span class="stat-val">BER_04</span>
                    </div>
                </div>
            </section>

            <section class="intel-blocks">
                <div class="card">
                    <span class="card-tag">LOG_01 // COVERT_OPERATIONS</span>
                    <h3>PROFIL & TARNUNG</h3>
                    <div class="description">
                        Malik Arslan operiert als unscheinbarer Sicherheitsmitarbeiter im Objektschutz auf
                        Mindestlohn-Basis. Sein Erscheinungsbild ist eine sorgfältig kalibrierte Rauschunterdrückung –
                        desinteressiert, funktional, unsichtbar.

                        <div class="high-value-intel">
                            <strong>OPERATIVE REALITÄT:</strong> Hinter dieser systematischen Fassade steuert das
                            Subjekt ein Logistik-Netzwerk für BTM im kumulierten Wert von 1,2 Mio. €. Die Uniform ist
                            kein Dienstkleid, sondern eine operative Rüstung, die unbegrenzten Zugang zu kritischen
                            Infrastrukturen gewährt.
                        </div>
                    </div>
                </div>

                <div class="card">
                    <span class="card-tag">LOG_02 // SYSTEM_MERKMALE</span>
                    <h3>AUSRÜSTUNG & SIGNATUR</h3>
                    <div class="description">
                        Dunkle Bomberjacken und Security-Parkas dienen der künstlichen Vergrößerung der physischen
                        Silhouette. Gesichtszüge bleiben durch ein tief sitzendes Cappy in den Schattenbereichen der
                        Überwachungssysteme.
                        <br><br>
                        <strong>SIGNATUR:</strong> Eine massive Goldkette unter der billigen Arbeitskleidung fungiert
                        als einziges Relikt seines wahren Status – ein Symbol, das nur in Momenten totaler Dominanz
                        exponiert wird.
                    </div>
                </div>
            </section>

            <div class="boss-quote">
                <p>"Sie sehen die Uniform und denken, ich diene ihnen. Aber während ich die Tür aufhalte, kaufe ich das
                    Gebäude. Ich bin der Wächter meines eigenen Imperiums."</p>
                <span>[ AUDIO_ENCRYPTED_224_MA ]</span>
            </div>
        </main>

        <footer class="hud-footer">
            <span>MASTER_ID: NEXUS-94-B</span>
            <span>SYSTEM_OVERRIDE_ACTIVE</span>
            <span>AKTE_PENDING_AUTO_REDACT</span>
        </footer>
    </div>

    <script>
        // Temporal-Synchronisation Engine
        function updateClock() {
            const now = new Date();
            const h = String(now.getHours()).padStart(2, '0');
            const m = String(now.getMinutes()).padStart(2, '0');
            const s = String(now.getSeconds()).padStart(2, '0');
            const ms = String(now.getMilliseconds()).padStart(3, '0');

            document.getElementById('clock').textContent = `${h}:${m}:${s}:${ms}`;
        }

        setInterval(updateClock, 1);
        updateClock();
    </script>
</body>

</html>
