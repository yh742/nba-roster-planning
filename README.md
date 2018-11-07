# nba-roster-planning
A linear programming model for planning NBA rosters.

## The Problem
The demands of the long NBA season can lead to injury concerns. 
  * Injuries have caused coaches to sit players for rest.
  * In order to compensate players, the coaching staff has to allocate minutes to other players.
  * Incorrect planning can lead to:
    * Over usage of other players
    * Quality deterioration
    * Cascading injuries
    
## The Solution
Apply a linear programming model to help the coaching staff decide the optimal minutes to allocate for each lineup he puts on the floor.

## Data
We will grab data from the 2016-2017 New York Knicks (don't worry I am not a fan), and try to plan the first 10 games of the 2017-18 season. 
  * Avg minutes per game for each player
  * The different lineups used by Knicks over the season
  * The average point differential

## Assumptions
* The ideal minutes each player should play is equal to the average minutes per game 
* The +/- rating is an accurate portrayal of team performance 
* NYK should be able to perform at a  +/- rating of -3.6 (team average of 2016-17)
* The NYK has a roster comprising of only 11 players
* There is many more players to consider
* Players get waived and hired as the season progresses
* The NYK only played 10 lineups during this period -> Excel solver is quite slow 

## Constraints
* The lineups played in every game need to add up to 1 as these decision variables are described in percentages
* Make sure that the lineups being played maintain the same type of quality as a team at full strength (or at least try to)
* A player can only play 48 minutes in a game

## Decision Variables
* The percentage that the lineups is playing in a game 
* The minutes underage or overage based on the lineup percentage

## Outcome
* The objective functions is to minimize the sum of overage minutes
* The final solution is 256.70 of overage minutes after minimization
* This is not a great result and is a sign that the the NYK are not a very balanced team
* We can see the overage minutes for Carmelo Anthony and Derrick Rose are quite large 
* This is due to the fact that NYK depends heavily on lineups with both of these two players, and in order to maintain the level of play, they would both have to play on their rest days
* If we included all the possible lineups and players, the solution will be better as there are more players and lineups to choose from 

## ToDo:
Put this to the test using Gurobi in Python with more lineups!
