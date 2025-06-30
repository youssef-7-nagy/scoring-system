# scoring-system
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Team Scoring System</title>
  <link rel="stylesheet" href="scoroo.css" />

  <!-- Firebase SDKs -->
  <script src="https://www.gstatic.com/firebasejs/9.0.0/firebase-app.js"></script>
  <script src="https://www.gstatic.com/firebasejs/9.0.0/firebase-database.js"></script>
</head>
<body>

  <header>
    <h1> Scoring System</h1>
  </header>

  <div class="container">
    <div class="team-card">
      <img src="photos/condor.jpg" alt="Team 1">
      <div class="team-content">
        <h3>Condor</h3>
        <input type="number" id="score1" value="0" min="0"readonly>
      </div>
    </div>

    <div class="team-card">
      <img src="photos/coq.jpg" alt="Team 2">
      <div class="team-content">
        <h3>Coq</h3>
        <input type="number" id="score2" value="0" min="0" readonly>
      </div>
    </div>

    <div class="team-card">
      <img src="photos/epervier.jpg" alt="Team 3">
      <div class="team-content">
        <h3>Epervier</h3>
        <input type="number" id="score3" value="129" min="0"readonly>
      </div>
    </div>

    <div class="team-card">
      <img src="photos/aigle.jpg" alt="Team 4">
      <div class="team-content">
        <h3>Aigle</h3>
        <input type="number" id="score4" value="0" min="0"readonly>
      </div>
    </div>
  </div>

  <button class="button" onclick="calculateScores()">Calculate Scores</button>

  <div class="result" id="result" style="display: none;">
    <h2>Team Ranking</h2>
    <ul id="ranking" style="list-style: none; padding: 0;"></ul>
  </div>


  <script>
  function calculateScores() {
    // Read scores from input fields
    const teams = [
      { name: 'Condor', score: parseInt(document.getElementById('score1').value) },
      { name: 'Coq', score: parseInt(document.getElementById('score2').value) },
      { name: 'Epervier', score: parseInt(document.getElementById('score3').value) },
      { name: 'Aigle', score: parseInt(document.getElementById('score4').value) }
    ];

    // Sort teams by score in descending order
    teams.sort((a, b) => b.score - a.score);

    // Get the ranking list container
    const rankingList = document.getElementById('ranking');
    rankingList.innerHTML = ''; // Clear any previous results

    // Create and append list items
    teams.forEach((team, index) => {
      const listItem = document.createElement('li');
      listItem.innerHTML = `<strong>${index + 1}.</strong> ${team.name} - ${team.score} points`;
      rankingList.appendChild(listItem);
    });

    // Show result box
    document.getElementById('result').style.display = 'block';
  }
</script>


  

</body>
</html>
