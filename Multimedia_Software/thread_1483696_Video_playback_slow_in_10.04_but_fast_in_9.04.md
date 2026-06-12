---
title: "Video playback slow in 10.04 but fast in 9.04"
date: 2010-05-14
forum: Multimedia Software
---

### Post by timkoop on 2010-05-14
Hi everyone.

I have two Ubuntus installed.  A 10.04 and a 9.04.  

In 9.04 if I watch a video in Firefox, it works very smoothly and nicely.  Using the "top" command, totem-plugin-vi is using the most cpu time at about 16%, and xorg is using about 5%.  But in 10.04, totem is using 72% and xorg is using 26%, and it looks really choppy.

I think watching DVDs is the same way.

Any ideas?

I checked "Hardware Drivers" in the System->Administration menu (in 10.04) and it said "No proprietary drivers are in use on this system."

I'm guessing maybe I'm using different video drivers on each system, but I don't even know how to check.

Any advice would be appreciated.  Thanks.

Oh, and here is an excerpt from lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

Thanks.

--
Tim

---

### Post by Eiríkr on 2010-05-15
I've got similar symptoms in Lucid 10.04.  Video playback is so choppy that sound gets all scratchy too.  Videos on the Vimeo site weren't a problem in 9.04, but are generally not fun to watch in 10.04.

Relevant [FONT="Courier New"]lspci[/FONT] output:
```
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV380 [Radeon X600]
```

What gives?  I've used the stock ati driver on both systems, the only difference is whatever got changed between 9.04 and 10.04.  Any hints on a solution would be appreciated.

---

### Post by Eiríkr on 2010-05-15
On a hunch, I downloaded the .flv I was trying to watch, and it plays just fine locally through Totem.  I tried again in my browser off the website, and despite waiting until it was fully buffered (to make sure the choppiness wasn't a slow streaming issue), it was still awful.

This seems to implicate Adobe's flash plug-in.  No real surprises there, since I'm running 64-bit, and they've been rather bad about 64-bit support.  Anyone aware of any alternate flash plug-in?

---

### Post by lovinglinux on 2010-05-15
> **timkoop said:**
> Hi everyone.

I have two Ubuntus installed.  A 10.04 and a 9.04.  

In 9.04 if I watch a video in Firefox, it works very smoothly and nicely.  Using the "top" command, totem-plugin-vi is using the most cpu time at about 16%, and xorg is using about 5%.  But in 10.04, totem is using 72% and xorg is using 26%, and it looks really choppy.

I think watching DVDs is the same way.

Any ideas?

I checked "Hardware Drivers" in the System->Administration menu (in 10.04) and it said "No proprietary drivers are in use on this system."

I'm guessing maybe I'm using different video drivers on each system, but I don't even know how to check.

Any advice would be appreciated.  Thanks.

Oh, and here is an excerpt from lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

Thanks.

--
Tim

Your CPU usage problem is due to the missing driver for your graphics card. Don't know how to solve that tho, since mine always show up in the list.

> **Eiríkr said:**
> On a hunch, I downloaded the .flv I was trying to watch, and it plays just fine locally through Totem.  I tried again in my browser off the website, and despite waiting until it was fully buffered (to make sure the choppiness wasn't a slow streaming issue), it was still awful.

This seems to implicate Adobe's flash plug-in.  No real surprises there, since I'm running 64-bit, and they've been rather bad about 64-bit support.  Anyone aware of any alternate flash plug-in?

The version you have is the best one for 64bit system. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

