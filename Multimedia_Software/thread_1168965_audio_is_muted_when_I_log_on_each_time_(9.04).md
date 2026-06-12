---
title: "audio is muted when I log on each time (9.04)"
date: 2009-05-24
forum: Multimedia Software
---

### Post by frankwakeman on 2009-05-24
I've just put Xubuntu 9.04 on my Acer Aspire One netbook.  The only problem I've found is I have to unmute the sound each time I put the computer on.  Has anyone found this, on this or any computer and is there  anything simple to do to sort it?

Thanks.

---

### Post by MarcDam on 2009-05-29
I had the exact same problem...
use alsamixer to set your settings
```
alsamixer
```
then go into root and store your alsa settings
```
sudo -i
alsactl store
exit
```
Then you just have to make sure that the following command is run on every boot
```
alsactl restore
```
And then your problem should be fixed :)

---

### Post by fillintheblanks on 2009-05-29
or you could run this command in your startup applications

> amixer sset 'Master',0 playback 75

this will set the master channel volume to 75% everytime

> amixer scontrols shows you all the available channels

---

### Post by extigyro on 2009-05-31
I'm having the same issue. 
The strange thing is that the bug is actually marked as SOLVED. However, i'm experiencing it at every reboot (my system is fully updated).

---

