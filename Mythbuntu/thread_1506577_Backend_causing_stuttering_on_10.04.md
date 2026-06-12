---
title: "Backend causing stuttering on 10.04"
date: 2010-06-10
forum: Mythbuntu
---

### Post by dnilsson on 2010-06-10
Hi,

I have recently upgraded my backend server from Debian etch to Ubuntu server 10.04. During this process the machine was reinstalled from scratch, but the sql tables with all mythtv setting were moved over from the old machine and upgraded. Mostly the process was smooth, and everything is running now.

However, I have an issue with stuttering that was not present on the old config (Debian etch, kernel 2.6.18 and MythTV 0.21). I'm 99% sure that the problem is caused by the backend because it happens at the same time in the videostream on all frontends as well as if the video is played back several times on the frontend. 

Backend specs are 3.0GHz Pentium 4 machine, 2GB RAM. Root filesystem is a SW RAID1 device with two SATA drives for redundancy. MythTV is recording to a dedicated third 1TB SATA drive. Ext4 filesystems are used throughout. The SW RAID1 root filesystem was not present before the system was upgraded, one drive was added to the system to achieve this during the upgrade. The framegrabber is an old BT848 card receiving over S-Video from an IPTV box.

There is nothing showing in either the frontend and backend logs that could indicate a problem. And now the really strange thing: If I increase the backend loglevel to "all" the problem becomes significantly worse, ie completely unusable. When this happens, the frontend logs are showing pre-buffer pause messages in the logfile.

The backend is running quite a few other processes, but only mythbackend is actually using CPU (around 35%). System load is however around 1.5 (?). With loglevel set to "all" the SW RAID1 root filesystem where the logs are written to is being utlized to around 60% with 150tps according to sar. With the default loglevel where the issue happens maybe every 10seconds the root filesystem is not really utilized at all according to sar and the dedicated MythTV disk also has very modest utilization.

So, sorry for the long post.... What is going here? How to debug this further?

Thanks
Daniel

---

### Post by dualboot on 2010-06-10
Hi Daniel,
I may have a similar problem.  I have a combined frontend/backend.  Video stuttering after a few seconds of playback.  Upgraded to 10.04 a few weeks back, but this only started a few days ago.

Perhaps you could confirm if you see the same symptoms ?

I noticed in 'top' that though there is no high cpu, the 'wa' figure is up at around 50pc whenever the video stutters.  I have two sata disks and so I don't believe it is a faulty disk. Same effect on either.  When the 'wa' goes down the video if normal too.

I don't believe its actually either frontend or back end program but something at a lower level.

I get the same symptoms if I 'play' a file from the command line with vlc.  Even copying a file from one disk to the other with mv hits the wa 

Intrestingly I attached a USB hard drive, and playing an archived .mpg file from that is fine.  Sometimes it is fine for many many minutes.

Sorry to hijack your thread, if you don't have the same thing or can't test just ignore - hope you get it sorted anyhow.

---

### Post by dnilsson on 2010-06-10
Hi,

I'm not sure we're seeing the same issue. Since there is a lag of some seconds between activity on the backend and seeing the result on the frontend it is difficult to correlate events on the backend to the stuttering. In any case, %wa (waiting) never goes about 5% on my backend while watching TV and seeing stuttering video.

```
top - 22:57:48 up  6:26,  6 users,  load average: 1.15, 1.02, 0.70
Tasks: 249 total,   1 running, 248 sleeping,   0 stopped,   0 zombie
Cpu(s): 32.6%us,  1.7%sy,  0.0%ni, 62.1%id,  3.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2059868k total,  1994596k used,    65272k free,    77576k buffers
Swap:  4193272k total,      676k used,  4192596k free,  1295400k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                         
 8206 mythtv    20   0  358m  54m  20m S 33.8  2.7   3:14.85 mythbackend                     
  288 root      20   0     0    0    0 S  0.3  0.0   0:00.97 kdmflush                        
12402 daniel    20   0  2544 1268  904 R  0.3  0.1   0:01.83 top                             
    1 root      20   0  2788 1604 1168 S  0.0  0.1   0:00.39 init                                

```

---

### Post by dnilsson on 2010-06-10
Hi,

I put up a sample [here]("http://www.dnil.se/temp/14_20100610232050.nuv") of what the video looks like, the stuttering that I'm talking about occurs around 10, 22 and 43 seconds into the stream. I play this back on a completely different machine using mplayer so mythtv is not involved at all.

---

### Post by dnilsson on 2010-06-16
So... after a lot of debugging, a number of kernel and initrd builds, different framefrabber cards etc I found out where the problem was. The video source for MythTV is an external IP TV box, this box has been working fine for several years but decided to give up on me right around the same time as I did a major software upgrade on the MythTV backend server. What is really annoying is that I have actually checked the quality of the video from this box a couple of times by bringing it out from the server room and connecting it to a regular TV. This worked just fine, but it seems like the temperature in the server room was just high enough to trigger the problems.

With a new IP TV box everything is running fine again. The issue with the log level of the mythtv backend process is probably a separate issue where video stuttering was actually added by the server to an already bad stream from the source.

Many hours went into this, lesson learned once more is garbage in garbage out...

---

