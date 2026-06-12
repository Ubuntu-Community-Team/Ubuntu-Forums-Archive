---
title: "Serious ATI issues..."
date: 2009-07-29
forum: Multimedia Software
---

### Post by internalkernel on 2009-07-29
This all started when I didn't check to see if my card was supported under the Catalyst 9.6 or not. I mean the laptop is a little over 3 years old, I figured it would be supported... I was very wrong. 

I have an ```
ATI Technologies Inc M24 1P [Radeon Mobility X600]
``` currently on Jaunty. I tried installing the 9.6 drivers, and of course got a strange error regarding memory allocation can not load module... 

So, I uninstalled it and this is where it started getting weird. The open source Radeon driver wouldn't load by default even when I would specify it... and then X would just hang before the log in screen. I could still SSH into the machine, and top should Xorg eating 100% CPU. The machine itself (other than SSH) was completely unresponsive to anything. 

I figured maybe there were some left over ATI modules/crap in there, checked my xorg.conf, etc. etc. - couldn't figure it out. The load I had on the machine was old, and alot of other people had been using it... so, I decided it was time for a re-install anyways. But, the problem persisted even after a clean install of Jaunty; which has worked flawlessly in the past. In fact, the livecd exhibited the same issue unless I specified "Safe Graphics Mode". Which of course left me using the VESA module. 

I then began trying some more solutions, updated X (to the latest experimental PPA), tried Tormold's Radeon driver... nothing helped. Then I tried to use the LiveCD of Intrepid as a test, which had a version of X that was compatible with the last supported release of Catalyst for my card. However, Intrepid had the same issues. So... for sh!t and giggles - and to satisfy my own curiosity at this point, I started playing with Hardy. The radeon driver would actually load on Hardy, X started and seemed to be okay... However, the screen was filled with garbage - blocks of pixels would flash red. But, at least it was working... So, I tried to install the Catalyst 9,3 (last supported release) in Hardy... and I got the same garbage filled pixelation on the screen. 

I've checked through log files and it showed no errors in loading the radeon module, in fact everything looked exactly as it should... but this all leaves me at a total loss. I'm stuck with the VESA module right now... and I'm starting to think that I somehow fried the card. My only option is to consider a hardware issue - although, then I should have some issues using VESA as well. 

I have even emailed ATI support explaining the issue and hoping they had some insight into the why... perhaps the Catalyst 9.6 install corrupted some firmware on my card. Totally grabbing at straws at this point... but they were absolutely no help - worse than no help... they didn't even try to address my question.

I'll attach the Xorg.0.log and my xorg.conf from when the radeon module did load on Jaunty, and X then freezes... I'm totally open to suggestions at this point, because I have no idea...


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
lspci -v
```
01:00.0 VGA compatible controller: ATI Technologies Inc M24 1P [Radeon Mobility X600]
	Subsystem: Hewlett-Packard Company Device 3082
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=256]
	Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at b0120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel modules: radeonfb

```

---

### Post by xzero1 on 2009-07-29
Check the troubleshooting section in this link [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

---

### Post by steefjeqv on 2009-07-29
Hi, 

Did you try :

sudo dpkg --purge fglrx-amdcccle fglrx-kernel-source xorg-driver-fglrx

This command should remove all fglrx stuff.

Then try the xorg ati driver.

I've attached my xorg.conf.

Greetings,
Steven

---

### Post by internalkernel on 2009-07-30
Thanks for replying, didn't have a chance to do anything about this until this morning. 

I've been through the Troubleshooting section of that cchtml.com before, most of that applies to fglrx drivers which I'm not trying to run. The Open Source Radeon driver won't load either and when it does pins Xorg at 100% CPU. 

I've tried specifying radeon and ati as the driver in xorg.conf. I'm way past dpkg --purge since this is a clean install, besides when I initially installed the driver I didn't build distro specific packages - I just let it install. there's an uninstall script in /usr/share/ati for it. Which is what I used at first... 

The issue now is rather simple... and completely unknown to me. By default with the radeon package installed my computers boots using the VESA driver - if I specify radeon or ati in xorg.conf - the computer boots and upon starting X freezes, ssh is the only way to access it and top shows Xorg eating 100% cpu. 

I'm using tormold's radeon driver and the standard version of X that comes with Jaunty.

---

### Post by xzero1 on 2009-07-30
Personally, I am convinced there is a big problem with X in Jaunty. Just browse launchpad for 'Jaunty freezes' and note what *they* think causes the problem. I have had my own problems first with a Nvidia card -- frequent freezes, unexplained segfaults, hard lockups. X using 100% etc. Luckily I also had a pre-release version of Jaunty installed. It worked much better since I did not allow it to update. After my motherboar failed (not related) I now had an completely different motherboard and cpu with a built-in ATI card. Using the stock flgrx driver I started having the same type of problems! Luckily, updating to catalyst 9.6 fixed everything in my case. Nothing that I could find corrected the problem save the final update to 9.6 that I mentioned. I think somehow X has a serious regression problem -- otherwise I cannot explain what happened. I am also quite suspicious of some of the Updates failing and not completing but I still think X is the cause.

---

### Post by internalkernel on 2009-07-30
I'm starting to think the same... just don't understand why this has always worked before, then broke after using the wrong fglrx modules. It's almost like my card took a crap... 

I've tried updating to the latest X as well - xorg-crack ppa. no love up there either... I even tried Karmic, but it's version of X is not that much different either...

---

