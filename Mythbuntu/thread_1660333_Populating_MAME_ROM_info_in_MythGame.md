---
title: "Populating MAME ROM info in MythGame"
date: 2011-01-05
forum: Mythbuntu
---

### Post by IceCap on 2011-01-05
I got sdlmame working reasonably well within MythGame and put handful of ROMs in there to try.  There are several references out there about automatically populating the metadata for the ROMs but I'm not sure which to use.
  I tried the script mame2myth.py and downloaded Catver.ini but when I execute the command to populate the metadata (mysql ...... <./mame2myth.py ) I get an error (looks like mysql doesn't like the variables in the script which doesn't make any sense).

  What are people using to populate the MAME ROM metadata in MythGame?  And I should then also ask for detailed instructions since mame2myth didn't work for me.

  Thanks

  IC

---

### Post by thatguruguy on 2011-01-05
For _recognized_ games in myth .24, I simply select the game I want, press "M" for menu, and then choose "Retrieve Details."

---

### Post by IceCap on 2011-01-05
Sorry, I should have been more specific, I'm using 0.23.1.  I'm assuming that the M doesn't work in 0.23.1?
  I guess that's one reason to switch to 0.24.

  Thanks

  IC

---

### Post by IceCap on 2011-01-07
And some more specifics.  When I run the command

```
mysql -umythtv -ppassword mythconverg < ./mame2myth.py
```
  which (I guess) is supposed to populate the game metadata in mysql with information from Catver.ini (located in the current directory as well as the mame2myth.py script), then I get

```
ERROR 1064 (42000) at line 13: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'FILTER_CLONES = 0

FILTER_MATURE = 1

FILTER_BIOS = 1

SYSTEM = "SDLMAME"

M' at line 1

```

  I'm at a loss, not sure what is going on.  Has anyone any experience with mame2myth.py script?

  Thanks

  IC

---

### Post by IceCap on 2011-01-12
OK I figured it out.  The mame2myth.py script file claimed the following code to populate mysql with the metadata: ```
mysql -u mythtv -p password mythconverg < ./mame2myth.py
```
  However, the script execution doesn't work this way.  Had to split it up into two commands:  ```
./mame2myth.py >output.txt
mysql -u mythtv -p password mythconverg < output.txt
```

  Note that you have to make sure that the variable SYSTEM in the mame2myth.py script has the same value as the game type in MythGame (I had called mine "SDLMAME").

  Hope this helps someone using 0.23.

  IC

---

