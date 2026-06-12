---
title: "Stalling and Choppy video with ATI HD 2600 Pro"
date: 2008-12-14
forum: Multimedia Software
---

### Post by mholland on 2008-12-14
I have seen people having this same issue in the past and it is something I have continued to research. Video lags and is choppy, and sometimes even just goes blank while audio continues to work. I have disabled special effects, tried lowering the resolution, changing video output (in VLC), going fullscreen is just out of the question. Does anyone have a quick fix for this issue? If you need more info I'll do what I can. Unfortuneately I have Creative (eep!) and ATI (eck!) hardware on the system. I have managed to get both sides working great except for these video issues.

OS: Ubuntu 8.10 Intrepid
Hardware: P4 3.4ghz w/ 3gb RAM
          512mb ATI HD 2600 Pro AGP

---

### Post by mholland on 2008-12-14
bump

---

### Post by mholland on 2008-12-15
bump .... anyone ... anybody ... hello :popcorn:

---

### Post by DwalerXIII on 2008-12-16
I also have a ATI HD 2600 Pro AGP but I can't even play a video.
The system freezes after a few seconds when playing video. 
Using Compiz is completely out of the question.

When running the Compiz-check script I only get 5 times a green OK but when I activate Compiz my system freezes.

Now I use the Ati Catalyst driver 8.12 but I had the same issues wit the 8.11 and 8.10 driver.

---

### Post by del_Brujo on 2008-12-16
> **DwalerXIII said:**
> I also have a ATI HD 2600 Pro AGP but I can't even play a video.
The system freezes after a few seconds when playing video. 
Using Compiz is completely out of the question.

When running the Compiz-check script I only get 5 times a green OK but when I activate Compiz my system freezes.

Now I use the Ati Catalyst driver 8.12 but I had the same issues wit the 8.11 and 8.10 driver.


Yes, the same happened to me with the new kernel.

---

### Post by mholland on 2008-12-16
Well using EnvyNG then activating the restricted driver on 8.10 Intrepid I had to do a few additional configuration settings. Reset the ATI configuration to default, the settings don't appear to be written properly the first go around and then make manual entries to the xorg.conf file. I have this info if you need it. I can get most videos to play in a small window, full screen is absolutely not happening. I am trying to play a bluray rip and I think the computer is about to overdose on all the high resolution high frame rate visuals spilling my way. Compiz doesnt freeze and I can turn on all the desktop  effects without performance impacts. I can game and see 3D models rendered...

The problem is with movies... I guess there really isnt any other way... Maybe its time to set up dual boot for movies. I AM STAYING TRUE TO UBUNTU HOWEVER!

---

### Post by JC Cheloven on 2008-12-16
Hi, almost the same here. 
I've an Intel 82852/855GM ("integrated graphics device") in my toshiba laptop, and the totem window gets black sometimes when playing a movie. Also if I move the mouse around, some rectangles of the window get black. I thought it was my graphics card, but it seems to be a broader issue.

As a silly workaround, try moving the window a little. It works for me (for a while).

---

### Post by Qui-Kelle on 2008-12-27
I have Club3D 2600 pro and can't even install 8.10, please recommend me distribution of ubuntu which will work with this video card.Thank you.

---

### Post by houseworkshy on 2010-01-19
I've done a lot of reinstalling recently.  Ever since the time of 9.10 being released I have also being getting stalls in all video formats and players, both from the dvd drive and files on the hard disk.  I have done clean installs of all Ubuntu versions from 8.04 to 9.10 and it is true of the lot.  As until around the time of 9.10 being released this was not a problem I am puzzled but can only assume that there is some bug in the codec which has got into the updates for all packages ( certainly 8.04 to 9.10 inclusive).  Does anyone have a fix for this?

---

