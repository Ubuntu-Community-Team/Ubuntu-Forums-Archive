---
title: "vVidia driver problems"
date: 2008-05-22
forum: Multimedia Software
---

### Post by pir on 2008-05-22
I have tried several tutorials, but I can't seem to get my dual monitor setup to work. I have two monitors, both 1440*900. My graphics card is nVidia 8600.

The problem which keeps coming back is
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
when trying to run nvidia-settings.

Currently, I think I am very near to the solution, but each time I try to do one step further, it doesn't work anymore.

What is working:
Both monitors give a resolution of 1440*900. There is a cloned output.

I **think** I am currently using nvidia-glx-legacy.

[http://pastebin.com/f4401df1a](http://pastebin.com/f4401df1a) is my current xorg.conf


ANY HELP IS APPRICIATED! Thanks!

---

### Post by pseudo-random on 2008-05-22
[http://ubuntuforums.org/showthread.php?t=780777&highlight=nvidia+dual+monitors](http://ubuntuforums.org/showthread.php?t=780777&highlight=nvidia+dual+monitors)

---

### Post by pir on 2008-05-22
> **pseudo-random said:**
> [http://ubuntuforums.org/showthread.php?t=780777&highlight=nvidia+dual+monitors](http://ubuntuforums.org/showthread.php?t=780777&highlight=nvidia+dual+monitors)

Another tutorial... 
Well, I hope this will work, I'll post here if it worked.

Tnx for the reply ;)

---

### Post by pir on 2008-05-22
Well, 90% worked, I am now stuck at step 8.

Via *$ gsku displayconfig-gtk* I should be able to edit the monitor settings of both monitors, but it only shows one monitor.

How can I make my 2nd monitor appear in displayconfig-gtk?

---

### Post by pir on 2008-05-23
:frown:
It won't work. I am getting really frustrated now :-(

I have just reinstalled my PC with 7.10

It just wont work. Anyone who would like to help me PLEASE I do not know what to do :(

---

### Post by xc3RnbFO8P on 2008-05-23
> **pir said:**
> 

I **think** I am currently using nvidia-glx-legacy.


Then you have install a wrong driver:
> 
**If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy**

Check in Synaptic Package Manager, search: **nvidia-glx-legacy**

---

### Post by pir on 2008-05-23
Thnx for the replies.
It works now. I am so happy :)

What I did to get my Dualscreen working on one nvidia card:
-> Clean install of 8.04
-> Activated restricted drivers
-> Installed nvidia-settings

I even got compiz working:)

---

