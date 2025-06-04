<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Calculadora de Partidas Rankeadas</title>
</head>
<body>
  <h1>Calculadora de Partidas Rankeadas</h1>
  <button onclick="iniciarCalculadora()">Iniciar</button>

  <script>
    function calcularRank(vitorias, derrotas) {
      let saldo = vitorias - derrotas;
      let nivel = "";

      if (vitorias < 10) {
        nivel = "Ferro";
      } else if (vitorias >= 11 && vitorias <= 20) {
        nivel = "Bronze";
      } else if (vitorias >= 21 && vitorias <= 50) {
        nivel = "Prata";
      } else if (vitorias >= 51 && vitorias <= 80) {
        nivel = "Ouro";
      } else if (vitorias >= 81 && vitorias <= 90) {
        nivel = "Diamante";
      } else if (vitorias >= 91 && vitorias <= 100) {
        nivel = "Lendário";
      } else {
        nivel = "Imortal";
      }

      return { saldo, nivel };
    }

    function iniciarCalculadora() {
      let continuar = true;

      while (continuar) {
        let vitorias = parseInt(prompt("Digite a quantidade de vitórias:"));
        let derrotas = parseInt(prompt("Digite a quantidade de derrotas:"));

        if (isNaN(vitorias) || isNaN(derrotas)) {
          alert("Por favor, insira apenas números válidos.");
          continue;
        }

        const resultado = calcularRank(vitorias, derrotas);
        alert(`O jogador tem um saldo de ${resultado.saldo} vitórias e está no nível: ${resultado.nivel}`);

        let resposta = prompt("Deseja calcular novamente? (s/n):").toLowerCase();
        if (resposta !== 's') {
          continuar = false;
        }
      }
    }
  </script>
</body>
</html>
