---
title: "Much higher load averages with recent builds of 2.6.34"
date: 2010-05-31
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by paul_in_london on 2010-05-31
I've been seeing much higher load averages than usual with the current and recent stock kernels.

```
uname -a
Linux maverick 2.6.34-5-generic #12-Ubuntu SMP Fri May 28 21:03:32 UTC 2010 i686 GNU/Linux
```

Here are a couple of snapshots from **top**:

```
top - 18:38:12 up 50 min,  2 users,  load average: 1.79, 2.15, 1.90
Tasks: 181 total,   5 running, 176 sleeping,   0 stopped,   0 zombie
Cpu(s):  7.3%us,  7.4%sy, 13.2%ni, 71.5%id,  0.5%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   3354424k total,  1097092k used,  2257332k free,    98136k buffers
Swap:        0k total,        0k used,        0k free,   493056k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                         
 3541 paul      28   8  254m  49m  17m R   87  1.5  24:53.51 /usr/lib/opera//operapluginwrapper 12 57 /usr/lib/mozilla/plugins/flashplugin-alternative.so                                                                                    
 1091 root      20   0 61304  45m  14m R   51  1.4  11:30.38 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-afdUjT/database -nolisten tcp vt7                                                                                    
 3481 paul      24   4  310m 228m  19m S   37  7.0   9:47.33 /usr/lib/opera/opera                                                                                                                                                            
 3276 paul      24   4 72264  58m  15m R   35  1.8   8:39.06 /usr/bin/compiz                                                                                                                                                                 
 3280 paul       9 -11  156m 5328 4124 S    4  0.2   1:54.68 /usr/bin/pulseaudio --start --log-target=syslog                                                                                                                                 
 3408 paul      20   0 55272  14m  10m S    2  0.4   0:08.20 gnome-terminal                                                                                                                                                                  
 5505 paul      20   0  2612 1112  820 R    2  0.0   0:00.01 top -cSb n
```

and

```
top - 18:47:56 up  1:00,  2 users,  load average: 1.46, 1.60, 1.71
Tasks: 181 total,   2 running, 179 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.7%us,  7.1%sy, 13.5%ni, 72.2%id,  0.4%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   3354424k total,  1104412k used,  2250012k free,   100540k buffers
Swap:        0k total,        0k used,        0k free,   494924k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                         
 3541 paul      28   8  254m  49m  17m S   58  1.5  30:18.47 /usr/lib/opera//operapluginwrapper 12 57 /usr/lib/mozilla/plugins/flashplugin-alternative.so                                                                                    
 3276 paul      24   4 72196  58m  15m S   12  1.8   9:59.17 /usr/bin/compiz                                                                                                                                                                 
 1091 root      20   0 61304  45m  14m S   10  1.4  12:54.36 /usr/bin/X :0 -nr -verbose -auth /var/run/gdm/auth-for-gdm-afdUjT/database -nolisten tcp vt7                                                                                    
 3481 paul      24   4  321m 232m  20m S    6  7.1  10:55.78 /usr/lib/opera/opera                                                                                                                                                            
 3280 paul      24   4  156m 5328 4124 S    4  0.2   2:18.72 /usr/bin/pulseaudio --start --log-target=syslog                                                                                                                                 
 5645 paul      20   0  2612 1112  820 R    2  0.0   0:00.02 top -cSb n 1                                                                                                                                                                    
    1 root      20   0  2860 1724 1248 S    0  0.1   0:53.93 /sbin/init                                                                     
```

The most recent daily build of 2.6.34-999 (26-May-2010) still maxes out **one of** my cores so I'm not using that.

A couple of days ago Phoronix published some worrying benchmarks:

[http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2635_fail&num=1)

Anyone else seeing higher load than usual? I did experience **udev** hogging the system around the time **zika** posted about it ([http://ubuntuforums.org/showthread.php?t=1491332&highlight=udev](http://ubuntuforums.org/showthread.php?t=1491332&highlight=udev)), but that doesn't seem to be the explanation at the moment.

---

### Post by taavikko on 2010-05-31
Don't see anything out of ordinary, just that opera has issues runnign flash, which causes the cpu to soar (yeah, flash ;) )

```
:~$ top

top - 21:10:25 up  6:32,  3 users,  load average: 0.09, 0.27, 0.36
Tasks: 254 total,   1 running, 253 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.2%us,  0.1%sy,  0.0%ni, 99.6%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   6107620k total,  2311264k used,  3796356k free,   117628k buffers
Swap:   975868k total,        0k used,   975868k free,  1348968k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                
 1304 root      20   0  130m  40m  20m S    1  0.7   7:35.84 Xorg                                   
 1550 tuomas    20   0  288m  58m  22m S    1  1.0   3:04.38 compiz                                 
 6245 tuomas    20   0 19408 1416  964 R    1  0.0   0:00.07 top                                    
 1534 tuomas    20   0  297m  10m 8000 S    0  0.2   0:04.53 gnome-settings-                        
 1633 tuomas    20   0  168m  10m 8344 S    0  0.2   0:04.03 gtk-window-deco                        
 1807 tuomas    20   0  204m  15m  10m S    0  0.3   0:06.09 gnome-terminal                         
 6166 tuomas    20   0  430m  18m  14m S    0  0.3   0:02.99 chromium-browse                        
    1 root      20   0 23844 1996 1300 S    0  0.0   0:01.95 init
```

---

### Post by andrewthomas on 2010-05-31
> **paul_in_london said:**
> The most recent daily build of 2.6.34-999 (26-May-2010) still maxes out of my cores so I'm not using that.

Should be ok now (when they get around to building the latest)
[http://ubuntuforums.org/showpost.php?p=9389319&postcount=6](http://ubuntuforums.org/showpost.php?p=9389319&postcount=6)

---

### Post by Slug71 on 2010-05-31
2.6.35-RC1 is out. Will probably land in the repos soon.

---

### Post by paul_in_london on 2010-05-31
Hi **taavikko**,

Your load figures are very typically of the sort of thing I normally see even when I'm streaming video and have lots of tabs open so I was wondering what other people might be seeing...

---

### Post by paul_in_london on 2010-05-31
> **Slug71 said:**
> 2.6.35-RC1 is out. Will probably land in the repos soon.

It'll be interesting to see what happens with 2.6.35...

---

### Post by zika on 2010-05-31
I've had the problem with udev in 2.6.34-999 [http://ubuntuforums.org/showthread.php?t=1491332](http://ubuntuforums.org/showthread.php?t=1491332) ... Waiting for 2.6.35-999

Update: Problem solved. Works like a butterfly...

---

### Post by paul_in_london on 2010-06-01
```
paul@maverick:~$ uname -a
Linux maverick 2.6.35-020635rc1-generic #020635rc1 SMP Tue Jun 1 18:38:58 UTC 2010 i686 GNU/Linux
paul@maverick:~$
```

Load averages with 2.6.35-rc1 are now definitely better than I've been seeing with the more recent 2.6.34 builds, but still pretty fscked up - fluctuating up and down instead of staying consistently low.

Not spiking as wildly anymore though (so far) and certainly better than I've seen for a little while :-)

---

### Post by Longinus00 on 2010-06-01
If your first post is any indication, your load averages have everything to do with flash sucking up cpu time and very little to do with the kernel.

---

### Post by paul_in_london on 2010-06-01
> **Longinus00 said:**
> If your first post is any indication, your load averages have everything to do with flash sucking up cpu time and very little to do with the kernel.

Thanks for your reply **Longinus00**.

Admittedly I haven't tested this systematically, but even with constant flash streaming, I've never noticed my system load being as high as it's been with the more recent 2.6.34 kernels.

What I can tell you is (under exactly the same conditions) 2.6.35-rc1+flash is definitely a bit of improvement for me compared with 2.6.34-5+flash.

Your reply made me wonder though because I've been using Flash 10.1 rc6 for a few days so I decided to revert to 10.1 rc5 for a little while to see whether that made much difference. So far, it seems to be another slight improvement so that's interesting to know...

That's what I get for changing too many things at the same time!

---

