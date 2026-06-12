---
title: "SBLive 5.1 External only front speakers -  Only &quot;PCM&quot; slider in gnome-alsamixer"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by carpediem1337 on 2007-10-06
Whenever I go to gnome-alsamixer to raise my rear & center PCM volume (in the USB Audio tab), the only slider there is just "PCM."  So obviously, I get no sound out of my rear/center speakers.  Any ideas?

---

### Post by Jukkis on 2007-10-06
Open the terminal and give command:

alsamixer

Window with many different sets will open. You can choose the item by using left/right arrow.  At the bottom are the descriptions of the items (also above the screen with details) you would like to set. If there is "mm" in the bottom of the parameter, it means it is not in use. First press "m" to set it on , then press up/down arrows to increase/decrease the "volume" of the item.

Usually the values of the item are from 0-100. Do no set it to high... about 70 is nice. 

Greetings from Finland

Jukkis :)

---

### Post by carpediem1337 on 2007-10-08
I have tried that (with the -c 1 command to edit the volumes of my USB SBLIve card) and still the only bar that shows up is just "PCM."

---

