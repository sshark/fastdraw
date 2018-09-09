# FastDraw
A console drawing application using line commands.

## How to Build
This project is built using [SBT](http://www.scala-sbt.org/download.html) and runs on [Scala 2.12](http://www.scala-lang.org/download/) on Linux. Please make sure these software are installed and accessible from shell before proceeding.

1. `sbt` to start the build tool. Steps (2) and (3) must be executed in the SBT console.
2. `fastDrawFill/run` to run the application.
3. `test` to run the all test spec.

## Commands

| Command 		    | Description
| ------------------|------------
| C w h             | Should create a new canvas of width w and height h.
| L x1 y1 x2 y2     | Should create a new line from (x1,y1) to (x2,y2). Currently only horizontal or vertical lines are supported. Horizontal and vertical lines will be drawn using the 'x' character.
| R x1 y1 x2 y2     | Should create a new rectangle, whose upper left corner is (x1,y1) and lower right corner is (x2,y2). Horizontal and vertical lines will be drawn using the 'x' character.
| B x1 y1 c         | Should fill the entire area connected to (x,y) with "colour" c. The behaviour of this is the same as that of the "bucket fill" tool in paint programs.
| Q                 | Should quit the program.

## Sample Output

Below is a sample run of the program. User input is prefixed with enter command:

```
enter command: C 20 4
----------------------
|                    |
|                    |
|                    |
|                    |
----------------------

enter command: L 1 2 6 2
----------------------
|                    |
|xxxxxx              |
|                    |
|                    |
----------------------

enter command: L 6 3 6 4
----------------------
|                    |
|xxxxxx              |
|     x              |
|     x              |
----------------------

enter command: R 14 1 18 3
----------------------
|             xxxxx  |
|xxxxxx       x   x  |
|     x       xxxxx  |
|     x              |
----------------------

enter command: B 10 3 o
----------------------
|oooooooooooooxxxxxoo|
|xxxxxxooooooox   xoo|
|     xoooooooxxxxxoo|
|     xoooooooooooooo|
----------------------

enter command: Q
```

## Missing Bells and Whistles
1. Command parameters are not validated and it may caused the application to hang or crash.
2. ~~Bucket fill feature is not supported yet.~~ Bucket fill is added as _add-on_ feature.
3. Parameters validations need to be better organized.
4. ~~Should use single linear array instead of multiple arrays for buffer.~~
5. ~~Should use immutable `List` for buffer instead of multiple mutable `Array`s. Related to previous point.~~
6. Canvas should contain only simple functions e.g. draw single pixels instead of draw lines or flood. Complex functions should be located in the command package.
7. Command should come in a complete package that consist of parameter parser and how to draw on canvas. Related to previous point.
8. ~~Canvas should not contain a list of commands. Instead, each command should operate on the canvas and return a modified canvas for the next command.~~
9. ~~A draw command on an empty canvas should not quit the application.~~
10. ~~Let border function take care of the total width.~~
