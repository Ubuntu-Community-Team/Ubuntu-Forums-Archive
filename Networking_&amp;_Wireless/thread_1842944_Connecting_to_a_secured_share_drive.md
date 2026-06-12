---
title: "Connecting to a secured share drive"
date: 2011-09-12
forum: Networking &amp; Wireless
---

### Post by jeffbartelli on 2011-09-12
[FONT=Arial][SIZE=2]My school offers a shared drive for students to access their files away from class.  They give directions for connecting to this server for Windows and Mac but not for linux.  I'm posting the instructions below for both in the hopes that somebody can translate them for me:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
**[FONT=Arial][SIZE=2]Windows 7 mapping to your H: drive[/SIZE][/FONT]**

[LIST=1]
[*][FONT=Arial][SIZE=2]Right click the windows orb on the lower left[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Click on Open Windows Explorer[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Click on “Computer” on the left column[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Across the top  menu bar click on “Map Network Drive”[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Select a drive letter, you can choose “H” if it’s not being used[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]For the second line enter **\\asadmin.duke.edu\SSPP\users**
(note backslashes). [/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]You may need to check “connect using different credentials” if your netid is not the same as the account name you use on your personal computer.   For user name enter: **win\netid**[/SIZE][/FONT]
[/LIST]**[FONT=Arial][SIZE=2]Windows 7 mapping to shared space, the G: drive[/SIZE][/FONT]**

[LIST=1]
[*][FONT=Arial][SIZE=2]Right click the windows orb on the lower left[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Click on Open Windows Explorer[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Click on “Computer” on the left column[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Across the top  menu bar click on “Map Network Drive”[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Select a drive letter, you can choose “G” if it’s not being used[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]For the second line enter **\\asadmin.duke.edu\SSPP\shared**
(note backslashes). [/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]You may need to check “connect using different credentials” if your netid is not the same as the account name you use on your personal computer.   For user name enter: **win\netid**[/SIZE][/FONT]
[/LIST]**[B][FONT=Arial][SIZE=2]MAC OS X [/SIZE][/FONT]**[/B]

**[FONT=Arial][SIZE=2][B]Connecting**** to the server with a Mac**[/SIZE][/FONT][/B]

[LIST=1]
[*][FONT=Arial][SIZE=2]Click on “Go” from the finder bar.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Click on “connect to server”[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]On the “Server address” line enter [/SIZE][/FONT]
[LIST]
[*][FONT=Arial][SIZE=2]**smb://bulletrogan.asadmin.duke.edu/sspp-users/<your netid>**
if you want to get to your H: drive[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]**smb://bulletrogan.asadmin.duke.edu/sspp-shared**
if you want to get to shared space[/SIZE][/FONT]
[/LIST]
[*][FONT=Arial][SIZE=2]Click on connect[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]When you are prompted to enter your netid use the syntax:  win\netid[/SIZE][/FONT]
[/LIST][FONT=Arial][SIZE=2]Thanks for any guidance you can offer![/SIZE][/FONT]

---

