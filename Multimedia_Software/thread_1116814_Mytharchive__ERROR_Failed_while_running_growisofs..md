---
title: "Mytharchive:  ERROR: Failed while running growisofs.  Result 144"
date: 2009-04-05
forum: Multimedia Software
---

### Post by Committed on 2009-04-05
I'm almost there with Mytharchive but can't get past this problem.  Here's a screenshot.  Also, where is the README it talks about. 


[IMG]http://img.photobucket.com/albums/v298/Danceswithtrees/Screenshot.png[/IMG]

---

### Post by Committed on 2009-04-05
Some more info from end of log file:

STAT: fixed 1 VOBUS                         
Finished  dvdauthor
Burning ISO image to /dev/scd0
growisofs -dvd-compat  -Z /dev/scd0 -dvd-video -V "UGN News at 5:30" /home/scott/mythtemp/work/dvd
Running growisofs to burn DVD
FATAL: /dev/scd0 already carries isofs!
------------------------------------------------------------
ERROR: Failed while running growisofs.
Result 144, Command was: growisofs -dvd-compat  -Z /dev/scd0 -dvd-video -V "UGN News at 5:30" /home/scott/mythtemp/work/dvd
Please check the troubleshooting section of the README for ways to fix this error
------------------------------------------------------------

Terminated

---

### Post by Committed on 2009-04-05
Well Ive got it working.  I had to use gnomebaker to force format the dvd+rw.  It was not empty.  Shouldn't Mytharchive have erased it?  I'm going to try again with the same dvd with the show I just recorded still on it since what was on it was data previously recorded to it by gnombaker.  Maybe just maybe.

---

### Post by Committed on 2009-04-05
Duh! I had single layer DVD selected instead of DVD+/-RW which gave me the erase DVD option. :redface:  

Maybe this will help somebody in the future.

---

### Post by AlecJ on 2009-05-05
Thank you, I had the same problem.

---

