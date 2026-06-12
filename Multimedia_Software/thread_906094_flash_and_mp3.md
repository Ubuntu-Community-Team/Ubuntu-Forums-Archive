---
title: "flash and mp3?"
date: 2008-08-31
forum: Multimedia Software
---

### Post by shao on 2008-08-31
Hey guys first and foremost let me say, I'm a newbie to Linux and I love It!!!
Except for one little issue I have, you see when I start my computer let's say I watch a video, after that I can't listen to mp3's or if I listen to my music after that I cant watch flash videos.

I have Ubuntu Hardy 64 and a HPdv6000

---

### Post by tuskenraider on 2008-08-31
yeah i have noticed if you go to a site like youtube.com in firefox and then try to use another application like pidgin or a mp3 player the sound doesnt work. i have found that if you close firefox... the sound returns..  idk why it does this.. but it just does.. oh and this was for 8.04.1 fully updated.  one of the strange oddities that is ubuntu.

tusken

p.s its still better than windoze or a sharp stick in the eye!! :lolflag:

---

### Post by minky311 on 2008-08-31
When both of you go to system->preferences->sound what is selected as your playback device in all of those fields.

---

### Post by shao on 2008-08-31
Alsa

---

### Post by wolfen69 on 2008-08-31
```
sudo apt-get install libflashsupport
```

---

### Post by minky311 on 2008-08-31
Press Alt and F2 type in gstreamer-properties and then press run.
Then proceed to change the device and press test to see if you can hear anything. If you can then try opening up more than one program playing sound and see if that works. Repeat this with each device listed.

---

### Post by tuskenraider on 2008-08-31
> **minky311 said:**
> Press Alt and F2 type in gstreamer-properties and then press run.
Then proceed to change the device and press test to see if you can hear anything. If you can then try opening up more than one program playing sound and see if that works. Repeat this with each device listed.


:):) and presto change-o it now works for me!!!!! 
yay!! i changed from autodetect to alsa... and now i can youtube and use pidgin.  yay!!!  

such a minor thing... sound.... but when it doesnt work its annoying..  i appreciate the help!!

---

### Post by emshains on 2008-09-01
I've never experienced any sound glitches with firefox/flash, thought this may occur when you open Rhythmbox at the startup.

---

