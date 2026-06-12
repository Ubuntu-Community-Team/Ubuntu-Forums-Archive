---
title: "problems with camara"
date: 2007-03-26
forum: Multimedia &amp; Video
---

### Post by Tread2007 on 2007-03-26
Alright, I'm trying to get video footage off my Canon Elura 100. Everytime i connect it to its firewire, nothing happens. Any suggestions?

---

### Post by Tread2007 on 2007-03-27
when i try to run gscanbus, i get this:

trevor@trevor-desktop:~$ gscanbus
couldn't get handle: Permission denied
This probably means that you don't have raw1394 support in the kernel or that
you haven't loaded the raw1394 module.
trevor@trevor-desktop:~$


Can any1 help me understand this please?

Also my camera uses MiniDV's and connects with firewire, if that helps solve the problem

---

### Post by fenian on 2007-03-27
Try this ffrom a terminal...

> 
sudo lsmod | grep 1394
you  should see the modules ieee1394, ohci1394, raw1394, video1394, dv1394 listed if not enter in terminal...

> sudo modprobe [modulename]

replace modulename with the missing module name (i.e. , ieee1394)

Finally add read/write permission for user with the command...

> sudo chmod 0666 /dev/raw1394

---

### Post by Tread2007 on 2007-03-27
Thanks, but still nothing.

I tried, {sudo chmod 0666 /dev/raw1394} but nothing happened. Is there any thing I can try?

---

### Post by fenian on 2007-03-27
Try 

> sudo chmod a+rw /dev/raw1394

---

### Post by Tread2007 on 2007-03-27
i tried that and all i got was:

trevor@trevor-desktop:~$ sudo chmod a+rw /dev/raw1394
trevor@trevor-desktop:~$

nothing loaded or happened

---

### Post by fenian on 2007-03-27
sorry typo try

> sudo chmod g+rw /dev/raw1394

---

### Post by Tread2007 on 2007-03-27
oh, ok. well, this time it asked me for my password. i typed it in and it went back to trevor@trevor-desktop:~$


is that what it was suppose to do?

---

### Post by fenian on 2007-03-27
Yes.Do you have a program installed to grab the video?If not you need to install one kino works well install it with...
> 
sudo apt-get install kino

read more about it [here]("http://www.kinodv.org/docbook/") and [here]("http://www.yourmachines.org/tutorials/kino.html")

---

### Post by Tread2007 on 2007-03-27
I already had Kino installed. At the bottom of the Kino window it says WARNING: dv1394 kernel module not loaded or failure to read/ write /dev/dv1394/0

Any other ideas?

---

### Post by fenian on 2007-03-27
What is the output from

> sudo lsmod | grep 1394

?

---

### Post by Tread2007 on 2007-03-27
Here's what i got:

trevor@trevor-desktop:~$ sudo lsmod | grep 1394
video1394              20300  0
dv1394                 21196  0
raw1394                30956  2
ohci1394               35124  2 video1394,dv1394
ieee1394              299832  5 video1394,dv1394,raw1394,sbp2,ohci1394
scsi_mod              139496  6 sg,sd_mod,sr_mod,sbp2,usb_storage,libata
trevor@trevor-desktop:~$


I don't know how, but Kino does detect the camera. I went to preferences, and clicked the ieee 1394 tab. and in the av/c device slot it says "Canon Elura 100". So thats a step in the right direction, right?

---

### Post by fenian on 2007-03-27
If it sees the camera it should be able to grab the video there are some instructions [here]("http://www.yourmachines.org/tutorials/kino.html")

---

### Post by Tread2007 on 2007-03-27
oh, awesome. i'm able to control the camara from the computer. Thanks a lot, man. Really appreciate it. If anything else comes up, I'll hit the forum again

---

