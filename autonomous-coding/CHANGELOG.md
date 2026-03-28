# Changelog

Toutes les evolutions notables du module `autonomous-coding` sont listees ici.

## [3.7.0] - 2026-03-28

### Added
- Nouveau flag CLI `--provider {claude,openai}` pour choisir explicitement le provider d'execution.
- Resolver provider/auth dedie pour distinguer Claude runtime et OpenAI/Codex runtime.
- Backend OpenAI base sur Codex CLI non interactif avec preflight credentials et verification Git.
- Couverture de tests dediee au dispatch provider, au preflight OpenAI, et a l'absence de shared session pour les backends qui ne le supportent pas.

### Changed
- Le preflight d'authentification tient maintenant compte du provider selectionne.
- Le partage de session est desactive par capacite backend et non plus uniquement par egalite de modele.
- La documentation CLI/README precise que le support OpenAI actuel passe par Codex CLI et non par une integration API OpenAI directe.

## [3.6.1] - 2026-03-27

### Added
- Nouveau flag CLI `--target-tests` pour definir explicitement le volume cible de tests dans les prompts de planification/initialisation (tous modes).

### Changed
- Priorite renforcee sur Playwright MCP en mode **headless par defaut** dans la configuration client (`client.py`).
- Clarification des consignes QA/prompts pour imposer Playwright headless en chemin principal, avec Puppeteer seulement en fallback.
- Mise a jour de la documentation versionnee (README + traceability consolidee) pour refleter cette politique navigateur.
- Si `--target-tests` n'est pas fourni, le runtime affiche un warning explicite et applique la valeur par defaut `200`.

## [3.6.0] - 2026-03-27

### Added
- Nouveau flag CLI `--auth-mode {api_key,cli,auto}` pour choisir explicitement la methode d'authentification.
- Detection best-effort des credentials Claude CLI (session/token/fichier credentials) pour preflight explicite.
- Couverture de tests dediee a la validation auth (`tests/test_client_auth.py`) et au parsing/erreurs CLI.

### Changed
- Preflight d'authentification centralise dans `client.py` (`validate_auth_configuration`) avec messages d'erreur actionnables.
- Integration de l'auth mode dans les chemins V3.1 (orchestrator) et V1 compat (`run_autonomous_agent`).
- Documentation mise a jour pour inclure les modes `cli` et `auto`.

## [3.5.2] - 2026-03-26

### Added
- Enrichissement de l'artefact de negociation (`reason_codes`, `confidence_score`, `actionable_suggestions`, `review_mode`).
- Option `--llm-contract-review` pour arbitrage de contrat assiste modele.

### Changed
- Alignement des marqueurs de version runtime/telemetrie sur V3.5.2.
- Conservation de compatibilite des statuts historiques (`approved|changes_requested`).

## [3.5.0] - 2026-03-26

### Added
- Telemetrie best-effort token/cout consolidee dans `state/run_state.json`.
- Resume d'usage LLM au niveau appel et phase.

### Changed
- Reprise (`--resume`) compatible avec cumul de metriques existantes.
- Schema `schemas/run_state.schema.json` etendu pour valider `llm_usage`.

## [3.4.0] - 2026-03-26

### Added
- Artefact de negociation de sprint `planning/sprint_contract_negotiation_round_XX.json`.

### Changed
- Durcissement progression des tests d'acceptation (normalisation, filtrage, deduplication).
- Validation plus stricte des propositions malformed.

## [3.3.0] - 2026-03-26

### Added
- Matrice de tracabilite dediee a la version 3.3.
- Contrat de chemin des artefacts de proposition sprint.

### Changed
- Filtrage des features deja tentees lors de la progression des rounds.
- Correctifs de prompts/typing et robustesse du parser de proposition.

## [3.2.0] - 2026-03-26

### Added
- Contrats de sprint par round avec cap/filtrage configurable.
- Integration explicite des propositions builder dans la preparation du round suivant.

### Changed
- Fallback deterministe `blocked` si rapport QA non conforme au schema.
- Avertissement explicite pour `--mode v2` deprecie.

## [3.1.0] - 2026-03-26

### Added
- Chemin principal en session continue (planner/builder/evaluator).
- Artefacts de contrat de sprint obligatoires.

### Changed
- Suppression du fallback silencieux builder vide (erreur explicite).
- Reprise renforcee (pas de redemarrage implicite d'un run termine).

---

## Notes
- Les dates exactes historiques anterieures peuvent etre affinees si vous souhaitez un changelog "calendaire" precis base sur l'historique Git.
