---
title: "x3100 - GM965 chipset &amp; ubuntu 9.04"
date: 2009-04-18
forum: Multimedia Software
---

### Post by hackercoolio on 2009-04-18
the best ubuntu version so far the worked great with compiz and 3D screen savers and etc. was 8.04 (On dell inspiron 1525 integrated x3100 graphic card)


How ever when 8.10 was released i installed it.. the panels crashed every time I boot in to Ubuntu.. and few screen lags once in a while.. and compiz did work but performance was lowerd. (even after all the update) so i switched back to 8.04.


i thought now 9.04 had some major changes in graphics drivers(thats what i saw on the 9.04 changes) and today I installed it.. 
Result: after getting all the update packs of the server.. my 9.04 wont even support compiz.. 

and well crashes more often ( even while switching tasks)

just came out of a boring exam bad mood.. whats this ? =(

any help fixing it up would be appreciated thanks =) till that ill have to use windows.

---

### Post by mjwhitfield on 2009-04-20
I've just installed 9.04 (64 bit) RC on my Aspire 5315 which has the GM965 card. Before I ran the updates compiz was working, however it won't fire up following the updates.  I've googled and there's a bunch of bugs in launchpad and it appears there are a lot of issues with the new Intel drivers.

Has anyone found a workaround until a fix is released?

---

### Post by pro1ove on 2009-04-24
It seems that Intel GM 965 series have been blacklisted in compiz

open the file : sudo gedit /usr/bin/compiz

change the line : T="$T 8086:2a02 " # Intel GM965

to : # T="$T 8086:2a02 " # Intel GM965

save it and compiz can work again.

---

### Post by stukpixel on 2009-04-24
I'm not entirely sure if the x3100 is being used right- my computer is lagging a fair bit with compiz activated.

---

### Post by jordan420 on 2009-04-24
Im on 9.04 with a Dell Vostro. gm965 , X3100.. you know. i've enabled UXA accelerating and compiz works better. it seems that the work bing done on the driver includes migrating from EXA to the above. the only problem is that xorg uses a lot of resources... kind of sparatic. its real fast when its not sluggish.. you know? but anyway try changing your xorg.conf to ```

```Section "Device"
	Identifier	"Configured Video Device"
	# ...
        Option        "AccelMethod" "uxa"
EndSection```

```

---

### Post by mjwhitfield on 2009-04-24
> **jordan420 said:**
> Im on 9.04 with a Dell Vostro. gm965 , X3100.. you know. i've enabled UXA accelerating and compiz works better. it seems that the work bing done on the driver includes migrating from EXA to the above. the only problem is that xorg uses a lot of resources... kind of sparatic. its real fast when its not sluggish.. you know? but anyway try changing your xorg.conf to ```

```Section "Device"
	Identifier	"Configured Video Device"
	# ...
        Option        "AccelMethod" "uxa"
EndSection```

```Yeah I've had mine set to UXA for the past day and I've noticed the same thing.

---

### Post by jordan420 on 2009-04-25
is anybody else locking up TOO often with this? at first on EXA i couldnt use the system for 15 minutes. with UXA it locks up alot but it seems randomsomestimes i can use it for a day sometimes a few minutes.. any hope for a fix? im thinking about trying an intel-xorg driver from xorg-edgers.

---

### Post by mjwhitfield on 2009-04-25
> **jordan420 said:**
> is anybody else locking up TOO often with this? at first on EXA i couldnt use the system for 15 minutes. with UXA it locks up alot but it seems randomsomestimes i can use it for a day sometimes a few minutes.. any hope for a fix? im thinking about trying an intel-xorg driver from xorg-edgers.I've not had any lockups with UXA. You sure it's using it? Have you checked your xorg logs?

---

### Post by jordan420 on 2009-04-26
hey i upgraded the kernel and a few other packages dealing with xorg and what not and the performance is MUCH better. no problems whatsoever running compiz with UXA. the only problem is thanks to the kernel upgrade my BCM 4328 wireless is disabled. almost definitely a kernel thing.

---

### Post by mjwhitfield on 2009-04-26
> **jordan420 said:**
> hey i upgraded the kernel and a few other packages dealing with xorg and what not and the performance is MUCH better. no problems whatsoever running compiz with UXA. the only problem is thanks to the kernel upgrade my BCM 4328 wireless is disabled. almost definitely a kernel thing.Which packages and where from? :)

---

### Post by jordan420 on 2009-04-26
to kernel 2.6.30rc3 xserver-xorg-video-intel_2.7.0 libdrm-intel1_2.4.9-1 and libdrm2_2.4.9-1     from kernel.ubuntu.com and ppa

---

### Post by xxernestoxx on 2009-04-26
> **pro1ove said:**
> It seems that Intel GM 965 series have been blacklisted in compiz

open the file : sudo gedit /usr/bin/compiz

change the line : T="$T 8086:2a02 " # Intel GM965

to : # T="$T 8086:2a02 " # Intel GM965

save it and compiz can work again.

Thanks a lot man that fixed it for me.

---

### Post by mjwhitfield on 2009-04-26
> **xxernestoxx said:**
> Thanks a lot man that fixed it for me.If you haven't changed to UXA, you may experience X locking up.

---

### Post by mjwhitfield on 2009-04-26
> **jordan420 said:**
> to kernel 2.6.30rc3 xserver-xorg-video-intel_2.7.0 libdrm-intel1_2.4.9-1 and libdrm2_2.4.9-1     from kernel.ubuntu.com and ppaWhich PPA? :)

---

### Post by dixon on 2009-04-26
> **mjwhitfield said:**
> Which PPA? :)
Here are the most recent "stable" drivers
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)

---

### Post by mjwhitfield on 2009-04-26
> **dixon said:**
> Here are the most recent "stable" drivers
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu)Thanks for the link.  Added the ppa and run a system update which updated 13 new packages. Compiz still seems to do the same stuttering thing. Shall I stop using UXA? Or is there something else I need to do?

---

### Post by andrelom on 2009-04-26
> **pro1ove said:**
> It seems that Intel GM 965 series have been blacklisted in compiz

open the file : sudo gedit /usr/bin/compiz

change the line : T="$T 8086:2a02 " # Intel GM965

to : # T="$T 8086:2a02 " # Intel GM965

save it and compiz can work again.

Thanks, that fixed it for me to.

---

### Post by jordan420 on 2009-04-26
hey guys im using xorg edgers ppa and the performance is outstanding with gm965.(uxa enabled)

---

### Post by jordan420 on 2009-04-27
whitfield: did you manually change the /proc/mtrr ? this alone made a huge difference for me. try doing ```
echo "base=0xb0000000 size=0x10000000 type=write-combining" > /proc/mtrr

```

---

### Post by calhau0 on 2009-05-03
Just installed "xserver-xorg-video-intel 2.2.7.0.1" drivers and the performance is better than UXA

---

### Post by alex.rayu on 2009-05-04
With me, on x3100, HP laptop (Compaq 6720s) uxa runs glxgears at ~350 fps. Without uxa, it runs 1,5 times faster. But such framerate is not much.

---

### Post by densou on 2009-05-04
> **alex.rayu said:**
> With me, on x3100, HP laptop (Compaq 6720s) uxa runs glxgears at ~350 fps. Without uxa, it runs 1,5 times faster. But such framerate is not much.

repeating it again: glxgears is NOT a benchmark, use */usr/lib/xscreensaver/glblur -window -fps* instead :popcorn:


anyway it's tough to improve Intel GMA experience for everyone: I noticed this OS give a very subjective answer with same settings as well (and same/similar hardware specs).... :(

however Fedora 11 Preview worked out-of-the-box as never seen among Linux Distros :KS

---

### Post by wyth on 2009-05-04
Just because:

See the [HOWTO: Jaunty Intel Graphics Performance Guide]("http://ubuntuforums.org/showthread.php?t=1130582") thread for more info on what you can do.  There's already nearly 30 pages on tips and tricks to try out with the blacklisted Intel driver.

---

