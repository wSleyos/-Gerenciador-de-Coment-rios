<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GERENCIADOR DE COMENTÁRIOS</title>
    <link rel="stylesheet" href="../Comentarios/css/c.css" />

</head>
<body>

    <div class="container">
        <h1>Comentários</h1>

        <div class="input-area">
            <input type="text" id="comentarioInput" placeholder="Digite seu comentário aqui..." />
            <button id="btnAdicionar">Adicionar Comentário</button>
        </div>

        <div id="listaComentarios"></div>
    </div>
    <script>
      
const inputComentario = document.getElementById("comentarioInput");
const btnAdicionar = document.getElementById("btnAdicionar");
const listaComentarios = document.getElementById("listaComentarios");

function criarComentario(texto) {
    // Cria container do comentário
    const divComment = document.createElement("div");
    divComment.classList.add("comment");

    
    const p = document.createElement("p");
    p.classList.add("comment-text");
    p.textContent = texto;

    
    const divBotoes = document.createElement("div");
    divBotoes.classList.add("comment-buttons");


    const btnEditar = document.createElement("button");
    btnEditar.textContent = "Editar";
    btnEditar.onclick = () => {
        const novoTexto = prompt("Edite o comentário:", p.textContent);
        if (novoTexto !== null && novoTexto.trim() !== "") {
            p.textContent = novoTexto.trim();
        }
    };


    const btnRemover = document.createElement("button");
    btnRemover.textContent = "Remover";
    btnRemover.onclick = () => {
        listaComentarios.removeChild(divComment);
    };

    divBotoes.appendChild(btnEditar);
    divBotoes.appendChild(btnRemover);

    divComment.appendChild(p);
    divComment.appendChild(divBotoes);

    return divComment;
}

btnAdicionar.addEventListener("click", () => {
    const texto = inputComentario.value.trim();
    if (texto === "") {
        alert("Por favor, digite um comentário antes de adicionar.");
        return;
    }

    const novoComentario = criarComentario(texto);
    listaComentarios.appendChild(novoComentario);

    inputComentario.value = "";
    inputComentario.focus();
});

    </script>

</body>
</html>
