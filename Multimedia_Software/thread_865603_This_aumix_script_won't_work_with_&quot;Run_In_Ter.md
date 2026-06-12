---
title: "This aumix script won't work with &quot;Run In Terminal&quot;"
date: 2008-07-20
forum: Multimedia Software
---

### Post by YAOMTC on 2008-07-20
I have here an aumix script I got from Whiffle last year (it toggles the headphones between muted and unmuted):
```
#\bin\bash
       aumix -Wq |grep -q 100
        if [ $? == 0 ]; then
          aumix -W mute
       else
          aumix -W 100
        fi
```
When I open up a terminal and enter ./headphones.sh, the script works. However, if I go to the script in Nautilus and try Open in Terminal, it doesn't do anything. When I set it as Application in Terminal for a panel launcher, it only unmutes, and won't mute. Does anyone know why this might be?

---

### Post by YAOMTC on 2008-07-21
Bump 1/&#8805;7

---

### Post by YAOMTC on 2008-07-22
Bump 2/&#8805;7

---

### Post by YAOMTC on 2008-07-23
Bump 3/&#8805;7

---

### Post by mcduck on 2008-07-23
The "Open in terminal" is not for running scrpits or anything. It simply opens the loaction you are browsing with Nautilus in a terminal.

If you want to run the scipt from Nautilus it should be possible simply by double-clicking the script.

---

### Post by YAOMTC on 2008-07-23
So there's no way of running a script from the top panel?

---

### Post by YAOMTC on 2008-07-23
Bump 4/&#8805;7

---

### Post by mcduck on 2008-07-23
For the launcher, set the type to "application in Terminal" (or whatever it was..), although the script should work even without that, you just can't see anything happening without the terminal window..

---

### Post by YAOMTC on 2008-07-23
For some reason, as an "Application in Terminal" will only *unmute* the headphones, whereas if I go into a terminal and enter ./headphones.sh, it'll do *both* mute and unmute.

---

### Post by YAOMTC on 2008-07-23
Bump 5/&#8805;7

---

### Post by YAOMTC on 2008-07-24
Bump 6/&#8805;7

---

### Post by YAOMTC on 2008-07-27
Bump 7/&#8805;7

Last bump.

---

