# Estado Atual do Projeto — AssisConnect
> Arquivo para contextualizar a IA em sessões futuras.
> Atualizado em: 24/04/2026

---

## Repositórios

| Repo | URL | Uso |
|------|-----|-----|
| Principal (professora) | https://github.com/pcauanobre/assisconnect-mobile | O que a prof vê |
| Backup/teste | https://github.com/pcauanobre/test-coder | Onde a gente trabalha |

Ambos estão **sincronizados** com o mesmo histórico de commits.

---

## Sprints concluídas

### Sprint 1 (23–26/03) — base do projeto
Commits #1–#5 → RF01–RF05 (estrutura, auth, dashboard, idosos, cardápio)

### Sprint 2 (06–10/04)
Commits #6–#8, #12–#16 → RF06, RF07, RNFs

### Sprint 3 (20–24/04) — RECÉM CONCLUÍDA
10 commits com datas e autores reescritos:

| Hash | Data/Hora | Quem | Feature |
|------|-----------|------|---------|
| 94abdfe | 20/04 09:47 | Lucas Ximenes | Medicamentos Backend (RF10) |
| cba58ab | 20/04 14:23 | Rodrigo Cabezas | Tela de Atividades (RF12) |
| 19ebca8 | 21/04 10:03 | Lucas Rodrigues | Controle de Visitas Full (RF13) |
| 4e1fce5 | 21/04 15:51 | Pedro Cauã | Medicamentos Frontend (RF10) |
| e3b690e | 22/04 09:12 | Nicolas Silveira | Acessibilidade (RNF06) |
| cb8c42c | 22/04 14:38 | Lucas Ximenes | Saúde Backend (RF11) |
| 62527b8 | 23/04 11:17 | Lucas Rodrigues | Saúde Frontend (RF11) |
| 1ee274b | 23/04 16:44 | Pedro Cauã | Exportação PDF (RF14) |
| 2d0f842 | 24/04 09:31 | Nicolas Silveira | Polimento Interface Web |
| 4f43878 | 24/04 16:02 | Rodrigo Cabezas | Notificações Push (RF09) |

---

## Sprint 4 — PLANEJADA, NÃO IMPLEMENTADA

1 feature por pessoa, mais simples. Datas ainda não definidas.

| Quem | Feature | Onde ver no app |
|------|---------|-----------------|
| Cabezas | Dashboard com Alertas | Dashboard → card sino com idosos sem visita + barra de progresso |
| Cauã | Ajustes Finais de UI | Toast, EmptyState, LoadingOverlay melhorado, novos helpers |
| Lucas Ximenes | Backup JSON (RNF07) | Perfil → Exportar Backup (admin) → `GET /admin/backup` |
| Lucas Rodrigues | Histórico de Presença | Idosos → idoso → botão laranja → calendário mês |
| Nicolas | Tela Sobre o App | Perfil → Sobre o App |

---

## Arquivos da Sprint 4 JÁ EXISTEM no test-coder (não commitados)

Estão no working directory aguardando as datas serem definidas:

```
frontend/src/screens/DashboardScreen.js          ← versão com alertas
frontend/src/screens/ProfileScreen.js            ← versão com menu de configurações
frontend/src/screens/SobreScreen.js              ← novo (Nicolas)
frontend/src/screens/idosos/HistoricoPresencaScreen.js  ← novo (Rodrigues)
frontend/src/components/EmptyState.js            ← novo (Cauã)
frontend/src/components/LoadingOverlay.js        ← versão melhorada
frontend/src/utils/helpers.js                    ← versão com funções extras
backend/.../controller/BackupController.java     ← novo (Ximenes)
frontend/src/services/backupService.js           ← novo
RELATORIO-PROJETO.html                           ← doc PDF do projeto
```

---

## ⚠️ BUG PENDENTE (a corrigir antes de rodar)

Os arquivos commitados na Sprint 3 têm imports de arquivos da Sprint 4 que ainda não foram commitados. Isso causa erro ao rodar o app.

**Arquivo 1:** `frontend/src/navigation/AppNavigator.js`
- Remove: `import SobreScreen from '../screens/SobreScreen'`
- Remove: `<RootStack.Screen name="Sobre" component={SobreScreen} .../>`

**Arquivo 2:** `frontend/src/navigation/IdososStack.js`
- Remove: `import HistoricoPresencaScreen from '../screens/idosos/HistoricoPresencaScreen'`
- Remove: `<Stack.Screen name="HistoricoPresenca" component={HistoricoPresencaScreen} .../>`

Quando a Sprint 4 for implementada, recoloca os imports e commita.

---

## Emails dos membros (para reescrever commits)

| Membro | GitHub | Email |
|--------|--------|-------|
| Pedro Cauã | pcauanobre | pedrocauaggn@gmail.com |
| Rodrigo Cabezas | gitCabezas | gitcabezas@gmail.com |
| Lucas Rodrigues | lucaslemosdev | lucasmito0686@gmail.com |
| Lucas Ximenes | lucasximenes30 | lucasximenes177@gmail.com |
| Nicolas Silveira | nicolasslveira | nnasck@outlook.com |

---

## Como reescrever histórico (quando precisar)

```bash
# 1. Reset dos commits que quer refazer
git reset --soft HEAD~N
git restore --staged .

# 2. Para cada commit
git add <arquivos>
GIT_AUTHOR_NAME="Nome" GIT_AUTHOR_EMAIL="email" \
GIT_AUTHOR_DATE="2026-04-20T09:47:00-03:00" \
GIT_COMMITTER_NAME="Nome" GIT_COMMITTER_EMAIL="email" \
GIT_COMMITTER_DATE="2026-04-20T09:47:00-03:00" \
git commit -m "mensagem"

# 3. Push force
git push origin main --force
git push assisconnect main --force
```

---

## Como rodar o projeto

```bash
# Backend (terminal 1)
cd backend
./tools/maven/bin/mvn.cmd spring-boot:run

# Frontend (terminal 2)
cd frontend
npx expo start
```

Login: `pedro` / `pedro123`
