---
title: "ATI Restricted Drivers not Working Even Though Enabled (Hardy)?"
date: 2008-05-03
forum: Multimedia Software
---

### Post by plinydogg on 2008-05-03
Hi folks,

I just upgraded in place from Gutsy to Hardy and everything seems to work fine except I'm having problems with my ATI drivers. Here's the scoop.

***Symptoms/Problem:***
(1) Visual effects are sluggish, from compiz stuff to just plain old menus.
(2) AssaultCube, a 3D game that ran fine in Gutsy, doesn't run properly and cites some sort of driver/video card problem as the reason. 
(3) Whenever I run glxgears, my system resources (2 GHz processor, 1 gig RAM) start maxing out (XGL starts to take up about 87% of the CPU).

***Why It's Weird:***
(1) I've enabled ATI Accelerated Graphics Driver in the Hardware Drivers (a.k.a. Restricted Drivers Manager).
(2) Although my graphics card isn't the greatest (ATI Radeon 200m), it has always been more than enough to produce fine video performance on previous versions of Ubuntu. 

My limited know-how tells me that this is a driver issue, but what could the problem be? I'm using the accelerated ATI driver...what else can I do?

Thanks in advance!

---

### Post by plinydogg on 2008-05-03
Well crap. I just attempted to turn off the restricted ATI driver and reboot (I had heard that doing this and then re-enabling it and rebooting again can solve the problem). After disabling the restricted driver and rebooting I am now stuck in an endless login screen loop: I enter my login information and then a few seconds letter it takes me to the login screen again!

Looks like I'm going to have to do a fresh install.

---

### Post by Canis familiaris on 2008-05-03
Before reinstalling Ubuntu, try this:
Go to tty mode: Ctrl + Alt + F1
 
At the terminal:
```
sudo dpkg-reconfigure xserver-xorg
```
And select vesa as your video driver.
And select all default choices

---

### Post by Canis familiaris on 2008-05-03
Use envy to install the ATI drivers instead of the restricted driver manager.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by plinydogg on 2008-05-03
Anurag_panda: Thanks for the quick response. Actually, while I was waiting on someone to respond, I booted into Vista and continued to troll the forums for help. I found that I could switch sessions into "failsafe Gnome" and then reenable the restricted driver. Now I'm back in business with only the original problem. 

I'm going to try to use envy and will report back here momentarily.

---

### Post by plinydogg on 2008-05-03
Well, the installation of envy went fine, I rebooted, etc. but the problem remains. I'm not sure if it's important or not but Hardware Drivers says that I still have the restricted driver enabled. 

Let me know if you think of anything else.

Thanks

---

### Post by Kowalski_GT-R on 2008-05-03
Envy isn't solving jack for a lot of people, at least in Hardy: Ati problems go beyond the drivers...

---

### Post by plinydogg on 2008-05-03
Kowalski_GT-R: Are you saying that this is a permanent problem?

---

### Post by plinydogg on 2008-05-03
Since my graphics card worked fine in Gutsy, I'm tempted to think it's something that changed in Ubuntu that is causing the problem. If that's the case, then it is fixable, right?

---

### Post by thirddeep on 2008-05-03
I am having a similar problem.

My problem is as described in : [http://ubuntuforums.org/showthread.php?t=758576&page=4](http://ubuntuforums.org/showthread.php?t=758576&page=4)

When I enable ATI restricted drivers and restart, all I get is a black screen -- and unable to CTRL + ALT + F1, complete lock up.

I can work fine with MESA, but then I can't play games :-)

They only driver that seems available with EnvyNG is 8.3.  I have tried to fix this with the normal way - click enable on restricted drivers - and Envy.

Thd.

Typed 8.4 instead of 8.3

---

### Post by thirddeep on 2008-05-03
I have fixed my problem !

I ran across this site : [http://wiki.cchtml.com/index.php/Troubleshooting#Computer_Freezes_while_using_fglrx_.28UMA_and_SIDEPORT.29](http://wiki.cchtml.com/index.php/Troubleshooting#Computer_Freezes_while_using_fglrx_.28UMA_and_SIDEPORT.29)

After reducing the AGP Aperture, still had the same problem.  So I tried the opposite, and increased it to 512.  FIXED :-)

Thd.

---

### Post by plinydogg on 2008-05-03
Alright. I've fixed it sort of. The ATI website recommended removing MESA by uninstalling xserver-xgl. They warned that doing so could mess up compiz but it didn't for me. Removing this package fixed all of the problems I listed in the original post.

The only problem with in-game video performance now is flickering, which I believe I read is caused by a conflict with compiz (I'll have to investigate that later).

The only problem now is that whenever I try to play back video all I get is a black screen plus the proper audio. I attempted to fix this by going to preferences->main menu and enabling "multimedia system selector." I then went into multimedia system selector, clicked on the "video" tab, and then selected "X Windows System (no xv)." Doing this allows me to play back video but only in Totem (i.e., not VLC). I'm going to try to find a solution to this problem.

Anyone have any ideas? I know the black screen during video playback is a fairly common issue.

---

### Post by plinydogg on 2008-05-03
Thirddeep: glad you got everything worked out!

---

### Post by plinydogg on 2008-05-03
Alright. After much tinkering here's where I'm at: with xserver-xgl uninstalled, compiz works flawlessly; there's no system sluggishness; but videos don't really play, most of the time I get a black screen when attempting to play video files, and the DVD playback is so slow as to be useless. Also, 3d games are rendered almost unplayable by the compiz conflict flickering effect.

When I disable compiz by switching to no desktop effects I can play some videos without the flicker effect and all of my 3d intensive games work fine with no flickering. 

Thus, the bottom line is this: to play games I have to disable compiz. DVD playback doesn't work no matter what, and I am still plagued by the black screen problem.

If anyone finds magic solutions to these problems let me know. Also, I will update this thread if I find any solutions.

---

### Post by st0nedpenguin on 2008-05-04
Not the most useful input, but if you have an older card that has 3d support from the open source ati driver included by default in Hardy, give it a shot.

I dropped a bit of 3d framerate but I have fully working Compiz with non flicker windowed video/3d.

Unfortunately if you have a newer card you may be stuck with the restricted driver. :|

---

### Post by plinydogg on 2008-05-04
Interesting idea stOnedpenguin. How do I go about doing that? Just uncheck the ATI restricted driver in system->administration->hardware drivers?

---

### Post by st0nedpenguin on 2008-05-04
I'd imagine that should work, if not then you may have to manually uninstall the ATi fglrx drivers, I just skipped them entirely though since I carried out a fresh install once Hardy hit release.

---

### Post by plinydogg on 2008-05-04
What graphics card do you have?

---

### Post by st0nedpenguin on 2008-05-05
Still running my crusty old X800XTPE, serves me well enough for Compiz and the odd game on Linux.

---

### Post by plinydogg on 2008-05-11
Alright I've fixed the remaining problems. Specifically, movie files now playback as they should. To fix this problem, I just installed this package via synaptic:

ubuntu-restricted-extras

DVD playback now works normally as well, after following the instructions on this useful thread:

[http://ubuntuforums.org/showthread.php?p=4615284](http://ubuntuforums.org/showthread.php?p=4615284)

Finally, to switch rapidly between compiz and metacity (because, for example, compiz conflicts with a lot of 3d games), I use fusion-icon (available via synaptic).

Thanks for everyone's help!

---

