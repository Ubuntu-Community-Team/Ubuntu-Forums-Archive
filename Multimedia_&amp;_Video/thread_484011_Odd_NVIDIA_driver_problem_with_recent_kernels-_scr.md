---
title: "Odd NVIDIA driver problem with recent kernels- screen image shifted to left?"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by jharker on 2007-06-25
Hiya, folks!  I've run into a very unusual problem and was hoping someone could help me out by suggesting a solution or pointing me to a previous discussion of this problem (although I couldn't find one anywhere)...

I run an IBM Thinkpad G41, which includes an onboard nVIDIA GeForce FX Go5200 chip.  I'm running Feisty and have been for a while.  I use the proprietary NVIDIA driver from NVIDIA, version 9755, which I believe is the most current.

Anyway, my computer ran absolutely fine with kernel 2.6.20-14, but starting with 2.6.20-15 and continuing with 2.6.20-16, I've had an unusual problem.  (Of course, when a new kernel comes out I have to re-install the proprietary NVIDIA driver, but I do that without much trouble.)

My problem is, often (maybe all the time) after I "wake up" the computer from a suspend-to-RAM, at first everything works fine.  But usually a minute or two later, the screen suddenly shifts to the left.  This is difficult to describe, but basically, it's as if the entire image on the screen has moved to the left, with stuff that goes offscreen being wrapped around to the right side.  There's also a margin of black space that appears on the right side, before stuff from the left side wraps around.

I want to emphasize that in all ways the display has perfect quality, not static or any other problem.  It is simply offset to the left.

So, for example, with the standard Ubuntu desktop as a reference, when my screen shifts, the "Places" menu is in the upper left corner, and on the right side of the screen is a vertical bar of black, with the "Ubuntu" symbol just starting to creep in the upper right corner.

The funny thing is, although the *display* looks weird, the response is correct.  That is, I can use the mouse as if the screen was NOT messed up.  I just have to imagine that the menus are where they would normally be, and they all work just fine.

I've found a stopgap fix for this problem, which is to go to the "Applications->System Tools->NVIDIA X Server Settings" utility, select my display, and change the "GPU Scaling Method" from "Stretched" to "Centered" and back.  This will always fix the problem.

After this, usually within a minute later, and sometimes immediately, the *exact same thing* happens again, but this time with a larger shift, so that perhaps the last "s" in the "Places" menu is at the upper left corner of the screen.  Once again, the same fix works.

After two shifts, the display is fine and will work normally with no further shifts until I put the computer to sleep again.

I know for a fact that this problem did *not* happen with earlier kernels.  It has only showed up with the last two kernel revisions.

Has anyone seen this problem before, or have any suggestions?  Any advice is much appreciated!

---

### Post by marli on 2007-07-30
I also have this problem which happens when i come back from suspend.  It's been going on for a while, but the fix I use is to put it back into suspend and then resume a minute later and then it works fine.  Pretty annoying, but i've been too lazy to look into really fixing it.  I am running feisty on a dell xps m1210 and i don't think i installed the proprietary nvida driver.  I'm curious as to whether anyone has a real fix for this problem though.

---

### Post by dabl on 2007-09-13
This left-shifted screen phenomenon just popped up when I installed Gutsy Tribe 5 a week ago.  On the same hardware platform, Feisty has never had a display issue (runs Beryl great, etc.).

Was a fix identified -- is it an Nvidia driver thing, or a kdm thing (I'm running Kubuntu 64-bit)?

---

### Post by gerv on 2007-09-22
I've been seeing this as well.

Dell Dimension 8300 Desktop
Ubuntu Feisty 7.04 stable
nVidia Corporation NV34 [GeForce FX 5200] (rev a1)

xorg.conf:
Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection
...
Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

My fix is to do Switch User, but switch back to myself. This fixes it. I hadn't thought about a connection with hibernate, but there could well be. Even though my machine's a desktop, I hibernate it rather than switch it off completely. I also (I think) normally only see the problem once.

If more info is needed, let me know (gerv at gerv dot net).

---

### Post by dabl on 2007-09-22
I've still got the problem on my Gutsy Kubuntu system after yesterday's kernel upgrade and a lot of xorg and compiz updates. I was hoping it would just go away with the upgrades, but I guess not.  I'm going to try the user-switching thing, but that is a truly clunky fix, if it works at all.  :(


EDIT:  Nope, switching users on my system makes no difference in that gray bar on the right edge.  :(

---

### Post by ilia on 2007-10-24
I had the same issue with Feisty and nvidia proprietary drivers. Now I use Gutsy. I've tried to change from nvidia to nv driver in Xorg (without disabling nvidia kernel modules though) and I still have this problem. Usually the screen shifts when some hardware-related operation is performed. For example, if I unplug and plug a USB hub or insert a DVD disk the screen is almost certainly shifts. 
The shifts are always to the left and "discrete" - each time it shifts 50-100 pixels, so it's looks like jumps, not smooth scrolling. It may shift more than once at a time (I see several such "jumps" one after another).
With nvidia Xorg driver, I've used to restore the screen with 'xrandr -o normal" command (accidentally found that it works). The combination "xrandr -o left; xrandr -o normal" is OK too. It's seen from the previous posts, that many commands can restore the screen. The command just need to perform some kind of display re-initialization (probably initialize some hardware register or X-server data). 
After Gutsy installation yesterday, the system started to hang with the messages in logs started with "NVRM: Xid....". I decided to revert to "nv" driver and it the issue has gone. However, the issue with the screen shifts is still there. With "nv" driver the above command worked at the beginning, but right now it does not :( So I started to look for the real fix...

My configuration:
CPU: AMD64
Motherboard: Gigabyte GA-M57SLI-S4
Video: two identical PCI-E Gigabyte cards, based on NVidia GeForce 7300 GS (SLI bridge is not connected)
Monitor: two identical Samsung SyncMaster 203B, connected by DVI cable
Distro: Kubuntu Gutsy 64bit (had the same issue with Feisty 64bit)
Kernel: 2.6.22-14-generic (current Gutsy), had the same problem with 2.6.20-15-generic and 2.6.20-16-generic in Feisty.
Current software:
```

nvidia-glx-new                             100.14.19+2.6.22.4-14.9
nvidia-kernel-common                       20051028+1ubuntu7
xorg                                       1:7.2-5ubuntu13
xserver-xorg-video-nv                      1:2.1.5-1ubuntu1
linux-image-2.6.22-14-generic              2.6.22-14.46
linux-restricted-modules-2.6.22-14-generic 2.6.22.4-14.9
linux-ubuntu-modules-2.6.22-14-generic     2.6.22-14.37

```

Interestingly, although I run two X servers simultaneously (one for each card - "multihead" setup), the issue appears on the fist display only (display 0, it always the same video card).

If I don't find any info soon, I go to launchpad and open a bug.

---

### Post by ilia on 2007-10-24
I've searched for this problem on ubuntuforums and on the Launchpad. I've found the following threads and bugs, which describe the same issue.

Forum threads:
[LIST]
[*][Odd NVIDIA driver problem with recent kernels- screen image shifted to left?]("http://ubuntuforums.org/showthread.php?t=484011") - this thread
[*][Screen shifted to the left after last update]("http://ubuntuforums.org/showthread.php?t=317836")
[*][Screen shifts after suspend]("http://ubuntuforums.org/showthread.php?t=317152")
[*][suspend bring many trouble]("http://ubuntuforums.org/showthread.php?t=403652")
[/LIST]

Launchpad bugs:
[LIST]
[*][bug #75214]("https://bugs.launchpad.net/ubuntu/+bug/75214")
[*][bug #100105]("https://bugs.launchpad.net/ubuntu/+bug/100105")
[*][bug #139546]("https://bugs.launchpad.net/ubuntu/+bug/139546")
[/LIST]

So far nobody found a fix or the exact source of the bug. It seems to be related to NVidia cards only, but happens with "nv" driver too.

---

