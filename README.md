# APPS-de-apostas
o intuito era criar um prototipo que ajuda a resolver um problema ou dor, e com um aspecto inovado 

<main>
  <section id="cliente" class="card cliente">
    <h2>Perfil do Cliente</h2>
    <div class="profile">
      <div class="row"><div><strong id="clientName">—</strong><div class="muted">Nome</div></div><div><button id="editProfile" class="ghost">Editar</button></div></div>
      <div class="row"><div><span id="clientCPF">***.***.***-**</span><div class="muted">CPF (privado)</div></div></div>
      <div class="row"><div><strong>Saldo: R$ <span id="clientSaldo">0.00</span></strong><div class="muted">Disponível</div></div>
      <div>
        <button id="recarregar">Recarregar</button>
      </div></div>
      <div class="actions">
        <button id="novaAposta">Nova Aposta</button>
        <button id="verHistorico" class="ghost">Ver Histórico</button>
      </div>
    </div>
  </section>

  <aside>
    <div class="card transactions">
      <h3>Histórico Consolidado</h3>
      <div class="muted small">Inclui Jogos da Sorte e Pagamentos</div>
      <div style="margin-top:10px;">
        <table id="txTable"><thead><tr><th>Data</th><th>Tipo</th><th>Detalhes</th><th>Valor</th></tr></thead><tbody></tbody></table>
      </div>
    </div>

    <div class="card" style="margin-top:12px;">
      <h3>Atalhos</h3>
      <div style="display:flex;flex-direction:column;gap:8px;margin-top:8px;">
        <button id="toJogos" class="ghost">Ir para Jogos</button>
        <button id="toPagamentos" class="ghost">Ir para Pagamentos</button>
      </div>
    </div>
  </aside>

  <section id="jogos" class="card" style="display:none;">
    <h2>Jogos da Sorte</h2>
    <div class="muted small">Adicione apostas e valide resultados. Sistema suporta: Mega-Sena, Quina, Lotofácil, Lotomania.</div>

    <div style="margin-top:12px;" id="apostaForm">
      <label>Tipo de Jogo</label>
      <select id="tipoJogo"><option value="megasena">Mega-Sena</option><option value="quina">Quina</option><option value="lotofacil">Lotofácil</option><option value="lotomania">Lotomania</option></select>
      <div style="margin-top:8px;" id="numerosWrap">
        <label>Números (separados por vírgula)</label>
        <input type="text" id="numeros" placeholder="ex: 05,12,23,34,45,56" />
      </div>
      <div class="grid-2" style="margin-top:8px;">
        <div>
          <label>Valor da Aposta (R$)</label>
          <input type="number" id="valorAposta" min="0" step="0.01" value="2.00" />
        </div>
        <div>
          <label>Data da Aposta</label>
          <input type="date" id="dataAposta" />
        </div>
      </div>
      <div class="actions"><button id="salvarAposta">Salvar Aposta</button><button id="limparAposta" class="ghost">Limpar</button></div>
    </div>

    <hr style="margin:14px 0;" />
    <div>
      <h3>Configurar Resultado Oficial</h3>
      <div class="muted small">Escolha o tipo de jogo e insira os números sorteados — o sistema atualizará automaticamente apostas e valores de prêmio.</div>
      <div style="margin-top:8px;">
        <select id="resTipo"><option value="megasena">Mega-Sena</option><option value="quina">Quina</option><option value="lotofacil">Lotofácil</option><option value="lotomania">Lotomania</option></select>
        <label style="margin-top:8px;">Números sorteados</label>
        <input type="text" id="resNumeros" placeholder="ex: 05,12,23,34,45,56" />
        <div class="actions" style="margin-top:10px;"><button id="confirmResultado">Confirmar Resultado</button></div>
      </div>
    </div>

    <hr style="margin:14px 0;" />
    <div>
      <h3>Apostas Recentes</h3>
      <div id="apostasList" class="admin-list" style="margin-top:8px;"></div>
    </div>
  </section>

  <section id="pagamentos" class="card" style="display:none;">
    <h2>Pagamentos & Investimentos</h2>
    <div class="muted small">Gerencie pagamentos, formas de pagamento e invista saldo do cliente.</div>
    <div style="margin-top:8px;">
      <label>Forma de Pagamento</label>
      <select id="formaPagamento"><option>PIX</option><option>Cartão</option><option>Boleto</option><option>Transferência</option></select>
      <label style="margin-top:8px">Valor (R$)</label>
      <input type="number" id="valorPagamento" min="0" step="0.01" />
      <div class="actions" style="margin-top:8px;"><button id="registrarPagamento">Registrar Pagamento</button></div>
    </div>

    <hr style="margin:12px 0" />
    <div>
      <h3>Investir Saldo</h3>
      <label>Opções</label>
      <select id="investOption"><option value="poupanca">Poupança (simulação)</option><option value="tesouro">Tesouro Direto (simulação)</option><option value="fundos">Fundos (simulação)</option></select>
      <label style="margin-top:8px">Valor a Investir</label>
      <input type="number" id="valorInvest" min="0" step="0.01" />
      <div class="small muted">Ao investir via app, o cliente recebe desconto de taxa em apostas (simulado).</div>
      <div class="actions" style="margin-top:8px;"><button id="investirSaldo">Investir</button></div>
    </div>

    <hr style="margin:12px 0" />
    <div>
      <h3>Histórico de Pagamentos</h3>
      <div id="pagosList" style="margin-top:8px;"></div>
    </div>
  </section>

  <section id="admin" class="card" style="display:none;">
    <h2>Painel do Administrador</h2>
    <div class="muted small">Visualize e gerencie apostas, resultados e pagamentos.</div>
    <div style="margin-top:12px;">
      <h4>Apostas</h4>
      <div id="adminApostas" class="admin-list"></div>
    </div>
    <div style="margin-top:12px;">
      <h4>Formulário Rápido — Inserir Resultado</h4>
      <label>Tipo</label>
      <select id="adminResTipo"><option value="megasena">Mega-Sena</option><option value="quina">Quina</option><option value="lotofacil">Lotofácil</option><option value="lotomania">Lotomania</option></select>
      <label style="margin-top:8px">Números</label>
      <input type="text" id="adminResNums" placeholder="05,12,23,34,45,56" />
      <div class="actions" style="margin-top:8px;"><button id="adminSetResultado">Aplicar Resultado</button></div>
    </div>
  </section>

</main>

<footer>Lotérica Caixas — protótipo. Dados salvos localmente (localStorage) para demonstração.</footer>
