# American Baseball Association project

## Overview

This is just a simple client and server to store some additional
statistics that are not tracked by OOTP as well as additional awards
since the game only allows one custom award. This readme is mostly
just notes for myself to keep up with what I want this to track so
that I can then plan the UI out.

### Game Log

Simple list of games with the following information:

* Away Team
* Home Team
* Date
* Start time
* Attendance
* Player of the game
* Special Notes blob

### Team Related tracking

* Win streaks over x games long
* Loss streaks over y games long
* All-time team
* Player of the game count for team
* ... Tracking for all awards by players on the team

### Awards/Cool things to track

* Player of game
* Player of game king
* Winged Spikes(stolen bases)
* Award for catcher best at throwing out runners, name tbd
* Playoff MVP
* Notable playoff performance
* World series mvp
* Manager of the year
* Firsts

### Person data structure

* Serial ID
* Name
* OOTP ID
* Start year
* Current team

### Tables

* game_log(id, away team, home team, date, start time, length, attendance, pog, special notes)
* award(id, award_name)
* award_history(id, award, player, team, date)
* person(id, name, ootp id, start year, current team)
* team(id, name)
* all_time_team(id, team, player)
* team_streak(id, team, start date, end date, total games, is_win)

### Questions

* tracking manager vs player, what if player becomes manager later
* how to track firsts which can contain multiple people
  * maybe -> firsts table, firsts_players table
  * but how to handle like, first double play -> a grounded out to b who threw to c who threw to d

### Client pages

* Game log:
  * List of games paginated, sortable(any colum), and filterable(team, away team, home team, length, attendance, player of game)
  * Ability to update or delete
  * Button to add a new log
* New game log:
  * Fields for everything
  * Have the player field be an autocomplete that shows (first name, last name, current team/retired)
  * Have a checkbox to exclude retired players from search
  * Need a plus sign next to the search box that opens a modal with player name starting with current
    search results and then fields for start year and team and ootp id where saving successfully,
    will close the modal and set the autocomplete selected to the new player
* Person list
  * List of players paginated, sortable, and filterable
  * Ability to delete/update/mark as retired
  * Button to add a new player which can use the same modal as the one from the new game log
  