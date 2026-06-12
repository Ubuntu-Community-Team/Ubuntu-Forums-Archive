---
title: "I have a problem after install veetle"
date: 2010-10-14
forum: Multimedia Software
---

### Post by cravonic on 2010-10-14
Hello

I have the problem when install veetle. My problem is the same that:
[http://ubuntuforums.org/showthread.php?t=1295076]("http://ubuntuforums.org/showthread.php?t=1295076")

I made this:
chown user:user /home/user/.ICEauthority
chmod 644 /home/user/.ICEauthority

And the error mensage in boot disapear.
But I have a process that put CPU in the maximum and i don't understand what process cause this. 
The bar of change volume don't work and hot-keys of change volume.
The problem process appear in the top output.

My top output:

```
top - 10:11:46 up 18 min,  2 users,  load average: 2.25, 2.74, 2.17
Tasks: 147 total,   3 running, 144 sleeping,   0 stopped,   0 zombie
Cpu(s): 72.4%us, 24.0%sy,  0.2%ni,  0.1%id,  2.9%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   1025028k total,   684212k used,   340816k free,    51696k buffers
Swap:   489940k total,        0k used,   489940k free,   296440k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
 1248 miguel    20   0  332m 136m  31m S 11.1 13.6   2:29.20 firefox-bin                                                     
 1390 miguel    20   0 54704  16m 9.9m S  9.2  1.7   1:11.70 indicator-apple                                                 
 1965 miguel    20   0  202m  70m  23m S  9.2  7.0   4:12.27 plugin-containe                                                 
  817 root      20   0 46204  26m  12m R  7.4  2.6   1:02.69 Xorg                                                            
 1201 miguel    20   0 68544  25m 9468 S  5.5  2.6   0:28.06 compiz                                                          
 1432 miguel    20   0 85356 4592 3656 S  5.5  0.4   1:02.73 indicator-sound                                                 
  713 root      20   0 18772 3268 2720 S  1.8  0.3   0:03.92 gdm-binary                                                      
 1079 miguel    20   0  3192 1312  608 S  1.8  0.1   0:19.64 dbus-daemon                                                     
 1221 miguel    20   0 48484  17m  13m S  1.8  1.7   0:08.61 gnome-panel                                                     
 1225 miguel    20   0 90676  20m  15m S  1.8  2.0   0:07.75 nautilus                                                        
 3966 miguel    20   0 32268  15m 8960 S  1.8  1.6   0:19.60 python                                                          
    1 root      20   0  2808 1628 1168 S  0.0  0.2   0:00.31 init                                                            
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      20   0     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0                                                     
    5 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      20   0     0    0    0 S  0.0  0.0   0:00.48 events/0                                                        
    7 root      20   0     0    0    0 S  0.0  0.0   0:00.00 cpuset                                                          
    8 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khelper                                                         
    9 root      20   0     0    0    0 S  0.0  0.0   0:00.00 netns                                                           
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.00 async/mgr                                                       
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 pm                                                              
   12 root      20   0     0    0    0 S  0.0  0.0   0:00.00 sync_supers                                                     
   13 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default                                                     
   14 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                   
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.02 kblockd/0                                                       
   16 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                          
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                    
   18 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kacpi_hotplug                                                   
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.20 ata/0                                                           
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                         
   21 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd    
```

The indicator-apple and indicator-sound is cause the problem of the sound.
But I don't understand what process put the processor in 100%

Thanks for attention

Sory for my poor english.

---

