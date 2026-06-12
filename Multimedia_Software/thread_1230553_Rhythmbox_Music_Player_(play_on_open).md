---
title: "Rhythmbox Music Player (play on open)"
date: 2009-08-03
forum: Multimedia Software
---

### Post by pqwoerituytrueiwoq on 2009-08-03
Is there a play on application start up?
and if so where?


Edit:
best solution i can come up with 
**Warning: This script will run till the cows come home or rhythmbox opens whichever comes first** (if you are not familiar with the phrase *till the cows come* home it mean forever)
```
#!/bin/sh
# Make sure rhythmbox is open
while [ 0`pidof rhythmbox` -eq 0 ]; do
        sleep 2 
done
# Now lets hope the song is not actually named "Not playing"
# Loop is cause it likes to be stubborn my guess is
# rhythmbox is open but not ready to play sometimes.
while [ "`rhythmbox-client --print-playing`" = "Not playing" ]; do
        rhythmbox-client --play
        sleep 2
done
```i run it through my login sound 
edited login sound in startup applications to run this script
```
#!/bin/sh
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
# Make sure rhythmbox is open
while [ 0`pidof rhythmbox` -eq 0 ]; do
        sleep 2 
done
# Now lets hope the song is not actually named "Not playing"
# Loop is cause it likes to be stubborn my guess is
# rhythmbox is open but not ready to play sometimes.
while [ "`rhythmbox-client --print-playing`" = "Not playing" ]; do
        rhythmbox-client --play
        sleep 2
done
```

---

### Post by pqwoerituytrueiwoq on 2009-08-07
Anyone?

---

### Post by pqwoerituytrueiwoq on 2009-08-22
dont make me quote my self

---

### Post by Major_Kong on 2009-08-22
> **pqwoerituytrueiwoq said:**
> Is there a play on application start up?
and if so where?

Good question, there's nothing in the options dialog and running rhythmbox help-all doesn't show any such option...

EDIT:

You could use rhythmbox-client to start the audio after rb opens... Write "rhythmbox-client --help" in the console to view the avaliable options.

---

### Post by pqwoerituytrueiwoq on 2009-08-23
FINALLY A REPLY!!!!
i have even tried a program i made (3 lines) to start it and play
```
#!/bin/sh
rhythmbox %U
rhythmbox-client --play
```i have also tried ```
sleep 15
``` in between the commands
i put 
```
rhythmbox %U
```in start up
and use a shortcut key to start it now

if this were windows i would have made
file.bat
```
start rhythmbox %U
nircmd wait 10000
rhythmbox-client --play
```

nircmd is a command line utility i downloaded
10000 is in milliseconds

---

### Post by Major_Kong on 2009-08-23
In alternative you could try writting a plugin for rb.

---

### Post by pqwoerituytrueiwoq on 2009-08-23
> **Major_Kong said:**
> In alternative you could try writting a plugin for rb.
would not know where to start 
i never even fully learned dos and just looked at (not even sure what language that it) just yesterday

---

### Post by Major_Kong on 2009-08-25
> **pqwoerituytrueiwoq said:**
> would not know where to start 
i never even fully learned dos and just looked at (not even sure what language that it) just yesterday

Drop by the IRC channel and talk to the devs. One of them might be open to the idea.

---

### Post by Panama2305 on 2010-06-25
I found a way to do this...

Recently I made a script to run Rhythmbox (RB) and CoverGloobus (CG) at the same time and close both when I close RB. I made this, cuz I did not want to open RB and then CG, was a waste of time for me :lolflag:. So, I made it and was running well, but today I want my RB run on startup and play my last song, but my script just run RB, but didn't play :confused:. Finally I did it well and the solution is this one: :popcorn:

:KS Install "Resume on start" plugin on RB. You can download from here [http://people.ksp.sk/~mic]("http://people.ksp.sk/%7Emic"). This is just to play the last song played last time, so your RB will resume your playlist.

:KS Run this script at startup:
```

#!/bin/bash
sleep 10
rhythmbox-client --play-pause
```:KS And also this one (if you have CoverGloobus, otherwise just add rhythmbox %U to startup)
```

#!/bin/bash
python /usr/share/covergloobus/covergloobus.py &
covergloobusPID=$!
rhythmbox %U
kill $covergloobusPID
```I hope this help you... :guitar:

---

### Post by pqwoerituytrueiwoq on 2010-09-14
So i tried making a plugin
put it in here:
$HOME/.gnome2/rhythmbox/plugins/

it is not working and there are no errors any idea on how to make it work
i looked at other peoples source to try to see how to send the play command

i attached my plugin
if anyone can make it work...
i am not familiar with python

---

