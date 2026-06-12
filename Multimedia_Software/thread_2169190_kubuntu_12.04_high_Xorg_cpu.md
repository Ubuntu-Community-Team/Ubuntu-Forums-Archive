---
title: "kubuntu 12.04 high Xorg cpu"
date: 2013-08-20
forum: Multimedia Software
---

### Post by gobo7 on 2013-08-20
i have a new install of kubuntu 12.04 on an hp z600 w/ 2x X5650, 24gb memory.  
video card is ati FireMV 2250.

```

Linux acan 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

compiz is not installed.
desktop effects are disabled.
installed is Xserver-xorg-video-radeon v 1:6.14.99-git20111219.aacbd629-0ubuntu2.

over a number of days, cpu utilization of Xorg begins to climb.  today is 15
days uptime and Xorg is between 45 to 68%.  open apps are firefox, chromium and
a couple of terminal sessions.

firefox hardware acceleration is disabled.

```

top - 22:28:27 up 15 days, 23:40,  5 users,  load average: 0.51, 0.53, 0.70
Tasks: 208 total,   2 running, 206 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.5%us,  0.3%sy,  0.0%ni, 95.1%id,  0.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  24673504k total, 16019864k used,  8653640k free,   333188k buffers
Swap: 23436284k total,      540k used, 23435744k free,  6185864k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                     
 6953 root      20   0  548m 386m  41m R   50  1.6   2652:27 Xorg                                        
 7211 gobo      20   0  926m 163m  42m S    5  0.7  19:08.22 kwin                                        
 7227 gobo      20   0 1241m 148m  50m S    1  0.6  15:13.76 plasma-desktop                              
10765 gobo      20   0 1342m 406m  45m S    1  1.7  19:27.34 firefox                                     
16167 gobo      20   0  504m  37m  25m S    1  0.2  16:29.27 konsole                                     
 7205 gobo      20   0  273m  16m  12m S    0  0.1   0:00.59 kactivitymanage                             
15578 root      20   0     0    0    0 S    0  0.0   0:23.61 kworker/3:0                                 
23302 gobo      20   0 17476 1424  956 R    0  0.0   2:16.42 top                                         
    1 root      20   0 24452 2344 1344 S    0  0.0   0:02.04 init

```    
    
lsmod:
```

ttm                    76949  1 radeon
drm_kms_helper         46978  1 radeon
drm                   242038  6 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon

```


does anyone have suggestions on what to look at?  if you need additonal details,
please let me know.


thanks.

---

### Post by gobo7 on 2013-08-24
since there have been no comments, do i need to post this concern in hardware?  or is there a different forum that would be better suited?

---

