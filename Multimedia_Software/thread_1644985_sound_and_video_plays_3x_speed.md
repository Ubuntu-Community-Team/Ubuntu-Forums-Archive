---
title: "sound and video plays 3x speed"
date: 2010-12-14
forum: Multimedia Software
---

### Post by goonie21 on 2010-12-14
I am new to ubuntu and linux in general.  I recently installed Ubuntu and have had trouble getting the sound to play correctly it is playing at 3x the speed if not faster.  This happens in Youtube videos other websites that play videos and also music in rhythembox.  My sound card is a SB! Live EMU10k1x.  Any help would be greatly appreciated.

---

### Post by jalopynolikey on 2010-12-14
I've had the same problem plaguing me since I switched all of 2 days ago from 10.04 to 10.10. Whether using Chromium or Firefox, all flash and .flv files played in browsers or VLC run at 3x speed (both video and sound). 

I have tried disabling hardware acceleration in flash settings in browser and I ran this suggested command line code:

[FONT="Courier New"][SIZE="3"]sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/[/SIZE][/FONT]

This made no difference. I'm pretty green with Linux and Command Line so any kind and patient explanations for solving this would be much appreciated.

---

### Post by Svamp on 2011-01-21
I have the exactly same problem. I have gotten some suggestions that can be viewed in the thread that I made. [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10382714](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=10382714)

However I have had no success in fixing this problem. I might making a reinstall of Ubuntu, and see if that fixes the problem.

---

