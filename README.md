# LOCAL-HER-CONNECT
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>LocalHer Connect</title>
  <style>
    body { font-family: Arial; margin: 20px; background: #f5f5f5; }
    h1 { color: #e91e63; }
    .worker-card { background: white; padding: 15px; margin: 10px 0; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.2); }
    .worker-card h3 { margin: 0; }
    .worker-card button { background: #e91e63; color: white; border: none; padding: 8px 12px; border-radius: 5px; cursor: pointer; }
    .worker-card button:hover { background: #d81b60; }
    input, select { padding: 5px; margin: 5px 0; width: 100%; }
    #add-worker { margin-top: 20px; background: #fff; padding: 15px; border-radius: 8px; box-shadow: 0 2px 5px rgba(0,0,0,0.2);}
  </style>
</head>
<body>

<h1>LocalHer Connect</h1>

<input type="text" id="searchSkill" placeholder="Search by skill..." onkeyup="filterWorkers()">

<div id="workersList"></div>

<div id="add-worker">
  <h2>Add Worker</h2>
  <input type="text" id="name" placeholder="Name">
  <input type="text" id="skill" placeholder="Skill">
  <input type="text" id="location" placeholder="Location">
  <input type="text" id="phone" placeholder="Phone">
  <input type="text" id="experience" placeholder="Experience">
  <button onclick="addWorker()">Add Worker</button>
</div>

<script>
let workers = [
  {name: "Priya", skill: "Tailor", location: "Chennai", phone: "9876543210", experience: "2 years"},
  {name: "Meena", skill: "Mehendi", location: "Chennai", phone: "9123456780", experience: "3 years"}
];

function displayWorkers(list = workers) {
  const container = document.getElementById('workersList');
  container.innerHTML = "";
  list.forEach(w => {
    const card = document.createElement('div');
    card.className = 'worker-card';
    card.innerHTML = `
      <h3>${w.name}</h3>
      <p><b>Skill:</b> ${w.skill}</p>
      <p><b>Location:</b> ${w.location}</p>
      <p><b>Experience:</b> ${w.experience}</p>
      <p><b>Phone:</b> <a href="tel:${w.phone}">${w.phone}</a></p>
    `;
    container.appendChild(card);
  });
}

function addWorker() {
  const name = document.getElementById('name').value;
  const skill = document.getElementById('skill').value;
  const location = document.getElementById('location').value;
  const phone = document.getElementById('phone').value;
  const experience = document.getElementById('experience').value;
  
  if(name && skill && location && phone && experience) {
    workers.push({name, skill, location, phone, experience});
    displayWorkers();
    document.getElementById('name').value = '';
    document.getElementById('skill').value = '';
    document.getElementById('location').value = '';
    document.getElementById('phone').value = '';
    document.getElementById('experience').value = '';
  } else {
    alert("Please fill all fields!");
  }
}

function filterWorkers() {
  const term = document.getElementById('searchSkill').value.toLowerCase();
  const filtered = workers.filter(w => w.skill.toLowerCase().includes(term));
  displayWorkers(filtered);
}

// Initial display
displayWorkers();
</script>

</body>
</html>
