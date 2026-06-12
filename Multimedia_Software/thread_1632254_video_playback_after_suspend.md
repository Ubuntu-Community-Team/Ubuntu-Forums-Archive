---
title: "video playback after suspend"
date: 2010-11-27
forum: Multimedia Software
---

### Post by raptx on 2010-11-27
Hi, 

I have a strange problem with video playback on my ubuntu 10.10 installation. On a fresh reboot, everything is fine. But when I suspend and resume, all flash playback (sites like youtube, hulu, and most noticeably in fullscreen mode) goes choppy. Sometimes playback in video players like VLC and Totem also becomes choppy after suspend/resume, but this is less common. The flash going choppy is consistent. Any ideas? I tried logging out, didn't work. The only thing that seems to work is full restart.

System/Settings:
Ubuntu 10.10 32-bit on 64-bit machine (Thinkpad T410).
Integrated graphics (I have nvidia optimus but I'm NOT using the nvidia drivers here)
No compiz enabled, desktop effects set to None.

Let me know if you need other info. Any help/ideas would greatly help!

Thanks!

EDIT: forgot to mention that I've checked previous posts on this, did find one with similar problem but no solution was offered.

---

### Post by grantheaslip on 2010-12-01
Hey raptx,

I'm having exactly the same issue&#8212;I'm not the only one! I'm on a Lenovo X201 with an Intel graphics chip. Here's my bug report on Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/676413](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/676413)

Feel free to weigh in there as well&#8212;it might help them out.

---

### Post by danzvash on 2010-12-07
Hi guys,

I have this annoying problem too.

My setup:

- Thinkpad W510
- Ubuntu 10.10 64 bit
- Nvidia drivers 260.19.06-0ubuntu1
- Flash 32bit v10.1 r102 running with nspluginwrapper (ubuntu default)


Normally, flash plays fine in full-screen (I'm running a resolution of 1920x1080).
After a single suspend-resume cycle, the same video plays very choppily, at maybe 1-5 frames a second - basically unwatchable.

This behaviour is cleared up after a reboot.


So what do we reckon?

Is this the fault of:
- nvidia drivers - NO (because you have it with Intel graphics)
- Xorg ?? - MAYBE
- Flash - MAYBE (I don't notice this with other video playback)
- Kernel - MAYBE


All thoughts appreciated ....

---

### Post by dargaud on 2010-12-07
Try to do a "killall npviewer.bin" in a shell, then reload the page with the flash video. Does it help ?

---

### Post by UKBB on 2010-12-13
I'm having this issue too and even had videos drop to grayscale instead of color, system specs are here. 

[http://ubuntuforums.org/showthread.php?t=1624004](http://ubuntuforums.org/showthread.php?t=1624004)

I will try the killall suggestion when I get home.

---

### Post by UKBB on 2010-12-17
> **dargaud said:**
> Try to do a "killall npviewer.bin" in a shell, then reload the page with the flash video. Does it help ?

When you say "in a shell" do you mean the terminal?

---

### Post by Brian96 on 2011-01-22
> **dargaud said:**
> Try to do a "killall npviewer.bin" in a shell, then reload the page with the flash video. Does it help ?

Been reading threads on this topic for weeks, and still have found no solution.

Bumping this and keeping my fingers crossed.

No, the command you recommended did not improve performance (ran both plan and as sudo).

---

### Post by frogpr on 2011-03-10
Same here on a HP Probook 4520s (i5-quad-core) with an ATI Mobility Radeon HD 5470 card and proprietary fglrx driver (Ubuntu 10.10)
Youtube videos run smoothly after boot, become laggy after first suspend/resume. Only noticable here for HD videos (720p and up), though. And only for flash videos, in vlc player all videos still run smoothly. Nothing seems to help but rebooting (even killing X, unloading fglrx, etc)

Have another laptop running on Debian (kernel 2.6.37), Lenovo W500. No such problems with the intel drivers used on this machine. Should try out the fglrx drivers for the ATI graphics card on this laptop (it's a switchable graphics system)...

So maybe it's an Ubuntu issue? Or the 2.6.35 Kernel used in 10.10?

---

### Post by Brian96 on 2011-03-20
I have the problem with 10.04.  It affects all fullscreen flash, not just HD, and not any other video.

However, for players that have a "pop out" video function, I can manually expand the video and it plays fine.  It is just the fullscreen function that results in choppy video, and that only after resuming from suspend.

Like others have posted, killing X does not make a difference.

---

### Post by clrg on 2011-04-05
For me, the issue started with Ubuntu Lucid kernel 2.6.32-26. Earlier kernels did not have the problem. Also seen on 2.6.35-based kernel.

I have a very reliable work-around though: disable hyper-threading processors before suspending, re-enable them after resume is finished. If I do this, the slowdown never occurs.

So I have this little script in /etc/pm/sleep.d/ which does the job:

```
#!/bin/sh
# Disable hyper-threading processor cores on suspend and hibernate, re-enable them
# on resume. Presumably helps for buggy nvidia behaviour.
# This file goes into /etc/pm/sleep.d/

case $1 in
        hibernate|suspend)
                echo 0 > /sys/devices/system/cpu/cpu1/online
                echo 0 > /sys/devices/system/cpu/cpu3/online
                ;;

        thaw|resume)
                echo 1 > /sys/devices/system/cpu/cpu1/online
                echo 1 > /sys/devices/system/cpu/cpu3/online
                ;;
esac
```



If you have a multi-core CPU with hyper-threading, you can try this and see if it removes the problem. The script needs to be adapted to CPU type (i.e. which processor ids need disabling/enabling, usually only the odd numbers from 1 to N-1, where N is the total number of logical processors that Linux sees when hyperthreading is enabled. It definitely works for me.

---

### Post by shellac on 2011-04-08
For thinkpad w510 / i7 820 QM - your work-around works fine!


#!/bin/sh
# Disable hyper-threading processor cores on suspend and hibernate, re-enable them
# on resume. Presumably helps for buggy nvidia behaviour.
# This file goes into /etc/pm/sleep.d/

case $1 in
        hibernate|suspend)
                echo 0 > /sys/devices/system/cpu/cpu1/online
                echo 0 > /sys/devices/system/cpu/cpu3/online
                echo 0 > /sys/devices/system/cpu/cpu5/online
                echo 0 > /sys/devices/system/cpu/cpu7/online
                ;;

        thaw|resume)
                echo 1 > /sys/devices/system/cpu/cpu1/online
                echo 1 > /sys/devices/system/cpu/cpu3/online
                echo 1 > /sys/devices/system/cpu/cpu5/online
                echo 1 > /sys/devices/system/cpu/cpu7/online
                ;;
esac


thx!

---

### Post by jimbo12345 on 2011-04-13
This fix has worked on my AMD dual core with ATI graphics also.  Flash player and compiz effects jerky after suspend/resume, but not now thanks to this!

#!/bin/sh
# Disable hyper-threading processor cores on suspend and hibernate, re-enable them
# on resume. Presumably helps for buggy nvidia behaviour.
# This file goes into /etc/pm/sleep.d/

case $1 in
hibernate|suspend)
echo 0 > /sys/devices/system/cpu/cpu0/online
echo 0 > /sys/devices/system/cpu/cpu1/online
;;

thaw|resume)
echo 1 > /sys/devices/system/cpu/cpu0/online
echo 1 > /sys/devices/system/cpu/cpu1/online
;;
esac

---

### Post by sauthess on 2011-05-06
Hi,

on my debian stable (that is impacted with same bug) on my HP Pavilion DM4-1162sf, the following do the job :


#!/bin/sh

# This file goes into /etc/pm/sleep.d/

case $1 in
hibernate|suspend)

echo 0 > /sys/devices/system/cpu/cpu1/online
echo 0 > /sys/devices/system/cpu/cpu2/online
echo 0 > /sys/devices/system/cpu/cpu3/online
;;

thaw|resume)

echo 1 > /sys/devices/system/cpu/cpu1/online
echo 1 > /sys/devices/system/cpu/cpu2/online
echo 1 > /sys/devices/system/cpu/cpu3/online
;;
esac

Thanks !

---

### Post by antimirov on 2011-05-15
2sauthess: the script helped me, thanks!

Guys, do you know if there is a bug reported somewhere so I can subscribe to it?

---

### Post by gsirus on 2011-05-17
Worked for me on thinkpad T410 with Nvidia graphic

thanks!!!

---

### Post by sauthess on 2011-05-18
Ubuntu bug report :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/676413]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/676413")

Regards

---

### Post by martini1179 on 2011-05-27
This bug also appears in Lucid.  To all of those that are having this problem, does Flash video performance still stutter in fullscreen if you disable Compiz? If it plays smoothly, then that's both a workaround and a clue. This bug has nothing to do with intel video drivers, or nvidia. From this layman's perspective, it looks like it's either a kernel bug, a compiz bug, or a flash bug.  For me (and likely for others for whom my workaround works), this bug is reproducible 100% of the time after suspending TWICE. Suspending only once from a fresh reboot does not reproduce the bug for me. Hibernate doesn't impact flash performance at all. I have no idea when this bug first appeared, since I always used to shut down the machine completely at the end of the day.

---

### Post by AgenT on 2011-05-27
Awesome! This works on Intel video card's as well! Ubuntu 11.04 (natty). On my system I  had to add cpu2 to the script.

Thank you so much clrg!

My script that was added to /etc/pm/sleep.d/10_sleep_video_fix (make sure to chmod it to 755):
```

#!/bin/sh
# Disable hyper-threading processor cores on suspend and hibernate, re-enable them
# on resume. Presumably helps for buggy nvidia behaviour.
# This file goes into /etc/pm/sleep.d/

case $1 in
    hibernate|suspend)
        echo 0 > /sys/devices/system/cpu/cpu1/online
        echo 0 > /sys/devices/system/cpu/cpu2/online
        echo 0 > /sys/devices/system/cpu/cpu3/online
        ;;
    
    thaw|resume)
        echo 1 > /sys/devices/system/cpu/cpu1/online
        echo 1 > /sys/devices/system/cpu/cpu2/online
        echo 1 > /sys/devices/system/cpu/cpu3/online
        ;;
esac

```[SIZE=3]UPDATE #1:
**[COLOR=Red]WARNING![/COLOR]**[/SIZE] 
The solutions given by myself as well as others will fix video and flash playback, but will **KILL** any **virtualization** you are doing! This virtualization freeze will also cause many problems like:

[LIST]
[*] It will totally **break Xorg** (for me, I end up having half of a monitor repeated).
[*] It will also **freeze your kernel** at certain points which means **DEAD computer** until you force cut-power!
[/LIST]
 I have only seen this happen when going to sleep with some virtualized environment running (for me, that's virtualbox)![SIZE=3]
[/SIZE]

---

### Post by sauthess on 2011-05-28
Hi,

Here is a script that should work on all our computer (instead of looking for CPU numbers...) :


#!/bin/sh
# Disable hyper-threading processor cores on suspend and hibernate, re-enable them
# on resume. Presumably helps for flash resume problem.
# This file goes into /etc/pm/sleep.d/

case $1 in
hibernate|suspend)
for i in /sys/devices/system/cpu/cpu*/online; do echo "0">$i; done
;;

thaw|resume)
for i in /sys/devices/system/cpu/cpu*/online; do echo "1">$i; done
;;
esac

I think it will be easier that checking cpus numbers...

For me, it's not an ubuntu bug (I have it on debian stable too) and not a compiz one too (as disabling cpus is a workaround...). 

Hope this "new" scripts helps few of us ;)

Regards,

---

### Post by didjital1984 on 2011-07-06
> **sauthess said:**
> Hi,

Here is a script that should work on all our computer (instead of looking for CPU numbers...) :


#!/bin/sh
# Disable hyper-threading processor cores on suspend and hibernate, re-enable them
# on resume. Presumably helps for flash resume problem.
# This file goes into /etc/pm/sleep.d/

case $1 in
hibernate|suspend)
for i in /sys/devices/system/cpu/cpu*/online; do echo "0">$i; done
;;

thaw|resume)
for i in /sys/devices/system/cpu/cpu*/online; do echo "1">$i; done
;;
esac

I think it will be easier that checking cpus numbers...

For me, it's not an ubuntu bug (I have it on debian stable too) and not a compiz one too (as disabling cpus is a workaround...). 

Hope this "new" scripts helps few of us ;)

Regards,
Worked for me. Thanks!

---

### Post by UKBB on 2011-07-31
Not sure if it was due to an update that fixed it or the video card I installed (previously on board graphics only) but this problem has gone away for me.

---

