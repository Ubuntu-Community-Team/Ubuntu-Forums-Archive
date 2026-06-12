---
title: "Problem with Flash player buttons"
date: 2010-05-25
forum: Multimedia Software
---

### Post by OdinOrion on 2010-05-25
Hello,

I am having a problem with Flash player.  It seems that I can not use the in screen buttons on some flash media player content.  I use YouTube to satisfy my music curiosity and typically scroll through the flash player to find new music.

Here is the issue.  There seems to be two versions of Flash on YouTube.   One has a horizontal volume slider.  This version works fine.  I have volume control, all the flash buttons work, and the in screen scroll buttons work.

But there is also another version of the player that has vertical volume control.  In this version I can not move the volume slider, none of the other flash buttons work, and the on screen scroll does not work.  

I am not sure if this is a Flash player problem, a browser problem or an Ubuntu problem.

Any suggestions appreciated.

Woops! Forgot imortant stuff:  Ubuntu 10.04, Mozilla default browser (wanted to use Opera, but whatever) with latest Flash plugin.

---

### Post by lovinglinux on 2010-05-25
If you are using 64bit system, then installing the 64bit version of flash should fix your problem. To do that easily or even revert to 32bit if you don't like the 64bit version, install [FLASH-AID](http://flash-aid-extension.blogspot.com/) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by OdinOrion on 2010-05-25
I am using the 64 bit.  IIRC, I let Firefox download the Flash plug in package.  I would have thought it would grab the right version automatically. 

Is there anyway to check which version of Flash is installed?

Strangely enough, I prefer command-line if I can.  I like to actually "see" what is going on, and it seems that the command-line offers more control than the GUI.

---

### Post by lovinglinux on 2010-05-25
> **OdinOrion said:**
> Is there anyway to check which version of Flash is installed?

Type about[noparse]:[/noparse]plugins in Firefox address bar.

> **OdinOrion said:**
> Strangely enough, I prefer command-line if I can.  I like to actually "see" what is going on, and it seems that the command-line offers more control than the GUI.

See link on my previous post.

---

### Post by OdinOrion on 2010-05-25
Fixed!  I just went ahead and did the command line to remove the plug in and then replace with the 64-bit.  All buttons now work!

Thanks!

---

### Post by Giant Enemy Cat on 2010-05-25
Never mind, fixed.

Thanks lovinglinux.

---

### Post by lovinglinux on 2010-05-25
> **OdinOrion said:**
> Fixed!  I just went ahead and did the command line to remove the plug in and then replace with the 64-bit.  All buttons now work!

Thanks!

You are welcome.

---

### Post by andreasbuykx on 2010-07-04
Had the problem too. This worked for me:

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

Many thanks to lovinglinux!

---

### Post by lovinglinux on 2010-07-04
> **andreasbuykx said:**
> Had the problem too. This worked for me:

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

Many thanks to lovinglinux!

You are welcome. That is the recommended method now, since Adobe dropped the support for the 64bit version of flash.

---

