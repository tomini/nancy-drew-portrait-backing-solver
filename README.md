# Portrait Backing Solver – Nancy Drew: Shadow at the Water's Edge

Peg puzzle solver for the portrait backing in *Nancy Drew: Shadow at the Water's Edge*. Pegs are joined by lines, and no lines may cross. Tell it where your pegs are and it tells you which pegs to move, and where, so nothing crosses.

I made this for a streamer who was stuck on the puzzle, and I'm keeping it online for anyone else who ends up in the same spot.

**Use it here:** https://tomini.github.io/nancy-drew-portrait-backing-solver/

Nothing to install. It runs entirely in your browser, and your screenshot never leaves your machine.

## Haven't touched the pegs yet?

Click **Junior start** or **Senior start** for your difficulty, then **Solve**. The pegs load at the game's original layout.

## Already moved the pegs?

Most people are here because of this. The game can't put the pegs back, so rebuild your current board in the solver:

1. In the game, drag the pegs apart so every line between them is easy to read, and take a screenshot.
2. Click **Load…** (or paste with **Ctrl+V**) and load your screenshot. A crop tool opens — drag the box over just the **playable** area (the pegs and lines), not the wooden frame border around them, then **Use crop**. Including the frame border throws off where the solver thinks the pegs are. Use **Recrop…** later to redo it without reloading. (If you clicked **Junior start** or **Senior start** earlier, click **Clear** first to start from an empty board.)
3. **Add peg**: click each peg on the screenshot.
4. **Connect**: click two pegs to add a line between them, and repeat for every line. Click the same two again to remove it.
5. Check the counts in the **Debug / export / import** panel: Junior has 15 pegs and 30 lines, Senior has 18 pegs and 43 lines.
6. Click **Solve**. Every peg that has to move turns green; pegs that stay grey don't move. For each green peg, find it at its **dashed circle** (where it is now) and drag it, in the game, to the **green peg at the end of the arrow** (where it should go).

Peg numbers are only the order you added them. They don't match anything in the game.

## Other controls

- **Move** drags pegs. **Delete line** removes a single line. **Delete peg** removes a peg and its lines.
- **Hide** / **Show** toggles the screenshot. The **Lines** button makes the lines translucent or fully visible.
- **Step by step** (bottom left of the board, after a solve) shows one move at a time: the peg to move is ringed in yellow and a green circle marks where to drop it. Use ▶ / ◀ to go through the moves, and **Show all** to go back. The moves are ordered so a peg is not dropped onto one that hasn't moved yet.
- **Stop** (while solving) uses the best result found so far. **Undo solved result** puts your layout back.
- **Guide** in the app repeats these steps.
- Crossing lines are drawn red.
- The Debug panel shows coordinates and connections, and exports or imports the board as JSON. Coordinates are fractions of the board, so they don't depend on the screenshot size.

## How it works

Simulated annealing. It moves pegs at random, keeps changes that reduce crossings (and sometimes worse ones early on), and cools over time. Once nothing crosses, it tries putting each moved peg back where it started and keeps the result if the board stays clean.

It runs in short slices, so the page stays responsive and shows the best result so far. It stops after 3 seconds with no improvement, or 15 seconds in total.

It always gives a valid layout, but not necessarily the fewest possible moves. In tests it moved 8–9 pegs for Junior and 12–13 for Senior from the game's start layout. Drop pegs close to the target spots, not on exact pixels.

## Run locally

Open `index.html` in a browser. There is no build step and no dependencies.

## Disclaimer

This is an unofficial fan-made tool. It is not affiliated with, endorsed by or sponsored by HeR Interactive. *Nancy Drew* and *Shadow at the Water's Edge* are trademarks of their respective owners. The puzzle frame and backing textures (`assets/`) are extracted from the game and used decoratively; screenshots you load yourself stay in your browser and are never uploaded anywhere.

## License

[MIT](LICENSE)
