# How to Set Up the Tests for the Bowling Lab

NOTE: This guide is for the lab machines, if you are on mac or WSL you can follow these same steps and test locally. As always, make sure your code works on the lab machines before submitting. If you are on WSL, you may need to install the `zip` and `unzip` utilities with `sudo apt install zip unzip`

Make a new directory

```bash
abradl11:hydra0 ~/cs102› mkdir bowling-lab
```

Move your `bowling.cpp` file into the new directory (or just create it in the directory if don't have one yet)

```bash
abradl11:hydra0 ~/cs102› mv bowling.cpp bowling-lab/
```

Download the tests into the directory

```bash
curl https://raw.githubusercontent.com/seeker-3/cs102-resources/main/tests/cs102-bowling-tests.zip -o cs102-bowling-tests.zip
```

Your directory should look like this

```bash
abradl11:hydra0 ~/cs102/bowling-lab› ls
bowling.cpp  bowling-tests.zip
```

Unzip the tests

```bash
abradl11:hydra0 ~/cs102/bowling-lab› unzip bowling-tests.zip
*lots of output*
```

And your directory should look like this

```bash
abradl11:hydra0 ~/cs102/bowling-lab› ls
bowling.cpp  bowling-tests.zip  scripts/ tests/
```

Run the tests like this

NOTE: the script will recompile your program each time you run it, so you don't need to recompile it yourself.

```bash
abradl11:hydra0 ~/cs102/bowling-lab› bash scripts/test.bash bowling.cpp
PASSED: 000-none.txt
FAILED: 010-ones.txt

YOURS                                                                   EXPECTED

Enter player's name (done for no more players):                         Enter player's name (done for no more players):
Enter score for frame 1, roll 1:                                        Enter score for frame 1, roll 1:
Enter score for frame 1, roll 2:                                        Enter score for frame 1, roll 2:
Enter score for frame 2, roll 1:                                        Enter score for frame 2, roll 1:
Enter score for frame 2, roll 2:                                        Enter score for frame 2, roll 2:
Enter score for frame 3, roll 1:                                        Enter score for frame 3, roll 1:
Enter score for frame 3, roll 2:                                        Enter score for frame 3, roll 2:
Enter score for frame 4, roll 1:                                        Enter score for frame 4, roll 1:
Enter score for frame 4, roll 2:                                        Enter score for frame 4, roll 2:
Enter score for frame 5, roll 1:                                        Enter score for frame 5, roll 1:
Enter score for frame 5, roll 2:                                        Enter score for frame 5, roll 2:
Enter score for frame 6, roll 1:                                        Enter score for frame 6, roll 1:
Enter score for frame 6, roll 2:                                        Enter score for frame 6, roll 2:
Enter score for frame 7, roll 1:                                        Enter score for frame 7, roll 1:
Enter score for frame 7, roll 2:                                        Enter score for frame 7, roll 2:
Enter score for frame 8, roll 1:                                        Enter score for frame 8, roll 1:
Enter score for frame 8, roll 2:                                        Enter score for frame 8, roll 2:
Enter score for frame 9, roll 1:                                        Enter score for frame 9, roll 1:
Enter score for frame 9, roll 2:                                        Enter score for frame 9, roll 2:
Enter score for frame 10, roll 1:                                       Enter score for frame 10, roll 1:
Enter score for frame 10, roll 2:                                       Enter score for frame 10, roll 2:
Enter player's name (done for no more players):                         Enter player's name (done for no more players):

John scored 21.                                                 |       John scored 20.
John did the worst by scoring 21.                               |       John did the worst by scoring 20.
John won the game by scoring 21.                                |       John won the game by scoring 20.


Run the test by itself with: ./bowling.bin <tests/input/010-ones.txt | sed 's/: /: \n/g'
View the input with:  cat tests/input/010-ones.txt
View the output with: cat tests/output/010-ones.txt
```

The tests use the `diff` command to compare the outputs between yours and mine. the `|` symbol means the two lines are different. The `>` symbol with output in green means the line is missing in your program. The `<` symbol with output in red means the line is extra is yours. If the lines look the same, then it could be a whitespace issue.

Here's what the output should look like if all the tests pass

```bash
abradl11:hydra0 ~/cs102/bowling-lab› bash scripts/test.bash bowling.cpp
PASSED: 000-none.txt
PASSED: 010-ones.txt
PASSED: 011-zeros.txt
PASSED: 020-first-strikes.txt
PASSED: 021-first-spares.txt
PASSED: 022-last-strikes.txt
PASSED: 023-last-spares.txt
PASSED: 024-all-strikes.txt
PASSED: 025-all-spares.txt
PASSED: 026-all-spares.txt
PASSED: 030-clears.txt
PASSED: 040-duplicate.txt
PASSED: 041-duplicate.txt
PASSED: 050-best-worst.txt
PASSED: 051-duplicate-best-worst.txt
PASSED: 052-max-min.txt
PASSED: 060-canvas1.txt
PASSED: 061-canvas2.txt
PASSED: 070-frame-9.txt
```
