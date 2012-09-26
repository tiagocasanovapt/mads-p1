# Product Backlog I

2.1. "Where there are mines and robots and things"

A mine is an n x m grid of cells, with the convention that (1, 1) is the bottom left and (n, m) is the top right. Each cell contains one of the following:

a. Mining Robot (R in ASCII)
b. Rock (*)
c. Closed Lift (L)
d. Open Lift (O)
e. Earth (.)
f. Wall (#)
g. Diamond (x)
h. Empty ( ) (yes, that was a space in ASCII)

There is nothing beyond the walls of the mine; only empty space.

2.2. "Time passes and rocks fall"

A mine is not static. As time passes, rocks that are not supported by other objects fall one cell at a time (until it collides). To simplify things, let us consider that nothing can happen under 1 second (or 1 step). So, if a rock is in an unsupported cell at second 0, it will be in the cell beneath it in second 1; and so on. In other words:

a. If (x, y) contains a Rock, and (x, y − 1) is Empty, then (x, y) is updated to Empty, and (x, y − 1) is updated to Rock.

For some unknown physical reasons, the cell grid is always updated left to right, then bottom to top.

2.3. "Where the robot moves"

In each step, the robot executes a command (which, of course, makes the mine layout update). Commands that the robot can execute are:

a. Move Left  (L), moving the robot from (x, y) to (x - 1, y)
b. Move Right (R), moving the robot from (x, y) to (x + y, y)
c. Move Up    (U), moving the robot from (x, y) to (x, y + 1)
d. Move Down  (D), moving the robot from (x, y) to (x, y - 1)
e. Wait       (W), which does nothing

In any case, the robot cannot pass walls (despite all the government attempts to contract "Micas").

2.4. "Where the robot can't move everywhere"

The robot can only move to a new location if:

a. It is a Diamond
b. It is an Open Lift

2.5. "Where the robot escavates and picks up diamonds and lifts open"

Whenever the robot moves into a cell occupied by Earth, it makes that cell Empty. Whenever the robot moves into a cell occupied by a Diamond, it collects it (and thus makes the cell Empty). When all diamonds in a mine are collected, the lift opens.

2.6. "Where invalid commands make the robot wait"

Whenever a command cannot be understood (or performed) by the robot, then the robot does nothing. However, time passes; it is thus equivalent to executing a "Wait" command.