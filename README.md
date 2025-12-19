                                          <!DOCTYPE html>
                                                <html lang="en">
                                                <head>
                                                        <meta charset="UTF-8">
                                                        <meta name="viewport" content="width=device-width, initial-scale=1.0">
                            <style>
                                body {
                                    background-color: white; /* Ensure the iframe has a white background */
                                }

                                * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

body {
    background-color: #f8fafc;
    color: #1e293b;
}

/* Header */
header {
    background-color: #0f172a; /* gelap, elegan */
    padding: 0.8rem 0;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 10px rgba(0,0,0,0.1);
}

.header-container {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 0 1.5rem;
}

/* Logo */
.logo {
    font-size: 1.5rem;
    font-weight: 700;
    color: white;
    display: flex;
    align-items: center;
    gap: 8px;
}

.logo span {
    color: #38bdf8; /* biru cerah */
}

/* Navigasi */
.nav-menu {
    display: flex;
    gap: 1.2rem;
}

.nav-menu a {
    color: #cbd5e1;
    text-decoration: none;
    font-weight: 600;
    padding: 0.4rem 0.6rem;
    border-radius: 6px;
    transition: all 0.2s;
}

.nav-menu a:hover,
.nav-menu a.active {
    color: white;
    background-color: #334155;
}

/* Konten Utama */
main {
    max-width: 1000px;
    margin: 2rem auto;
    padding: 0 1.5rem;
}

.live-header {
    margin-bottom: 1.5rem;
}

.live-header h2 {
    color: #dc2626;
    margin-bottom: 0.4rem;
}

.live-header p {
    color: #64748b;
    font-size: 0.95rem;
}

/* Kartu Pertandingan */
.match-card {
    background: white;
    border-radius: 12px;
    box-shadow: 0 3px 10px rgba(0,0,0,0.08);
    padding: 1.2rem;
    margin-bottom: 1.2rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    transition: transform 0.2s;
}

.match-card:hover {
    transform: translateY(-2px);
}

.match-card.live {
    border-left: 5px solid #ef4444;
}

.team {
    font-weight: 700;
    font-size: 1.2rem;
    color: #1e293b;
}

.score {
    font-size: 1.6rem;
    font-weight: 700;
    color: #0f172a;
    min-width: 80px;
    text-align: center;
}

/* Footer */
footer {
    text-align: center;
    padding: 1.5rem;
    color: #94a3b8;
    font-size: 0.9rem;
    background-color: #0f172a;
    color: #cbd5e1;
    margin-top: 3rem;
}

/* Responsif */
@media (max-width: 768px) {
    .header-container {
        flex-direction: column;
        gap: 1rem;
    }

    .nav-menu {
        flex-wrap: wrap;
        justify-content: center;
    }

    .match-card {
        flex-direction: column;
        gap: 0.8rem;
        text-align: center;
    }

    .score {
        font-size: 1.8rem;
    }
}


                            </style>
                                                </head>
                                                <body>
                                                        <!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <title>Skor Olahraga Live</title>
    <link rel="stylesheet" href="style.css" />
    <!-- Google Fonts (opsional tapi bagus untuk tampilan) -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">
</head>
<body>
    <!-- Header dengan Logo & Navigasi -->
    <header>
        <div class="header-container">
            <!-- Logo -->
            <div class="logo">
                ⚽ <span>ScoreMatch</span>
            </div>

            <!-- Navigasi Menu -->
            <nav class="nav-menu">
                <a href="#" class="active">Home</a>
                <a href="#">Sepak Bola</a>
                <a href="#">Bola Basket</a>
                <a href="#">Baseball</a>
                <a href="#">Tenis</a>
                <a href="#">Lainnya</a>
            </nav>
        </div>
    </header>

    <!-- Konten Utama -->
    <main>
        <div class="live-header">
            <h2>🔴 Pertandingan Sedang Berlangsung</h2>
            <p>Perbarui otomatis setiap 30 detik</p>
        </div>

        <div id="live-matches">
            <!-- Data skor akan dimuat di sini -->
        </div>
    </main>

    <!-- Footer -->
    <footer>
        <p>&copy; 2025 SkorOlahragaLive. Data simulasi untuk demo.</p>
    </footer>

    <script src="script.js"></script>
</body>
</html>



                            <script>
                                                            // Data simulasi pertandingan live
const mockLiveMatches = [
    { home: "Manchester United", away: "Liverpool", homeScore: 2, awayScore: 1, live: true },
    { home: "Real Madrid", away: "Barcelona", homeScore: 0, awayScore: 2, live: true },
    { home: "Lakers", away: "Warriors", homeScore: 89, awayScore: 92, live: true },
    { home: "Yankees", away: "Red Sox", homeScore: 5, awayScore: 3, live: true },
    { home: "Djokovic", away: "Alcaraz", homeScore: 1, awayScore: 1, live: true, sport: "tenis" },
];

function renderMatches() {
    const container = document.getElementById("live-matches");
    container.innerHTML = "";

    if (mockLiveMatches.length === 0) {
        container.innerHTML = "<p>🎯 Tidak ada pertandingan live saat ini.</p>";
        return;
    }

    mockLiveMatches.forEach(match => {
        const card = document.createElement("div");
        card.className = `match-card ${match.live ? 'live' : ''}`;
        card.innerHTML = `
            <span class="team">${match.home}</span>
            <span class="score">${match.homeScore} – ${match.awayScore}</span>
            <span class="team">${match.away}</span>
        `;
        container.appendChild(card);
    });
}

// Jalankan saat halaman dimuat
document.addEventListener("DOMContentLoaded", renderMatches);

// Simulasi pembaruan setiap 30 detik
setInterval(renderMatches, 30000);


                            </script>
                                                </body>
                                                </html>
