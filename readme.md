# Roteiro em Sprints (Releitura com foco no front atual)

## Contexto do produto
Aplicativo web/mobile para consultores registrarem **horas** e **RAT**, com múltiplos:
- consultores
- projetos
- clientes

Perfis de acesso:
- Diretor
- Financeiro
- PM
- Tech Lead
- Consultor

## Diretriz principal
Como já existe um front atual, a estratégia recomendada é **evoluir sem reescrever do zero**:
1. mapear telas e componentes existentes;
2. identificar gaps funcionais;
3. estabilizar UX/fluxos antes de expandir features.

---

## Sprint 0 — Releitura do front atual (AS-IS)
**Tarefa:** Inventariar o front existente (telas, rotas, componentes, estados, validações), mapear o que já funciona para horas e RAT e levantar inconsistências de UX.

**Fase:** Diagnóstico funcional e técnico.

**Responsável:** Tech Lead + Frontend Senior + PM.

**Tecnologias recomendadas:**
- Figma (documentar fluxo atual)
- Storybook (catálogo de componentes)
- Jira/Linear (backlog de gaps)

**Saída esperada:**
- Mapa de telas AS-IS
- Lista de gaps priorizada (Must/Should/Could)
- Decisão do que será reaproveitado vs. refatorado

---

## Sprint 1 — Base de acesso e domínio
**Tarefa:** Consolidar autenticação/autorização por perfil (Diretor, Financeiro, PM, Tech Lead, Consultor) e organizar domínio (cliente, projeto, consultor, alocação).

**Fase:** Fundação de segurança e modelo de dados.

**Responsável:** Backend + Tech Lead.

**Tecnologias recomendadas:**
- Backend: NestJS (ou .NET)
- Banco: PostgreSQL
- RBAC/Auth: Keycloak/Auth0
- API docs: OpenAPI/Swagger

---

## Sprint 2 — Fluxo de lançamento de horas
**Tarefa:** Entregar fluxo completo de lançamento de horas no front atual (diário/semanal), com validações, feedback de erro e salvamento consistente.

**Fase:** Core operacional.

**Responsável:** Frontend + Backend + QA.

**Tecnologias recomendadas:**
- Front web: React/Next.js
- Mobile: React Native (se já houver app)
- Formulários: React Hook Form + Zod

---

## Sprint 3 — Fluxo de RAT
**Tarefa:** Implementar/ajustar preenchimento de RAT com campos obrigatórios, anexos (se necessário) e histórico de alterações.

**Fase:** Core operacional.

**Responsável:** Frontend + Backend.

**Tecnologias recomendadas:**
- Upload: storage compatível (S3/Azure Blob)
- Auditoria de alteração no backend

---

## Sprint 4 — Aprovação por níveis
**Tarefa:** Implantar workflow de aprovação com devolução para ajuste:
- Consultor envia
- Tech Lead/PM valida
- Financeiro confere
- Diretor acompanha visão executiva

**Fase:** Governança.

**Responsável:** Backend + PM + Financeiro.

**Tecnologias recomendadas:**
- Máquina de estados no backend
- Notificações por e-mail/push

---

## Sprint 5 — Dashboards e fechamento
**Tarefa:** Criar dashboards por cliente/projeto/consultor e processo de fechamento mensal com exportação.

**Fase:** Gestão e inteligência.

**Responsável:** Backend + Frontend + Financeiro.

**Tecnologias recomendadas:**
- Dashboards: ECharts/Chart.js
- Exportação: CSV/XLSX/PDF

---

## Sprint 6 — Qualidade e escala
**Tarefa:** Fortalecer qualidade, observabilidade e segurança para produção.

**Fase:** Hardening.

**Responsável:** QA + Tech Lead + DevOps.

**Tecnologias recomendadas:**
- Testes: Playwright/Cypress + Jest
- Observabilidade: Sentry + Grafana
- CI/CD: GitHub Actions/GitLab CI

---

## Matriz de responsabilidades por perfil
- **Consultor:** lança horas e RAT, corrige devoluções.
- **Tech Lead:** valida tecnicamente lançamentos.
- **PM:** controla aderência por projeto/sprint.
- **Financeiro:** fecha competência e consolida faturamento.
- **Diretor:** acompanha indicadores executivos.

## KPIs mínimos
- % de lançamentos feitos dentro do prazo
- tempo médio de aprovação
- % de devoluções para correção
- horas aprovadas vs. horas lançadas
- aderência por consultor/projeto

## Entrega mínima recomendada (até Sprint 3)
1. Login + RBAC por perfil.
2. Cadastro de cliente/projeto/consultor.
3. Lançamento de horas funcionando ponta a ponta.
4. Lançamento de RAT funcionando ponta a ponta.
