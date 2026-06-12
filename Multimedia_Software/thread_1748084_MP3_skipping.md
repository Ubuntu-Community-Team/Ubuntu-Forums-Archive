---
title: "MP3 skipping"
date: 2011-05-03
forum: Multimedia Software
---

### Post by Condor Cluster on 2011-05-03
I have noticed that some of my music albums have tracks that 'skip' or 'crackle' when played on my netbook. They sound the same played with VLC and Banshee. 
I then tried those albums on an mp3 player I had lying around, and some of those albums sounded okay, but some were still fubar.
 
Question is, could this be a codec problem, that certain mp3's might have difficulties with?
 
Also, is there a program that I could use to scan my entire music collection, and highlight those tracks that are borked?
 
Thankyou
 
8)

---

### Post by Condor Cluster on 2011-05-04
UPDATE: seems to be doing it with video files now aswell. Could be linked to some recent updates I've done, possible the new Lucid kernel version...

---

### Post by lidex on 2011-05-04
Try resetting your pulse configuration.
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* ~/.pulse-cookie 
sudo rm /etc/asound.conf
```
**Reboot**
* Ignore any 'No such file or directory' errors*

---

### Post by Condor Cluster on 2011-05-06
So far, it seems resetting PulseAudio may have done the trick.

Thanks

---

### Post by Condor Cluster on 2011-05-16
This problem seems to crop up again occasionally.
 
Not sure if it is the current kernel patch, or just that pulse audio is poo. 
 
:(

---

### Post by Condor Cluster on 2011-05-19
Right, it's getting on my nerves now.

Okay, I ran ```
sudo apt-get remove pulseaudio gstreamer0.10-pulseaudio
``` and rebooted.

Seems like it wiped pulseaudio off my system, but now I have no way to change volume.

How do I get the menu bar applet and keyboard shortcuts back with alsa?

Much thanks.

---

### Post by lidex on 2011-05-20
This help at all:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by Condor Cluster on 2011-05-20
I added the ppa from your link ([http://ppa.launchpad.net/dtl131/ppa/ubuntu](http://ppa.launchpad.net/dtl131/ppa/ubuntu)), then updated and downloaded all the packages from it.

Next, I rebooted my machine, then added volume control to the menu bar. Keyboard shortcuts etc now all work as before with pulseaudio (just looks a bit out of place theme wise though...)

Seems to have done the trick, thanks :)

EDIT: managed to get mupen64plus working again by installing libsdl1.2debian-alsa (which in turn removed an old pulse package. weird.

---

