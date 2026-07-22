# UNUSABLE — Gamification sulla (scarsa) UX

## Descrizione del progetto

**UNUSABLE** è un'applicazione web a livelli, interamente contenuta in un singolo file HTML (HTML, CSS e JavaScript inline, senza dipendenze esterne), che trasforma pattern classici di interfacce volutamente disfunzionali — noti nel filone informale delle "bad UI" — in una serie di dieci sfide giocabili, brevi e comiche.

Ogni livello prende un elemento di interazione comune (un campo data, una casella di consenso, un pulsante di conferma, uno slider, un login, un calendario, un cruciverba) e lo rende deliberatamente ostile all'uso, mantenendo però sempre una via di risoluzione garantita. L'obiettivo dichiarato del progetto è l'intrattenimento attraverso la parodia della UX, non la frustrazione fine a sé stessa.

File principale: `index.html`

## Come eseguire il progetto

Il file non richiede installazione, build o server: è sufficiente [aprirlo](https://salvatorecapolupo.github.io/unusable/) in un browser moderno (Chrome, Firefox, Safari, Edge). È compatibile con desktop, tablet e dispositivi mobili.

## Interfaccia e navigazione

- **Intestazione**: nome del progetto e indicatore del livello corrente.
- **Barra di avanzamento**: dieci indicatori cliccabili, uno per livello, che permettono di saltare liberamente tra i livelli già raggiunti.
- **Controlli di navigazione**: pulsanti "livello precedente" e "livello successivo" per scorrere la sequenza senza dover completare ogni sfida in ordine stretto.

## Elenco dei livelli

| # | Titolo | Meccanica |
|---|--------|-----------|
| 1 | Che giorno è oggi? | Inserimento di una data tramite un tastierino numerico le cui posizioni si rimescolano dopo alcuni utilizzi. |
| 2 | Accetta i termini | Un numero variabile (3–8) di caselle di consenso cade con fisica a gravità reale (accelerazione, attrito, rimbalzo) e va accettata al volo. |
| 3 | Prendi il tasto INVIA | Il pulsante di conferma si muove nello spazio a velocità casuale a ogni round; il punteggio è inversamente proporzionale alla velocità al momento del colpo. Include un mirino personalizzato compatibile con mouse e tocco. |
| 4 | Trova le parole scritte male | Dieci parole italiane comuni, di cui 3–4 presentano un errore grossolano ma restano visivamente simili all'originale; l'utente deve individuarle e confermare la selezione. |
| 5 | Componi il numero | Adattamento del concetto "phone slider selector": uno slider a risoluzione volutamente insufficiente copre l'intero spazio di un numero di cellulare italiano. Due modalità operative (Base e Avanzata, quest'ultima con una fisica di deriva che si inclina visivamente) più pulsanti di precisione che garantiscono sempre una via di soluzione. |
| 6 | Gioco dei sinonimi | Un campo di testo reale, largo esattamente quanto la risposta più breve attesa: ogni carattere in eccesso cade fisicamente oltre il bordo del campo. Le definizioni sono estratte casualmente da un piccolo dizionario interno in formato JSON. |
| 7 | CatchLogin | Un login navigabile senza mouse: un labirinto generato proceduralmente (sempre risolvibile per costruzione) va attraversato per raggiungere in sequenza i campi Utente e Password. Controllabile in modo equivalente da tastiera, D-pad touch e gesti di scorrimento. |
| 8 | Calendar Hell | Individuazione di una data lontana 2–6 anni, navigabile solo tramite frecce mese/anno. Include elementi di variabilità: giorni che collassano con fisica a gravità, scosse sismiche casuali, segnali acustici generati via Web Audio API, indicazioni volutamente ambigue e un comando di salto anno dall'esito non deterministico. |
| 9 | Cruciverba a caduta | Un cruciverba a incrocio singolo le cui coppie di parole e relative definizioni sono estratte casualmente da un dizionario JSON interno; le lettere già inserite correttamente possono collassare nel tempo e richiedere una nuova digitazione. |
| 10 | Il Gauntlet Finale | Sequenza conclusiva di tre prove ridotte, ciascuna basata sul motore di un livello precedente (cattura del pulsante mobile, accettazione di caselle in caduta, attraversamento di un mini-labirinto), a chiusura dell'esperienza. |

## Principi di design

- **Risolvibilità garantita**: ogni livello, anche quando introduce elementi casuali o di disturbo, offre sempre un percorso di completamento verificabile (pulsanti di precisione, labirinti generati come alberi di copertura sempre connessi, tolleranze di punteggio calibrate).
- **Variabilità controllata**: dove opportuno, i contenuti (numero di elementi, parole, definizioni, bersagli) sono estratti casualmente da insiemi predefiniti, per aumentare la rigiocabilità senza compromettere la coerenza dell'esperienza.
- **Compatibilità multi-dispositivo**: i livelli che richiedono interazione direzionale (es. livello 7) espongono controlli equivalenti per tastiera, tocco e puntatore.
- **Attenzione all'accessibilità**: gli effetti visivi ad alta intensità (ad esempio le luci lampeggianti del livello 8) sono calibrati con frequenza e area contenute, per limitare il rischio di disagio fotosensibile.

## Note tecniche

- Nessuna libreria o framework esterno: HTML, CSS e JavaScript nativi in un unico file.
- Le animazioni fisiche (gravità, rimbalzo, caduta di elementi) sono implementate tramite `requestAnimationFrame`.
- La generazione procedurale dei labirinti utilizza un algoritmo di tipo randomized depth-first search, che produce per costruzione un grafo sempre connesso tra punto di partenza e destinazione.
- I contenuti testuali variabili (dizionari di sinonimi e di parole crociate) sono strutturati come dati in formato JSON, analizzati a runtime.

## Ispirazione e attribuzione

Alcuni livelli si ispirano concettualmente a progetti pubblici di "bad UI" (in particolare la raccolta [GoulartNogueira/BadUI](https://github.com/GoulartNogueira/BadUI), a sua volta collegata alla community r/badUIbattles): il "Phone Slider Selector", il concetto di limitazione dei caratteri con effetto di eliminazione, e il login navigabile a labirinto. In tutti i casi, il meccanismo è stato reimplementato autonomamente in JavaScript proprio, senza riutilizzo di codice originale; dove verificato, il comportamento è stato reso più fedele alla fonte su richiesta esplicita, per poi essere adattato a fini di giocabilità.

Claude ha terminato la risposta
Individuo le sezioni da modificare

    Rinomino il livello 1.

Rinomino il titolo del livello 1 in "Che giorno è oggi?"

    Livello 2: numero di pillole randomico da 3 a 8.

Architettato sistema di pillole casuali con etichette variabili e interfaccia compatta

    Livello 3: click più affidabile (pointerdown invece di click) + testi buffi casuali.

Ricalibrò proporzioni tipografiche per coerenza visiva scalabile

    Livello 6: dizionario di più vocaboli per il gioco dei sinonimi.

Architettato refactoring JSON, dinamizzato sinonimi e ottimizzato interfaccia

Devo aggiornare il riferimento a LIMIT (ora dinamico per round) nel listener di input.
2 file modificati, eseguito un comando, file visualizzato

    Livello 7: vista più compatta, senza scroll, indipendente dalla risoluzione.

Orchestrated responsive layout con calcoli dinamici per maze compatto

Ora rendo la dimensione delle celle del labirinto dinamica in base allo spazio disponibile, ricalcolata a ogni ingresso nel livello.
File visualizzato, file modificato

Ora chiamo computeCellSize() dentro resetLevel7, prima di generare/renderizzare il labirinto.
Verificò l'integrità del codice prima d'implementare il livello avanzato

Ora verifico coerenza prima di passare al livello 10 (cruciverba a caduta).
Verifica intermedia prima del livello 10

    Livello 9 (nuovo): cruciverba a caduta, con definizioni pescate da un piccolo dizionario JSON interno.

Trovo i punti di aggancio per il nuovo livello 9

Aggiungo CSS, markup e motore del livello 9.
CSS per il livello 9: cruciverba, celle, lettere che crollano

Ora il markup del livello 9, e ridireziono nextBtn9 verso il nuovo livello invece del toast "in arrivo".
Markup livello 9: cruciverba a caduta

Ora MAX_LEVEL_IMPLEMENTED, l'aggancio in goToLevel, e il collegamento nextBtn9.
2 file modificati, eseguito un comando

Ora collego nextBtn9 e aggiungo il motore completo del livello 9.
Verificati gli incroci e gli allineamenti delle parole nel cruciverba

Tutte le intersezioni verificate. Presento il file finale.
Orchestrated documentation updates per level progression changes

Ho implementato tutto. Riassumendo le correzioni:

    Livello 1 → rinominato "Che giorno è oggi?"
    Livello 2 → pillole di consenso ora random da 3 a 8 (pool di 8 frasi)
    Livello 3 → click più reattivo (passato da click a pointerdown, molto più affidabile su desktop); al colpo il bottone scrive una frase buffa casuale (AHIA, UFFA, LASCIAMI STARE...) per un attimo e riparte con traiettoria/velocità nuove
    Livello 6 → dizionario JSON interno con 6 vocaboli (non solo INUTILIZZABILE), uno estratto a caso ad ogni round, stessa identica UI
    Livello 7 → niente più scroll: dimensione del labirinto calcolata dinamicamente in base allo spazio disponibile, sempre centrato con D-pad sotto, qualunque risoluzione
    Livello 9 (nuovo) → cruciverba a caduta: griglia 4×4 a incrocio singolo, 4 coppie di parole/definizioni in un piccolo JSON interno (estratte a caso), lettere già corrette che ogni ~3.5s crollano a caso con la stessa fisica a gravità del resto del progetto

Una nota: hai detto "decimo livello" per il cruciverba, ma l'ho inserito come livello 9 (il prossimo slot libero in sequenza) per non lasciare un buco nella barra di avanzamento — il livello 10 resta libero. Dimmi se intendevi diversamente.
Livelli inusabili
Codice · HTML 

no, va bene
pensiamo al decimo livello
ci sono idee inutilizzate ad oggi?
Inventariati tre concetti puzzle inutilizzati per il decimo livello

Sì, dal brainstorm di prima ne sono rimaste tre non usate (avevo proposto 4 idee per il puzzle a caduta, ne abbiamo fatta solo una):

    Tetris di parole — lettere cadono dall'alto una alla volta; le "catturi" nell'ordine giusto per comporre la parola bersaglio prima che troppe sbagliate si accumulino in basso.
    Frase da riordinare — tessere-parola da riordinare per formare una frase; una tessera non ancora piazzata ogni tanto cade dal vassoio ed è persa, quindi conviene sistemarla in fretta.
    Memoria a caduta — mostri una sequenza di lettere da memorizzare, poi le clicchi in ordine da una griglia; una tessera non ancora usata crolla ogni paio di secondi, restringendo le opzioni col tempo.

Tra queste la più semplice da costruire è la 1 (Tetris di parole), la più originale/diversa dagli altri livelli è probabilmente la 3 (introduce la memoria, finora mai usata). Quale scegli?

SISTEMA UNUSABLE(TM) diventa semplicemente UNUSABLE
pensiamo al livello 10 con qualcosa di diverso, riutilizzando le cose che gia abbiamo
Architettato finale ricombinando meccaniche esistenti in un'esperienza unificata

Fatto per il nome. Per il livello 10, un'idea che riusa quello che abbiamo già invece di inventare una meccanica nuova:

Il Gauntlet Finale — un ultimo livello che mette in fila, veloce, mini-versioni delle sfide già fatte: un tasto INVIA che rimbalza (dal livello 3, ma bastano 1-2 colpi), 2 pillole di consenso con gravità (dal livello 2), un salto rapido nel labirinto (dal livello 7). Tutto molto più breve del solito — è il "riassunto" finale del gioco, non una fatica aggiuntiva.

Alternativa, se preferisci qualcosa in un'unica schermata invece che in sequenza: Il Modulo Impossibile — un form con più campi, ognuno preso da un motore già costruito (data con tastierino che si rimescola, checkbox che cade con gravità, bottone invia che scappa), tutti visibili insieme, da completare in un colpo solo.

Preferisci il Gauntlet (in sequenza, riusa il codice com'è) o il Modulo (tutto insieme, un po' più di lavoro per farli coesistere)?

Gauntlet
Architected multi-stage gauntlet level combining physics, maze, and state management

Ora il markup del livello 10.
Markup livello 10: Il Gauntlet Finale

Ora MAX_LEVEL_IMPLEMENTED, l'aggancio in goToLevel, e il collegamento nextBtn10.
2 file modificati

Ora collego nextBtn10 e aggiungo il motore completo del Gauntlet.
Collego nextBtn10 al livello 10 e aggiungo il motore completo del Gauntlet Finale

Verifico coerenza id, bilanciamento div e sintassi.
Eseguito un comando, file letto

Tutti e 10 i livelli sono a posto:

    Header semplificato in UNUSABLE.
    Livello 10 — Il Gauntlet Finale: tre mini-prove in sequenza, ridotte e veloci, che riusano i motori già scritti — bounce a 2 colpi (livello 3), due pillole da accettare al volo (livello 2), mini-labirinto 4×4 con frecce/D-pad/swipe (livello 7). Alla fine, schermata di chiusura con pulsante per tornare al livello 1.

Il gioco è completo: 10 livelli, barra di avanzamento piena, navigazione libera tra tutti.
Livelli inusabili
Codice · HTML 

dammi un readme in formato md in due lingue, italiano e inglese
scritto in modo serio e professionale
Architected bilingual documentation aggiornata per dieci livelli

Entrambi i README sono pronti, aggiornati con tutti e 10 i livelli, tono professionale: README.md (italiano) e README.en.md (inglese).
Readme
Documento · MD 
Readme.en
Documento · MD 
Hai utilizzato 90% del limite della tua sessione


Claude è un'AI e può commettere errori. Verifica le risposte.
Readme.en · MD
# UNUSABLE — Layered Gamification Based on Unusability
 
## Project Description
 
**UNUSABLE** is a single-file, level-based web application (inline HTML, CSS and JavaScript, no external dependencies) that turns classic patterns of deliberately dysfunctional interfaces — informally known as "bad UI" — into a series of ten short, playable, comedic challenges.
 
Each level takes a familiar interaction element (a date field, a consent checkbox, a confirmation button, a slider, a login form, a calendar, a crossword) and deliberately renders it hostile to use, while always guaranteeing a path to completion. The project's stated purpose is entertainment through the parody of usability, not frustration for its own sake.
 
Main file: `livelli-inusabili.html`
 
## Running the Project
 
The file requires no installation, build step, or server: simply open it in a modern browser (Chrome, Firefox, Safari, Edge). It is compatible with desktop, tablet, and mobile devices.
 
## Interface and Navigation
 
- **Header**: project name and current level indicator.
- **Progress bar**: ten clickable markers, one per level, allowing free navigation among levels already reached.
- **Navigation controls**: "previous level" and "next level" buttons to move through the sequence without requiring strict in-order completion.
## Level Overview
 
| # | Title | Mechanic |
|---|-------|----------|
| 1 | What day is it today? | Entering a date via a numeric keypad whose key positions reshuffle after a few uses. |
| 2 | Accept the Terms | A variable number (3–8) of consent checkboxes fall under real gravity physics (acceleration, friction, bounce) and must be accepted in mid-air. |
| 3 | Catch the SUBMIT Button | The confirmation button moves around the play area at a randomized speed each round; the score is inversely proportional to the button's speed at the moment of the hit. Includes a custom crosshair cursor compatible with both mouse and touch input. |
| 4 | Find the Misspelled Words | Ten common Italian words are shown, 3–4 of which contain a coarse but visually similar misspelling; the player must identify and confirm the incorrect ones. |
| 5 | Dial the Number | An adaptation of the "phone slider selector" concept: a deliberately low-resolution slider covers the entire range of an Italian mobile phone number. Two operating modes (Basic and Advanced, the latter featuring a drift physics that visibly tilts the control) plus precision buttons that always guarantee a solvable path. |
| 6 | The Synonym Game | A real text input, sized exactly to the length of the shortest expected answer: any excess character physically falls past the field's boundary. Clues are drawn at random from a small internal JSON dictionary. |
| 7 | CatchLogin | A mouse-free login flow: a procedurally generated maze (always solvable by construction) must be traversed to reach the Username and Password fields in sequence. Controllable equivalently via keyboard, an on-screen touch D-pad, and swipe gestures. |
| 8 | Calendar Hell | Locating a date 2–6 years away, navigable only via month/year arrows. Includes variability elements: days that collapse under gravity physics, random seismic tremors, audio alerts generated via the Web Audio API, deliberately ambiguous hints, and a year-jump control with a non-deterministic outcome. |
| 9 | The Collapsing Crossword | A single-intersection crossword whose word pairs and clues are drawn at random from an internal JSON dictionary; correctly entered letters may collapse over time and require re-entry. |
| 10 | The Final Gauntlet | A closing sequence of three scaled-down challenges, each reusing the engine of a previous level (catching the moving button, accepting falling checkboxes, crossing a mini-maze), bringing the experience to a close. |
 
## Design Principles
 
- **Guaranteed solvability**: every level, even when introducing randomness or disruptive elements, always offers a verifiable path to completion (precision buttons, mazes generated as always-connected spanning trees, calibrated scoring tolerances).
- **Controlled variability**: where appropriate, content (element counts, words, clues, targets) is drawn at random from predefined sets, increasing replayability without compromising overall coherence.
- **Cross-device compatibility**: levels requiring directional interaction (e.g., level 7) expose equivalent controls for keyboard, touch, and pointer input.
- **Accessibility awareness**: high-intensity visual effects (such as the flashing beacons in level 8) are kept to a low frequency and confined area, to limit the risk of photosensitive discomfort.
## Technical Notes
 
- No external libraries or frameworks: native HTML, CSS, and JavaScript in a single file.
- Physics-based animations (gravity, bouncing, falling elements) are implemented using `requestAnimationFrame`.
- Procedural maze generation uses a randomized depth-first search algorithm, which by construction always produces a connected graph between start and destination.
- Variable text content (synonym and crossword dictionaries) is structured as JSON data, parsed at runtime.
## Inspiration and Attribution
 
Some levels are conceptually inspired by publicly available "bad UI" projects (notably the [GoulartNogueira/BadUI](https://github.com/GoulartNogueira/BadUI) collection, itself connected to the r/badUIbattles community): the "Phone Slider Selector," the character-limiting field with a discard effect, and the maze-navigated login. In all cases, the underlying mechanism was independently reimplemented in original JavaScript, with no reuse of source code; where verified, behavior was made more faithful to the source upon explicit request, and subsequently adapted for playability.


# unusable
unusable is unusable (recursively). 

