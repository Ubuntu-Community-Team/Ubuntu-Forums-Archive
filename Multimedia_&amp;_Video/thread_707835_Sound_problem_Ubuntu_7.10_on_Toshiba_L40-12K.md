---
title: "Sound problem: Ubuntu 7.10 on Toshiba L40-12K"
date: 2008-02-25
forum: Multimedia &amp; Video
---

### Post by cserrano on 2008-02-25
I  installed Ubuntu 7.10 a few weeks ago and I have still not been capable of fixing the sound. I hear this peach and when I play with the volume the sound just stops working. 
I tried prevously posted solutions but none worked on my laptop.
I have a  82801G (ICH7 Family) High Definition Audio Controller (marking "rev02" when I lspci) in a Toshiba Satellite L40-12k running Ubuntu 7.10. Any help please??

---

### Post by linuxwizard on 2008-02-26
Look at bottom of this page in the notes for sound. It may or may not help or you might have already seen it.
[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL40-12K](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteL40-12K)

---

### Post by cserrano on 2008-02-26
Yes. The last line of /etc/modprobe.d/alsa-base is options snd-hda-intel model=3stack, as suggested in that page. However it still doesn't work. 
I wonder if I messed up something while trying other stuff..

---

### Post by linuxwizard on 2008-02-26
That is hard to say if something might have gotten messed up. Not sure if it will help or not but you might try to update to the latest version of ALSA.

---

### Post by cserrano on 2008-02-27
I tried both 1.14 and 1.16 and nothing. The peach is still there. I think it must be a configuration problem

---

