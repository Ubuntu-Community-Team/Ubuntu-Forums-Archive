---
title: "HDMI audio not working after update"
date: 2010-07-26
forum: Multimedia Software
---

### Post by spiderworm on 2010-07-26
Hello,

I installed Ubuntu 10.04 a few days ago and HDMI audio worked out of the box (with the nVidia drivers enabled).  Today I did a system update and (among other problems) there is no more sound coming over HDMI.  I'm not really sure what to do to diagnose this problem... where would I start?

Thanks!

---

### Post by jda8818 on 2010-07-26
spiderworm:

I had a similar problem.  If you can get the attention of Lidex (a responder in this support category), he will fix you up.

To get started, however, he might ask you to post the results of these four commands:

```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#*
```Check out my previous thread. Good Luck!

JA

---

### Post by spiderworm on 2010-07-27
Here is the output from the commands you suggested... from what little I know of Linux audio, everything looks fine here to me:

uname -a```

Linux spidey 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux

```
aplay -l```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
dpkg -l | grep "alsa"```

ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  linux-backports-modules-alsa-2.6.32-24-generic 2.6.32-24.17                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.24.25                                    Backported drivers for alsa-driver snapshot.

```
head -n 1 /proc/asound/card*/codec#*```

Codec: Nvidia MCP77/78 HDMI

```

Anyone have any ideas?  Would like to be able to listen to music on this machine again...

---

### Post by spiderworm on 2010-07-27
Going through my logs, I see several entries that look like this:

```

pulseaudio[1815]: shm.c: shm_open() failed: Permission denied

```

... as well as several like this:

```

pulseaudio[1579]: core.c: failed to allocate shared memory pool. Falling back to a normal memory pool.

```

I assume the two are related, but I don't know for certain.  Also, I see a lot of this:

```

pulseaudio[1769]: ratelimit.c: (number) events suppressed

```

I don't know if these are related to the issue or not, but I'm posting it here just in case it helps somehow.

---

### Post by spiderworm on 2010-07-31
bump

---

### Post by lidex on 2010-08-01
Try removing config files. 
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
**Logout/in.**

[http://ubuntuforums.org/showthread.php?t=1466111](http://ubuntuforums.org/showthread.php?t=1466111)
[http://ubuntuforums.org/showthread.php?t=1532355](http://ubuntuforums.org/showthread.php?t=1532355)

---

### Post by spiderworm on 2010-08-02
Thanks, Lidex, for helping me out!

I was able to remove ~/.pulse without a problem.  The asound files, however, couldn't be removed because they didn't exist.  Perhaps I don't have alsa and I have to install it or something like that?  If my system came with it installed, I can't for the life of me guess why they would have been uninstalled.

---

### Post by lidex on 2010-08-02
> **spiderworm said:**
> Thanks, Lidex, for helping me out!

I was able to remove ~/.pulse without a problem.  The asound files, however, couldn't be removed because they didn't exist.  Perhaps I don't have alsa and I have to install it or something like that?  If my system came with it installed, I can't for the life of me guess why they would have been uninstalled.

Those are optional config files - no problem there. Did you check out the links?

---

