---
title: "Very low sound in Karmic"
date: 2009-12-22
forum: Multimedia Software
---

### Post by stevebond001 on 2009-12-22
Hi
My default installation of 64 bit Karmic has really low sound (with the previously installed version the sound was fine)

Can anyone give me any clues as to what to do to increase the sound?

Many thanks in advance

---

### Post by stevebond001 on 2009-12-24
Anyone??

---

### Post by RedSingularity on 2009-12-24
In a terminal type 

alsamixer

and adjust the sound level there.

---

### Post by stevebond001 on 2009-12-24
Hi
Thanks for that but all levels are at their maximum.  Any other ideas?

---

### Post by RedSingularity on 2009-12-24
In a terminal try this

gnome-volume-control

---

### Post by stevebond001 on 2009-12-30
Thanks for that.  However, this just opens the sound applet.  I can adjust the master volume to 150% but it distorts the sound.
The main problem I have is that the sound is just too low, even when set to maximum volume.  I understand that this is an issue with Karmic but I still haven't fathomed out how to fix it.

Any other suggestions would be welcome.

---

### Post by sigurnjak on 2010-01-01
[http://www.webupd8.org/2009/08/increase-maximum-sound-level-in-ubuntu.html](http://www.webupd8.org/2009/08/increase-maximum-sound-level-in-ubuntu.html)

Try this , it worked well for me after reboot .

---

### Post by stevebond001 on 2010-01-04
Hi
Thanks for the advice but it made no difference to my sound.

Is this hardware specific or should it work on any PC?

---

### Post by sigurnjak on 2010-01-04
No ,i do not think so . However , you may try this , i forgot to mention it :[http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html](http://www.webupd8.org/2009/11/ubuntu-karmic-upgrade-alsa-to-1021-from.html)

---

### Post by stevebond001 on 2010-01-05
Hi
Thanks very much for the link.  I followed the instructions and it made a slight difference.  I am now able to listen to my music (albeit very low) but my podcasts are still very low.  I can listen to them but I need to adjust the volume output to 150%.
I think that this is the best I'll get until an inbuilt patch for this issue is included (hopefully in the next release)

Many thanks once again.

---

### Post by trash on 2010-01-06
THANKS!! Worked on my Toshiba:D

> **sigurnjak said:**
> [http://www.webupd8.org/2009/08/increase-maximum-sound-level-in-ubuntu.html](http://www.webupd8.org/2009/08/increase-maximum-sound-level-in-ubuntu.html)

Try this , it worked well for me after reboot .

---

### Post by sigurnjak on 2010-01-07
You are most welcome friend !;)

---

