---
title: "Sound not working on 24&quot; iMac (Early 2009)"
date: 2009-11-02
forum: Multimedia Software
---

### Post by FirstNameRyan on 2009-11-02
I'm very new to Ubuntu and linux in general. I've just installed Ubuntu 9.10 and it's working great so far I've updated the drivers and everything, but my sound still isn't working. I can adjust the volume from my keyboard and it notifies me in the top right of screen but there isn't any sound when I go to YouTube or anything.

---

### Post by FirstNameRyan on 2009-11-04
This is awesome no responses yet.

---

### Post by bananasareformonkeys on 2009-11-21
Try opening the terminal and open /etc/modprobe.d/options:
sudo nano /etc/modprobe.d/options
and add "options snd-hda-intel model=imac24" to the file and save ( ctrl+o and then ctrl+x to exit )
then reboot.

If you're still having trouble or the mic doesn't work or something, try writing mbp3 instead of imac24.

---

### Post by at2guch2 on 2009-11-22
Hi,
I had the exact same problem, follow the steps from bananasareformonkeys.

Reboot, opening the terminal and launch without admin rights "alsamixer" last on the right you have the number of channels, after setting it from 2 Ch to 4 Ch I got the sound working.

I hope this will work for you.

---

### Post by oneiric on 2009-11-23
you have to change the alsa-base.conf file which is located in /etc/modprobe.d

to do this,

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

then scroll down to the end of the file and add the line

options snd-hda-intel model=mbp3

save, and restart computer

if that doesn't work, then repeat the process try instead the line

options snd-hda-intel model=imac24

---

