# frogger
Objective: Make you character pass 9 lanes of traffic without collision, and within a certain time.
           If a new level is reached, cars will get bigger, and speeds will get faster.


Implementation: I used an outdated assembly language called CUSP. CUSP supports 5 registers and 10 easy to use addressing modes. 
It allowed me to make use of an IO mapped IO, and keyboard and timer registers to display moving characters on the screen.

Structure of data: Array of objects (lanes) found at the bottom of the file.
  A lane includes a starting IO port, for which a sequence of cars should be drawn on the IO.
  It also includes a frame offset, which determines how far the car should be draw from its initial location.
    (Note that the width of the IO is 38, so any car location past 0 or 38 will recycle to 38 or 0 respectively).
  Thirdly, a lane will have a refresh rate, which determines how often the lane is redrawn (its speed).
  Also, a lane has a direction of travel (left or right, -1 or 1).
  The rest of the data in the structure is a series of 6 car sizes+gaps (sums to 38).
  
Another item to note: Car sizes and lane speeds are both randomly generated upon reaching a new level.
 
Function of car animation: delete the end character of the car, and replace the front with a new car character
  That goes for any updating item: player, score, and lives, but the car animation had to be optimized.

Score: +10 per new line reached on a level, and +50 (and time remaining) if end of level is reached

Since CUSP is an outdated environment, I've included my own gameplay:
