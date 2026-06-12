---
title: "nvidia g86 rev a1 driver for 12.04 please"
date: 2013-03-28
forum: Multimedia Software
---

### Post by iocane on 2013-03-28
Hello all I have been having the worst time with video cards since I switched to 12.04.  I had an onboard ati Graphics card but I screwed up everything so bad I couldn't even boot into safe graphics mode with it (I installed a driver directly from ati website and didn't know how to remove it)  So instead I went out and got an used nvidia gforce card from a friend.  When I use  the  lspci |grep VGA command the out put I get is g86 rev a1.  I can run this card in fail safe graphics mode but not boot to it without.  I am still kind of new with linux and would like a way to either use the fail safe driver as my default or use a known good driver for this graphics card.  Also I am using a daewoo lcd monitor that is at least 10yrs old.  I am not sure if this is my root cause or not.  Thank you in advance for your help

---

### Post by ManamiVixen on 2013-03-28
What are your computer's specs? Model? What graphics cards are we talking bout here? Their model's too please.

---

### Post by iocane on 2013-03-28
Ok  I built the system myself
 processor is an amd a43300 2.5ghz
Mother board is a gigabyte ga-a55m-d52
hard drive is a seagate barracuda 7200 500gb drive
and the video card I am trying to use is the nvidia geforce 8300gs (or g86)
and I am running Ubuntu 12.04lts

---

### Post by ManamiVixen on 2013-03-28
Since you are on 12.04, the nvidia-current (173.XX) should work for your card. "sudo apt-get update && sudo apt-get install nvidia-173-updates"

---

### Post by iocane on 2013-03-28
no such luck.  when I booted up I got hung up on the ubuntu splash screen with and when I restarted I go a black screen.  I have just booted back into fail safe graphics mode and used  sudo apt-get purge nnidia-current

can I use the fail safe graphics driver as default?

---

### Post by ManamiVixen on 2013-03-28
I meant to put "nvidia-173-updates" not "nvidia-current" sorry. I fixed my previous post/

---

### Post by iocane on 2013-03-28
yeah I tried "nvidia-173-updates" as well and got the same result

---

