# doybu

an online multiplayer checkers game that runs entirely in the browser.

## play

open `index.html` in any modern browser, or use the hosted copy on github pages.
everything else (accounts, matchmaking, leaderboards) is handled by the services
below; there is no build step and no server of your own to run.

## what is in here

| file | purpose |
| --- | --- |
| `index.html` | the whole app: auth screen, game engine, matchmaking ui, profile, leaderboard, match history |
| `mittens.jpg` | mascot |
| `README.md` | this file |

## how it works

- **accounts** — firebase authentication (email + password, plus popup sign-in)
- **state** — cloud firestore, collections `games` and `users`
- **matchmaking** — a cloudflare worker (see `WORKER_URL` in `index.html`)
- **engine** — 8x8 board, diagonal movement, captures, draws, bot opponent

the firebase web config near the top of `index.html` is client-side configuration,
not a secret: it ships to every browser that loads the page. access control lives in
the firestore security rules and the firebase console (authorized domains, api key
restrictions), not in this file. if you rotate or restrict anything in the firebase
console, update the config block here to match.

## local development

no dependencies. edit `index.html`, reload the browser. the page pulls the firebase
sdk and two google fonts from cdns, so first load needs a network connection.
