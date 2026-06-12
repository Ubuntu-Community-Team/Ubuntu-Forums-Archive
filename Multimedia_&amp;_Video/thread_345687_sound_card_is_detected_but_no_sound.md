---
title: "sound card is detected but no sound"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by milux on 2007-01-24
hello all,

i am new to ubuntu.  i just successfully installed the xubuntu in my laptop.  everything seems to work fine except the sound.  the sound card is detected, but there is no sound.  i am also umuted 'alsamixer'.   do am i missing something here? all comments are appreciated...

#aplay -l
list of PLAYBACK Hardware Devices 
card 0: I82801CAICH3 [INTEL 82........] device 0: Intel .......

#lspci -v | grep -i audio
00:1f.5 Multimedia audio controller: Intel Corporation 8281......

---

### Post by deadgobby on 2007-01-24
What is your lap top? 
GObby

---

### Post by milux on 2007-01-24
ibm thinkpad t23

---

### Post by Screevo on 2007-02-09
Hey, I just installed Ubuntu on a T23 last night, and for some reason, sound seems to boot up as muted. Make sure that you unmute the sound using the thinkpad buttons up top, and make sure that you also have all the thinkpad specific packages installed.

---

