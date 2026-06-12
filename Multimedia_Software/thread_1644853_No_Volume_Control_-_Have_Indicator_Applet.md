---
title: "No Volume Control - Have Indicator Applet"
date: 2010-12-13
forum: Multimedia Software
---

### Post by HKJGN on 2010-12-13
So i've noticed people having trouble with thier sound control saying they need to have the Indicator Applet up, well i already do and it's still missing.

i usually have to remove Pulse Audio due to applications that it interferes with, but apparently it's built into Ubuntu, since when i remove it, this happens, and the sound server doesnt respond

well i reinstalled it but i still see no Volume Control, even after restart, Help? X.x

---

### Post by tommcd on 2010-12-13
> **HKJGN said:**
> 
i usually have to remove Pulse Audio due to applications that it interferes with, but apparently it's built into Ubuntu, since when i remove it, this happens, and the sound server doesnt respond

If you want to remove pulseaudio (and well you should, because it is a huge bloated resource hog) just do this:
```
sudo apt-get remove --purge pulseaudio gstreamer0.10-pulseaudio
```
Then run **gstreamer-properties** and set everything to alsa.
You can use **alsamixer** in the terminal to control volume levels. If you want a GUI to control volume then install 
**gnome-alsamixer**.

---

### Post by HKJGN on 2010-12-14
that didnt really return my volume control on Indicator Applet though... i kinda like having the volume control up there for quick usage, is there any other way?

---

### Post by tommcd on 2010-12-14
> **HKJGN said:**
> that didnt really return my volume control on Indicator Applet though...
I did not say it would return the volume applet. I just offered up a way you can easily control the volume with either alsamixer or gnome-alsamixer.
As for alternatives, see this thread:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8284273)
I know that is a very long thread, but there are many suggestions there about dealing with the removal of pulseaudio.

---

