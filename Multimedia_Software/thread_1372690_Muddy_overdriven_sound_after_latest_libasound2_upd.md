---
title: "Muddy overdriven sound after latest libasound2 update"
date: 2010-01-04
forum: Multimedia Software
---

### Post by junglist313 on 2010-01-04
I have logitech z2300 THX speakers, they sound great, normally. Today I ran the update manager and updated the following packages:

gcalctool (5.28.1-0ubuntu1) to 5.28.2-0ubuntu1
gnome-screensaver (2.28.0-0ubuntu3.1) to 2.28.0-0ubuntu3.2
lib32asound2 (1.0.20-3ubuntu6) to 1.0.20-3ubuntu6.1
libasound2 (1.0.20-3ubuntu6) to 1.0.20-3ubuntu6.1
libasound2-dev (1.0.20-3ubuntu6) to 1.0.20-3ubuntu6.1
libpq-dev (8.4.1-1) to 8.4.2-0ubuntu9.10
libpq5 (8.4.1-1) to 8.4.2-0ubuntu9.10
tzdata (2009s-0ubuntu0.9.10) to 2009u-0ubuntu0.9.10
tzdata-java (2009s-0ubuntu0.9.10) to 2009u-0ubuntu0.9.10

Now I get muddy, overdriven crappy sound, especially on the right channel for some reason. I have tried plugging in the speakers to my mp3 player and they still sound great, so it's not that the speakers are blown or going bad but that's exactly what it sounds like. Had no issues until these updates were applied. Using 9.10 64bit. I have tried ```
$ pulseaudio -k
$ alsa reload
```

And that seemed to imporve the sound quality somewhat, but not to it's original state. I have not changed any settings or anything, just these updates. 

Any ideas?

---

### Post by junglist313 on 2010-01-04
Just doing some more poking around and I have realized that it seems to be music specific. Oddly enough, if I play a .avi in Totem, it sounds fine. But if I play an .mp3 or .ogg file in Totem it sounds like utter trash. Same with several other music players, but to varying degrees. For instance, Totem is the worst, overdriven, awful sound, muddy and crackles even. VLC is earshattering loud, I have to turn the volume down to about 2% to get normal sound. mocp is missing most of the volume issues of the other two, but still sounds muddy and slightly distorted. System volume is set at base 63% or -12db according to the volume applet in the tray. This is very strange. :confused:

---

### Post by junglist313 on 2010-01-05
Bump

---

### Post by imjafo on 2010-01-05
junglist: I had the same problem with my altec-lansing THX speaker system. I opened the terminal and entered "alsamixer", when the mixer opens, I used the arrow keys to reduce the gain to 90% on each of the mixer levels. Use the arrow keys to move to the right or left, and up and down. I reduced all the inputs to 90%. Start with Master and work your way to the right. Go way to the right as there are several off to the right side of the screen. Then hit the escape key to exit the mixer and close the terminal. This solved the overdriven, muddy sound issues for me in 9.04 and 9.10. After that my sound was good, and I have had no further issues.
Hope this helps.

---

### Post by junglist313 on 2010-01-05
I will try this when I get home. Thanks!

---

### Post by junglist313 on 2010-01-05
Winner winner chicken dinner! For some reason all my levels are way out of wack now. In alsamixer i put the master volume level at 70%, but in the volume control app in the panel it shows that it's at about 23%. Weird. Thanks a million for you help! :)

---

### Post by imjafo on 2010-01-05
Gotta love when a plan comes together. I am glad that it worked for you. My audio level in 9.10 (64 bit) shows at 78% or -6.40db, but in the mixer it is 90% across the board. In 9.04 32bit, it is 90% in the mixer and -7ish db at 80% on the volume control.
Happy to be of help. I guess you can mark this as solved.

---

