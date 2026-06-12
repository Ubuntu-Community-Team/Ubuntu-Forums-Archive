---
title: "Broadcom 4322"
date: 2013-08-18
forum: Networking &amp; Wireless
---

### Post by edog2 on 2013-08-18
Howdy folks,

I have a broadcom4322 wireless card/adapter and am trying to get it to work, but my efforts have been fruitless. Ive tried to activate through additional drivers, download the firmware through software center,and ive tried using certain commands in terminal. Nothing is working.

When I try to download the driver through terminal, it prompts me to insert "disc labeled 'Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)' in the drive." I am pretty sure that I have put this disc in already. If its the wrong disc, then I have no clue what to insert because thats the only ubuntu-related disc I have.

Help please!

---

### Post by edog2 on 2013-08-18
**Copied from my earlier thread in beginner section**

Howdy folks, 

I have a broadcom4322 wireless card/adapter and am trying to get it to work, but my efforts have been fruitless. Ive tried to activate through additional drivers, download the firmware through software center,and ive tried using certain commands in terminal. Nothing is working.

When I try to download the driver through terminal, it prompts me to insert "disc labeled 'Ubuntu 12.04.2 LTS _Precise Pangolin_ - Release amd64 (20130213)' in the drive." I am pretty sure that I have put this disc in already. If its the wrong disc, then I have no clue what to insert because thats the only ubuntu-related disc I have.

Help please!

---

### Post by ibjsb4 on 2013-08-18
First you need to open up your software sources and UNcheck CDrom.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

Thats why its asking for the CD, which is not needed.

I have the same wireless card, so you need to install "bcmwl-kernel-source" package from the software center and you should be good to go :)

[ATTACH=CONFIG]245464[/ATTACH]

Have any more questions; please post back.

---

### Post by cariboo on 2013-08-18
Please don't create multiple threads on the same subject, I have merged your two threads.

To answer your question, I'd leave the CD-Rom enabled in Software sources, until after you have installed the correct driver for your wireless device.

Open the Software Centre, and search for **dkms** and install that, next search for **fakeroot** and install that, and finally search for [/b]bcmwl-kernel-source[/b] and install that. The order you install fakeroot and dkms doesn't matter, but make sure you install bcmwl-kernel-source last.

I run development versions, and with every installation on my netbook I have to install the drivers, I find that installing the wireless drivers from CD-Rom or USB drive to be far easier than searching for a spare network cable, disconnecting something from my switch, connecting the netbook, installing the driver, then reversing the procedure. :-)

---

### Post by ibjsb4 on 2013-08-18
I did not know that you could find drivers on the live cd.  I use the mini.iso and search for a spare network cable, disconnecting something from my  switch, connecting the netbook, installing the driver, then reversing  the procedure. :smile:

---

