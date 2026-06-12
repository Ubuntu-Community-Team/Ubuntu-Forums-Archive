---
title: "High PulseAudio cpu usage"
date: 2009-03-22
forum: Multimedia Software
---

### Post by usercontrol on 2009-03-22
hi!

Since few days i'm observing a high cpu usage during playing music - about 30% by PulseAudio process. 

My hardware is:
Sony Vaio VGN-AR21M with C2D 1,86 cpu, 2 GB RAM, Toshiba Multimedia Center (SoundBlaster Live! 24bit External usb).

What is wrong? Which config file need you to detect my problem?


top:
```
top - 21:46:08 up  6:09,  2 users,  load average: 1.41, 1.28, 1.20
Tasks: 170 total,   1 running, 169 sleeping,   0 stopped,   0 zombie
Cpu(s): 27.4%us,  4.8%sy,  0.0%ni, 67.5%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2071392k total,  2014600k used,    56792k free,   130692k buffers
Swap:  1052216k total,     1972k used,  1050244k free,  1191628k cached
 Unknown command - try 'h' for help 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
25807 usercont  20   0 41400 4604 3328 S   29  0.2  15:28.98 pulseaudio         
32412 usercont  20   0  322m 147m  31m S   20  7.3  15:25.21 firefox            
 8792 root      20   0  147m  65m  14m S    5  3.3  18:32.65 Xorg               
10405 usercont  20   0  790m 123m  48m S    4  6.1  17:01.43 amarok             
 9368 usercont  20   0 75264  36m  11m S    4  1.8   7:55.72 compiz.real        
21957 usercont  20   0 90840  22m  12m S    3  1.1   0:00.78 gnome-terminal     
 9469 usercont  20   0 37920  19m  10m S    2  0.9   6:25.43 python             
 8624 root      20   0  3472 1160 1004 S    1  0.1   0:16.64 hald-addon-stor    
 9377 usercont  20   0 21648 5760 4312 S    1  0.3   0:28.70 gnome-screensav    
 9386 usercont  20   0 82332  29m  17m S    1  1.4   3:48.93 gnome-panel        
 9426 usercont  20   0 39572  15m  10m S    1  0.8   0:22.58 stickynotes_app    
 9476 usercont  20   0 46976  21m  11m S    1  1.1   1:47.76 python             
20453 usercont  20   0 49484  18m  11m S    1  0.9   0:01.14 gedit              
 9381 usercont  20   0 36276  14m 8968 S    0  0.7   1:33.93 gtk-window-deco    
 9387 usercont  20   0  140m  45m  21m S    0  2.2   4:27.51 nautilus           
    1 root      20   0  3056 1896  576 S    0  0.1   0:01.40 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
```

---

### Post by change_mode on 2009-03-22
If you search a bit, there are a few topics in these forums that explain how to improve your PulseAudio configuration. The default configuration isn't that good.

Alternatively you can go to the sound options and set all the options to ALSA, so PulseAudio won't be used anymore.

---

### Post by jjacobs2 on 2009-03-22
Perhaps your CPU is being dramatically downclocked to save power and that's why the pulseaudio usage seems high.  Try checking what speed the cpu is running at with cat /proc/cpuinfo and look for cpu MHZ.

---

