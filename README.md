<!DOCTYPE html>
<html lang="pt-br">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Relógio Neon</title>
<style>
    body {
      margin: 0;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      background: linear-gradient(135deg, #0f0c29, #302b63, #24243e);
      font-family: 'Arial', sans-serif;
    }
      .relogio {
      text-align: center;
      padding: 30px 50px;
      border-radius: 20px;
      background: rgba(255, 255, 255, 0.15);
      backdrop-filter: blur(12px);
      border: 2px solid rgba(255, 255, 255, 0.3);
      box-shadow: 
        0 0 15px #00fff7,
        0 0 30px #00fff7;
      animation: neon 2s infinite alternate;
    }
    @keyframes neon {
      from {
        box-shadow: 0 0 10px #00fff7;
      }
      to {
        box-shadow: 0 0 30px #00fff7, 0 0 60px #00fff7;
      }
    }
    #hora {
      font-size: 56px;
      color: #ffffff;
      text-shadow: 0 0 10px #00fff7;
    }
    #data {
      font-size: 20px;
      color: #ffffff;
      margin-top: 8px;
    }
    #mensagem {
      font-size: 24px;
      margin-top: 12px;
      color: #00fff7;
    }
  </style>
</head>

<body>

  <div class="relogio">
    <div id="hora"></div>
    <div id="data"></div>
    <div id="mensagem"></div>
  </div>

  <script>
    function atualizarRelogio() {
      const agora = new Date();

      const horas = agora.getHours().toString().padStart(2, '0');
      const minutos = agora.getMinutes().toString().padStart(2, '0');
      const segundos = agora.getSeconds().toString().padStart(2, '0');

      document.getElementById("hora").innerHTML =
        `${horas}:${minutos}:${segundos}`;

      const dias = ["Domingo","Segunda","Terça","Quarta","Quinta","Sexta","Sábado"];
      const meses = ["Janeiro","Fevereiro","Março","Abril","Maio","Junho","Julho",
                      "Agosto","Setembro","Outubro","Novembro","Dezembro"];

      const dataFormatada =
        `${dias[agora.getDay()]}, ${agora.getDate()} de ${meses[agora.getMonth()]} de ${agora.getFullYear()}`;

      document.getElementById("data").innerHTML = dataFormatada;
      document.getElementById("mensagem").innerHTML = getMensagem(agora.getHours());
    }

    function getMensagem(hora) {
  if (hora >= 5 && hora < 12) {
    return "☀️ Bom dia!";
  } 
  else if (hora >= 12 && hora < 18) {
    return "🌤 Boa tarde!";
  } 
  else if (hora >= 18 && hora < 23) {
    return "🌙 Boa noite!";
  } 
  else {
    return "🌌 Boa madrugada!";
  }

}
    setInterval(atualizarRelogio, 1000);
    atualizarRelogio();
  </script>

</body>
</html>
