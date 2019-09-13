# puzzle-game
There are three levels for this game-

     Beginner – 9 * 9 Board and 10 Mines
    Intermediate – 16 * 16 Board and 40 Mines
    Advanced – 24 * 24 Board and 99 Mines

Probability of finding a mine –

    Beginner  level –  10/81 (0.12)
    Intermediate level – 40/256 (0.15)
    Advanced level – 99 / 576 (0.17)

    When we click on a cell having adjacent mines in one or more of the surrounding eight cells, then we get to know how many adjacent cells have mines in them. So we can do some logical guesses to figure out which cells have mines.
    If you click on a cell having no adjacent mines (in any of the surrounding eight cells) then all the adjacent cells are automatically cleared, thus saving our time.
    So we can see that we don’t always have to click on all the cells not having the mines (total number of cells – number of mines) to win. If we are lucky then we can win in very short time by clicking on the cells which don’t have any adjacent cells having mines.

Implementation

Two implementations of the game are given here:

    In the first implementation, the user’s move is selected randomly using rand() function.
    In the second implementation, the user himself select his moves using scanf() function.

Also there are two boards- realBoard and myBoard. We play our game in myBoard and realBoard stores the location of the mines. Throughout the game, realBoard remains unchanged whereas myBoard sees many changes according to the user’s move.

We can choose any level among – BEGINNER, INTERMEDIATE and ADVANCED. This is done by passing one of the above in the function – chooseDifficultyLevel() [However in the user-input game this option is asked to the user before playing the game].

Once the level is chosen, the realBoard and myBoard are initialized accordingly and we place the mines in the realBoard randomly. We also assign the moves using the function assignMoves() before playing the game [However in the user-input game the user himself assign the moves during the whole game till the game ends].

We can cheat before playing (by knowing the positions of the mines) using the function – cheatMinesweepeer(). In the code this function is commented . So if you are afraid of losing then uncomment this function and then play !

Then the game is played till the user either wins (when the user never steps/clicks on a mine-containing cell) or lose (when the user steps/clicks on a mine-containing cell). This is represented in a while() loop. The while() loop terminates when the user either wins or lose.

The makeMove() function inside the while loop gets a move randomly from then randomly assigned moves. [However in the user-input game this function prompts the user to enter his own move].

Also to guarantee that the first move of the user is always safe (because the user can lose in the first step itself by stepping/clicking on a cell having a mine, and this would be very much unfair), we put a check by using the if statement – if (currentMoveIndex == 0)

The lifeline of this program is the recursive function – playMinesweeperUtil()

This function returns a true if the user steps/clicks on a mine and hence he loses else if he step/click on a safe cell, then we get the count of mines surrounding that cell. We use the function countAdjacentMines() to calculate the adjacent mines. Since there can be maximum 8 surrounding cells, so we check for all 8 surrounding cells.

If there are no adjacent mines to this cell, then we recursively click/step on all the safe adjacent cells (hence reducing the time of the game-play). And if there is atleast a single adjacent mine to this cell then that count is displayed on the current cell. This is given as a hint to the player so that he can avoid stepping/clicking on the cells having mines by logic.
Also if you click on a cell having no adjacent mines (in any of the surrounding eight cells) then all the adjacent cells are automatically cleared, thus saving our time.

So we can see that we don’t always have to click on all the cells not having the mines (total number of cells – number of mines) to win. If we are lucky then we can win in very short time by clicking on the cells which don’t have any adjacent cells having mines.

The user keeps on playing until he steps/clicks on a cell having a mine (in this case the user loses) or if he had clicked/stepped on all the safe cell (in this case the user wins).
