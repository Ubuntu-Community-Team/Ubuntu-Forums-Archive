---
title: "Random lag in mplayer"
date: 2008-12-01
forum: Multimedia Software
---

### Post by unammed on 2008-12-01
Hi, I'm running Ubuntu 8.10 32bit with 2core processor 2.0Ghz. I got my PC hooked to LCD TV 1920x1080 @ 60Hz.

First thing I tried was using ffmpeg. Well I learnd that it wasn't multithreaded and I had laggy playback with my 1080p material ( 720p worked fine ).

Well after that I installed CoreAVC and 1080p runs great. With my both cores around 70%. But the thing is that randomly I get tiny lag in video, but audio runs well through S/PDIF. This can happen every 2 min, but CPU never jumps to 100%, so it's not running out of juice. I also get small tearing in video sometimes.

Using latest SVN build of mplayer and latest CoreAVC.
Using Ati's gfx drivers.

Specs:
E2180 @ 2.00Ghz
RADEON HD EAH 3450
1 GT DDR2 800Mhz

EDIT:

I've also used this same setting with Windows XP to watch HD movies using ffdshow + mpclassic and it worked good, so it's not hardware issue

---

### Post by unammed on 2008-12-02
Anyone? :mad:

---

### Post by shirilover on 2008-12-02
Try adding either -lavdopts fast:threads=2 to your mplayer command or add
lavdopts=fast:threads=2 to ~/.mplayer/config

---

### Post by unammed on 2008-12-02
Didn't help.

Still waiting for reply. Lag isn't bad, it just happens every now and then. Video lags not audio, and after that it runs good again.

Lag is only like 1 sec. Not even that, but it is noticable and I want to get smooth playback as possible

---

### Post by xtreme- on 2008-12-05
Hi,
I have the exact same problem on a box running updated version of Arch Linux 64 bit.
Hardware: Asus P5Q Pro, Intel Core 2 Duo E8500, Sapphire Radeon 4850.

I have tried increasing buffer size (by appending "cache=16384" to ~/mplayer/config), with no luck.
Now I really suspect that this is a ATI driver issue.
If I find no other solution, I will try to use the open source ATI driver instead.

I will let you know if I find a solution to this.

---

### Post by unammed on 2008-12-05
> **xtreme- said:**
> Hi,
Now I really suspect that this is a ATI driver issue.
If I find no other solution, I will try to use the open source ATI driver instead.

I will let you know if I find a solution to this.

Yeah, that is same conclusion I come with also. I haven't tried other drivers yet, but please let me know if you have any success

---

### Post by unammed on 2008-12-10
Problem solved!

I uninstalled Ati's closed drivers and decided to try Envy to reinstall them.

There is only one difference in xorg.conf:

Section "Module"
	Load	"glx"
	Disable "dri2"
EndSection

I don't know what else Envy configures, but no more random lags in video.

---

### Post by xtreme- on 2008-12-24
Hi,
Sorry for not getting back to you earlier, but I have not been around my computer lately.
However, it looks like you nailed the problem.

Do you (or anyone else) know which ATI driver version(s) this issue is related to?
I will check which version my box is running when I get back to it - but it will take some time.
Maybe a bug report should be filed?

I have a laptop running Ubuntu, using an ATI Mobility Radeon 9700, with driver version 8.47.3 (from dmesg), with no problems.
But this issue is probably not related to all ATI cards....

Thanks for any help!

---

### Post by xtreme- on 2009-01-01
Hi again,
Just wanted to let you know that upgrading my ATI fglrx drivers solved my problem too.
I am now running fglrx 8.56.4, and the video lag is gone.:)

---

