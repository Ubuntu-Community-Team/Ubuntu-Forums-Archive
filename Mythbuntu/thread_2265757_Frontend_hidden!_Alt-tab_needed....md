---
title: "Frontend hidden! Alt-tab needed..."
date: 2015-02-17
forum: Mythbuntu
---

### Post by dibuntux on 2015-02-17
Dear all, I cannot get out of this...after upgrading from 12 to 14 all is ok but... Frontend appears "hidden"...I can see the standard background with grey lines of the Mythbuntu theme, but no menus...Alt-tab and all is shown correctly...tried to put a timing in the frontend starting, no good.
If I exit the frontend and startit again everything is right with no need for an Alt-Tab, which is very annoying to give at the keyboard when you are already on the sofa...
How can I get out of this situation?

Thank you all in advance...

---

### Post by kpatz on 2015-02-17
I found turning on MythWelcome seemed to fix this for me.

---

### Post by khPWXxF on 2015-02-18
I wonder whether this is related to this bug?
  [https://bugs.launchpad.net/mythbuntu/+bug/1181335](https://bugs.launchpad.net/mythbuntu/+bug/1181335)
   
  1.  What are your settings for FE setup > appearance > Theme/Screen GUI sizes?
  Does it get fixed if you zero them?
   
  2.  Does it get fixed if you do a DISPLAY (see below)?  On my system it needs to be run after frontend has started so I spawn a job.
   
  Change /usr/bin/mythfrontend (a link) to add a line after the check_groups line like this:
  ```
/usr/bin/fullscreen.sh&
```
   
This will to spawn off a job:  /usr/bin/fullscreen.sh.
   
  ```
[FONT=&amp]#!/bin/bash[/FONT]
  [FONT=&amp]#get rid of junk at top of screen[/FONT]
  [FONT=&amp]#this script called from /usr/bin/mythfrontend[/FONT]
  
  [FONT=&amp]sleep 10[/FONT]
  [FONT=&amp]DISPLAY=:0 wmctrl -r "MythTV Frontend" -b add,fullscreen[/FONT]
  [FONT=&amp]exit[/FONT]
```
   
hth
  Phil

---

### Post by dibuntux on 2015-02-19
aha..that is the problem...Mythwelcome is running and not configured...I modified mythtv.desktop in .config/autostart to run mythwelcome, and I can see the other job running. It does work, and displays Frontend correctly...but then I have Mythwelcome, which I do not want...I do I get rid of it and whotever ghost process I may have running?

---

