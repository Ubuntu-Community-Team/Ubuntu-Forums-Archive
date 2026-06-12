---
title: "Problems with Logitech QuickCam E2500 on 8.10"
date: 2009-01-02
forum: Multimedia Software
---

### Post by nischni on 2009-01-02
I'd like to install a Logitech QuickCam E2500 on ubuntu 8.10, but I didn't really know what to do. 
I've found this manual: 
[http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/)
because the patch-File, used on this page, produced an error (the file gspca.ko wasn't created, I tried it with the patch-File from:
[http://ubuntuforums.org/showthread.php?t=966932&highlight=e2500](http://ubuntuforums.org/showthread.php?t=966932&highlight=e2500)
So I typed:

[INDENT]tar -xvf gspcav1-20071224.tar.gz
tar -xvf patch.tar.gz
cd gspcav1-20071224
patch < ../gspca.patch

sudo rmmod gspca
sudo modprobe -v gspca[/INDENT]

this creates: insmod 
/lib/modules/2.6.27-7-generic/kernel/media/gspca.ko

So I further typed:

[INDENT]sudo rmmod gspca
sudo rm /lib/modules/2.6.27-7-generic/kernel/media/gspca.ko
sudo mv gspca.ko /lib/modules/2.6.27-7-generic/kernel/media/
sudo modprobe gspca[/INDENT]

and now there should be a video device, but I can't find anything like that. No /dev/video0!!!!

What can I do? If there is a any thread, that may help me, I would me glad to know. I must add, that I'm new on ubuntu and Linux, and that I don't really know, what I type ;-).

Thanks

---

### Post by nischni on 2009-01-07
Can't anybody help me? Have I done anything wrong? Should the Webcam be connected with the computer? Where should I unpack the tar-Files?

Pleeeease help me!

---

### Post by pobloke on 2009-01-07
I'm trying to do excatly the same thing on 8.10 but I get:

ERROR: Module gspca does not exist in /proc/modules

when I type 

sudo rmmod gspca
sudo modprobe -v gspca

Can anyone help?

---

### Post by Spr0k3t on 2009-01-08
I had the exact same problems with the E2500.  I got so fed up with the results that I finally gave in and replaced the E2500 with a 9000 Pro.

---

