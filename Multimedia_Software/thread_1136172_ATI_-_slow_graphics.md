---
title: "ATI - slow graphics"
date: 2009-04-24
forum: Multimedia Software
---

### Post by se_landy on 2009-04-24
Hi,

I have clean install of ubuntu 9.04. I've managed to solve every problem so far except one... When i minimize window it goes away very fast, but when I try to unminimize it, it comes back very slowly. And if there is music or video playing, everything stops for a second! I also noticed that when I try to open some application or just a window with files it opens very slowly. I don't see that my CPU goes to 100%, so I think it's graphics that I'm having problems with...
It's very annoying!! Did anyone have similar problems, or does anyone know how to fix this???
I have ATI Mobility Radeon 2400, and I have enabled ATI proprietary FGLRX graphic drivers from System->Administration->Hardver drivers

EDIT: I have found similar problems and I would like to try [this]("http://ubuntuforums.org/showpost.php?p=6970990&postcount=2"). Does anybody know where can I edit those options???

---

### Post by murderslastcrow on 2009-04-25
I'm having similar issues with my ATI graphics card, too, after a new install. Compiz was automatic on both Intrepid and Jaunty, but suddenly things have become stilted and a bit annoyingly so. I don't wanna' go back one version just because of the interface.

I tried UXA acceleration to no avail (no real difference). I'll go try XAA now.

If you want to do it, edit your xorg.conf file (located in etc/X11/xorg.conf). You can either do this using sudo gedit from the terminal, or simply type "gksu nautilus" to browse to the file yourself.

Under where it says Section Device, you'll want to place this line.

Option      "AccelMethod"   "XAA"

Replace XAA with UXA or whatever other method you wish to enable. Save, restart X (logout), sign in and see what results you get. I'm gonna' try XAA now.

---

### Post by murderslastcrow on 2009-04-25
Right on! Haha, seems to have fixed the problem for me. ^,~ Keep me posted on your situation.

---

### Post by poyraza on 2009-04-26
Hi there,

I have the same issue.  I have found this website; [http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html]("http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html")

I hope it helps for all of us,
Regards

---

### Post by se_landy on 2009-04-26
Could you tell me what did you exactly do??? What driver did you use (the one from System->Administration->Hardware Drivers)??? I've tried to use that driver and set AccelMethod to XAA, it speeds up a bit, but it is still not fast enough... Windows still show up slowly and music stops when i try to open anything... Fullscreen is an impossible mission :(

This is Device section from /etc/X11/xorg.conf

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
	Option	"AccelMethod" "XAA"
EndSection
```

EDIT: Adding this line just makes things worst :(
```
Option "MigrationHeuristic" "greedy"
```

---

### Post by RockClimb on 2009-04-26
I am having the same problem with ubuntu 9.04 and the latest version of the fglrx drivers. I didn't have this trouble with ubuntu 8.10 and the fglrx drivers. I have found a way to correct it, but it comes with a new problem.

I had this in my xorg.conf

Section "Extensions"
       Option  "Composite" "Disable"
EndSection

video works great with this option... but the problem that it causes makes the system unusable. The problem is, with this disabled, I have no window frames. I can't resize, minimize, maximize, or close windows. I have tried the options above and they offer no improvement. If anyone has any idea on how to fix this, I am desperate!!!! If I don't find a fix in the next day or so I will be switching back to 8.10.

---

### Post by mattman on 2009-04-26
This helped me quite a bit with a ATI 9250.

> **poyraza said:**
> Hi there,

I have the same issue.  I have found this website; [http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html](http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html)

I hope it helps for all of us,
Regards

---

### Post by Melcar on 2009-04-26
Well for one, fglrx does not support UXA, so attempting to load it will just cause problems or simply not do anything.  The only acceleration type supported by fglrx is XAA, which is loaded by default.
Second, the current driver has problems with composition managers.  The slow resizing and transforming of windows are recurring issues that have not been solved.  Jaunty seems to have made things a bit worse however.
Lastly, the open source drivers (radeon & radeonhd) support both XAA and EXA acceleration.  It depends on the chip, but usually XAA is loaded by default.  EXA is faster, so it's generally better to enable it.

---

### Post by RockClimb on 2009-04-27
I have a fix, at least for me! Will be posting details in a bit.

---

### Post by RockClimb on 2009-04-27
It is super late, so here are the basics. Not exactly sure what is causing the problem at this point. With the option in my earlier post. I completely removed everything related to compiz. I reinstalled gnome. The problems were still there. I created another user and logged into it. Everything worked great. For some of you, this will give you enough info to fix the problem. For the others, I will track down the problem after I get some sleep.

---

### Post by RockClimb on 2009-04-27
At this point I recommend backing up your files in your home directory and wiping it, or just create another user for yourself. I found another problem I was having was caused by config files in my home directory. Somewhere along the way some things are not getting overwritten and they are causing various problems.

---

### Post by dE_logics on 2009-04-28
Why don't you all use the proprietor drivers form ATI's website?


You know that gives the best performance.

---

### Post by Ghilteras on 2009-04-28
> **dE_logics said:**
> Why don't you all use the proprietor drivers form ATI's website?


You know that gives the best performance.

i'm having those issues with those very drivers.

---

### Post by mattman on 2009-04-28
My 9250 graphics card is no longer supported by the proprietary driver.

> **dE_logics said:**
> Why don't you all use the proprietor drivers form ATI's website?


You know that gives the best performance.

---

### Post by ZaaBI_AlonSo on 2009-09-06
> **poyraza said:**
> Hi there,

I have the same issue.  I have found this website; [http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html]("http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html")

I hope it helps for all of us,
Regards


can it help with compiz enabled???

---

### Post by kubusz on 2010-06-13
I have upgraded to Ubuntu 10.04 and my graphics got really slow, especially rendering. When I scrolled down in FireFox it was slow and not smooth.

This link helped me a lot [http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html](http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html)

I commented the original Section "Device" in my /etc/X11/xorg.conf and added the following lines

Section "Device"
 Identifier "ATI Radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
 Option "MigrationHeuristic" "greedy"
 Option "AccelDFS" "true"
 Option "EnablePageFlip" "true"
 Option "EnableDepthMoves" "true"
EndSection

And now everything is fast :)

---

### Post by h4ck3r on 2011-06-17
> **kubusz said:**
> I have upgraded to Ubuntu 10.04 and my graphics got really slow, especially rendering. When I scrolled down in FireFox it was slow and not smooth.

This link helped me a lot [http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html](http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html)

I commented the original Section "Device" in my /etc/X11/xorg.conf and added the following lines

Section "Device"
 Identifier "ATI Radeon"
 Driver "ati"
 Option "AccelMethod" "EXA"
 Option "MigrationHeuristic" "greedy"
 Option "AccelDFS" "true"
 Option "EnablePageFlip" "true"
 Option "EnableDepthMoves" "true"
EndSection

And now everything is fast :)

THANK YOU SO MUCH! My computer was running rather laggyish, and with these added, everything is great! I knew it wasn't my card since I'm using an HD5970... :D

---

