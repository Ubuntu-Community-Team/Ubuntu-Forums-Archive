---
title: "The CTL/ALT F1 Trick, etc Doesn't Get nVidia Drivers Installed"
date: 2010-01-21
forum: Multimedia Software
---

### Post by motsteve on 2010-01-21
I'm using Karmic 32. I have the nVidia NVIDIA-Linux-x86-190.53-pkg1, but if I try to get a virtual terminal with CTL/ALT/Fx all I get is hash.  I tried recovering mode, but it doesn't like run level 1.  I think this is my last nVidia card (9800).  I've already had to reinstall Karmic 32 and 64 at least 5 times each because if it does look like 190.53 installs, the screen goes black as soon as you should be seeing Xserver.  I have a feeling that ctl-del-bckspace is a ruse also.

One would think a gpu vendor would always want his gpu to have some sort of installation instructions that ought to work with the various machines around.  I search all over their web site and found zilch.

:P

---

### Post by SymphonicNerd on 2010-01-21
I believe i experienced a similar problem recently, when i would try to switch to one of the TTY's or ctrl+alt+fx as you referred to it, my screen would switch to nothing but colors or what looked like tv fuzz depending on its mood. what someone here suggested was checking the grub file for a line that read VGA=775 or something like that. when i was in grub i hit e to edit then erased that line and haven't had any problems since after the next boot. but you may want to check around because it seems like your graphics card is probably newer then mine

PS- im on 9.10 Karmic just so you know what version of ubuntu im running

---

### Post by motsteve on 2010-01-22
Ever since grub2 came along my flawless multiboot system was working like a dream.  Now I have three big drives with only one with Windoz and Karmic on it.  Progress!  It sounds more like Congress!

There has to be a nVidia engineer or other gpu expert that can help us with this.  It seems wasteful to buy a really nice gpu only to have it sit there not working up to par because the drivers are ancient.  The real insult is the drivers are available and to put them on, you have to play the game Jeopardy.  Silly is the only term I can think of at the moment.

I've read all the past threads, they don't even apply any more.:confused:

Thanks for the response.  I usually talk to myself on this forum.  Of course, I normally talk to myself.:D

Steve

---

### Post by motsteve on 2010-01-22
Well, like usual, I'm answering my own questions because no one seems to like to answer questions that seem too complicated.  This little jaunt only took me two days of searching.   After the 8th reload of Karmic 32 I got a virtual terminal (ctl-alt-F1 to F6).  Once logged on I was able to stop the x server with /etc/init.d/gdm stop, but not without the machine giving me a big admonishment for taking such an ancient and crude way.  I had already downloaded the script for the 32 bit version, so I ran it like normal " $ sudo sh NV..........pkg1.run"  Apparently the  one for Karmic 64 is NVIDIA.........pkg2.run.  I answered all the ncurses questions, but before getting out of the virtual terminal, I did a "/etc/init.d/gdm start" and a  " $ sudo reboot ".  When I got back on, I installed the NVIDIA control center and it verified that I had indeed installed 190.53.  The normal hardware menu said it still wanted me to use  185..... 

I surely hope this helps the people like me that seem to have to blunder along on their own.:(

---

