---
title: "Video choppy after resume from suspend"
date: 2009-07-30
forum: Multimedia Software
---

### Post by montini on 2009-07-30
OK, I decided to take my time to try to resolve this particular problem on Jaunty (ubuntu 9.04).

I watch my movies fullscreen, and they are showed correctly, but then I close my laptop lid to send it to sleep (suspend) and after I resume from suspend, sometimes video becomes choppy. By saying "choppy" I mean it freezes for a couple of seconds and after the next keyframe is displayed it is ok for some time - until next freeze. If I try to reboot, issues disappear - video is displayed correctly.

I don't know were to start searching, maybe someone has some thoughts?

I am using Thinkpad R61 with Nvidia Quadro NVS140M video card, 2GB RAM, proprietary video driver (at the moment I don't remember which version - but it is the recommended driver by Jaunty default installation - I think it's 180.??). I use compiz effects turned on as well (they don't interfere with fluent video display after reboots).

If you need more information or logs, just tell.

---

### Post by xc3RnbFO8P on 2009-07-30
Read this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337040]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337040")

---

### Post by montini on 2009-07-30
> **Ringi said:**
> Read this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337040]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337040")

You mean I should file a bug or what? Because there I don't see any solution for the particular problem - they are experiencing problems with major failure to wakeup graphics card from standby - which is not the case here: my laptop wakes up, but just the videos played after standby are displayed with freezes - it applies also to videos newly started, not the ones that should be immediately played after wakeup.

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

