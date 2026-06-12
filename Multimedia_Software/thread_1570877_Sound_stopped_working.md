---
title: "Sound stopped working?"
date: 2010-09-08
forum: Multimedia Software
---

### Post by ericrcan on 2010-09-08
Hey there everyone. I am new to ubuntu (and new to linux) and am really having some fun with it. I have a Toshiba NB205 netbook and installed Ubuntu 10.4 lts on it and everything was working fine. The bluetooth, sound, wifi, everything! Now yesterday the sound stopped working all of a sudden... I can put in headphones and listen to it, but even in the headphones it sound terrible. It speeds up and slows down and skips. Anyone have any idea how to fix this? I tried updating using ```
System> Administration>Update Manager
``` and I also tried ```
sudo apt-get update
``` but to no avail.. Like I said, I am new so I do not really know the terminal (switching from windows, I know some DOS), but I am ready to learn. Any help would be great!

---

### Post by tommcd on 2010-09-08
Did you install Ubuntu on the Toshiba using Wubi? Or did you do a real Ubuntu install to a linux partition on your hard drive?
Anyway, try adding:
```
options snd-hda-intel model=asus-mode4
```
to your: */etc/modprobe.d/alsa-base.conf* file. Reference:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks/ToshibaNB205)
Fist, back up the file for safety. Open a terminal and run:
```
sudo cp /etc/modprobe.d/alsa-base.conf /etc/modprobe.d/alsa-base.conf.orig
```
Then to edit the file, use an easy text editor like **gedit**. Form the terminal run:
```
gksudo gedit /etc/modprobe.d/alsa-base.conf 
```  
This will open the alsa-base.conf file with super user write access using the gedit text editor. Then just add *options snd-hda-intel model=asus-mode4* to the end of the file by starting a new line right after the last line. Save the file and then reboot.
After rebooting, run **alsamixer** in the terminal and move all the volume levels up using the arrow keys. If any levels have a "m" below them, it means they are muted. Unmute them by toggling the "m" key. Hit the Esc key to exit alsamixer.
Hope this helps.
If this fails, others have reported getiing sound to work on your netbook by installing OSS:
[http://ubuntuforums.org/showthread.php?t=1203480](http://ubuntuforums.org/showthread.php?t=1203480)
But lets try the simple stuff first!

And welcome to the Ubuntu forums!

---

### Post by ericrcan on 2010-09-08
I installed it using the normal Ubuntu Desktop edition. I put it on a flash drive and formatted a partition on my hd and installed it. It is just kind of strange because the sound was working fine, then all of a sudden it only plays through the headphones. I will try the OSS method, but its pretty involved, so I will try it later tonight.

*edit*
Of course as soon as I post I find a way to fix it, even though I have been looking through these issues for a few months.. lol. I did this and now it works like a charm! Thanks for you help :)

```
sound:
edit /etc/modprobe.d/alsa-base.conf
put-> options snd-hda-intel index=0 model=auto

```

---

### Post by tommcd on 2010-09-09
> **ericrcan said:**
> 
Of course as soon as I post I find a way to fix it, even though I have been looking through these issues for a few months.. 

edit /etc/modprobe.d/alsa-base.conf
put-> options snd-hda-intel index=0 model=auto

Glad you fixed it. Just out of curiosity, where did you find that option for alsa-base.conf? The only one I found was in the link I gave in my last post.

---

### Post by ericrcan on 2010-09-09
I dont know how I missed it before (I literally looked through hundreds of pages about nb205 and sound), but I found it here:```
http://ubuntuforums.org/showthread.php?t=1522913#post9547125
```

---

