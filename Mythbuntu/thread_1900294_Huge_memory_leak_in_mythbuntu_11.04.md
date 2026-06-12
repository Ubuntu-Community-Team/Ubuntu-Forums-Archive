---
title: "Huge memory leak in mythbuntu 11.04"
date: 2011-12-26
forum: Mythbuntu
---

### Post by marco.hahn on 2011-12-26
Hello,

I have a roughly 4 your old system that used mythTV 0.19.xx until lately. Everything was OK. This fall, I upgraded to mythbuntu 11.04. The hardware is an AMD Athlon x64, NVidia 6150 (Asus M2NPV-VM based system) with two Hauppauge WinTV-NOVA-T-USB2 for DVB-T reception.

I really like mythbuntu, setting it up was quite a bit easier than my homebrewn old combination. BUT I have two problems: 
1. XvMC is no longer supported (this is not nice, but the system is strong enough to handle this via the CPU). Any suggestion on how to turn it on for a trial would be welcome.

2. There is a huge memory leak! Essentially, **the system seems to lose memory at the rate of data recorded (i.e. 2-3 MB/s!!!)**.:sad::sad::sad: I upgraded memory to 2 GB, but this is filled up well within one hour. The mythTV status says that a few MB a left over and continues to work, but playback is severely impeded. **Any help on this is urgently needed!**

Thanks a lot in advance,

marco.hahn

****

---

### Post by 2F4U on 2011-12-26
In Linux there is a difference between the RAM used by processes and the RAM used for caching. You may first want to read through this thread and see if there really is a problem.

[http://ubuntuforums.org/showthread.php?t=1051144](http://ubuntuforums.org/showthread.php?t=1051144)

---

### Post by marco.hahn on 2011-12-27
Thanks for the suggestion. I tried it out during recording and playback of TV:

Playback was essentially constant.

Recording showed the following changes over 10-second-periods:
```

             total       used       free     shared    buffers     cached
Mem:       1924760     668944    1255816          0      35060     281184
-/+ buffers/cache:     352700    1572060
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:       1924760     673912    1250848          0      35132     285640
-/+ buffers/cache:     353140    1571620
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:       1924760     678260    1246500          0      35428     289884
-/+ buffers/cache:     352948    1571812
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:       1924760     683980    1240780          0      35540     294792
-/+ buffers/cache:     353648    1571112
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:       1924760     687708    1237052          0      35612     298812
-/+ buffers/cache:     353284    1571476
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:       1924760     691188    1233572          0      35692     302128
-/+ buffers/cache:     353368    1571392
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:       1924760     694668    1230092          0      35764     305388
-/+ buffers/cache:     353516    1571244
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:       1924760     698396    1226364          0      35844     308672
-/+ buffers/cache:     353880    1570880
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:       1924760     706604    1218156          0      35916     312116
-/+ buffers/cache:     358572    1566188
Swap:            0          0          0

             total       used       free     shared    buffers     cached
Mem:       1924760     709464    1215296          0      35988     314864
-/+ buffers/cache:     358612    1566148
Swap:            0          0          0

```Which means that used goes up by approx 5M/10s, free goes down by the same amount, buffers goes up by 72K/10s and cached goes up by 4.4M/10s.

So it may really be that the cache simply eats everything up. But then: Once the free mem ist near zero, playback does not work smoothly anymore ... Can I limit the caching somehow?

Thanks for the help,
marco.hahn

---

### Post by ian dobson on 2011-12-27
Hi,

Try changing your video playback to CPU-- or CPU-. If your graphic card support VDPAU then use that (NVidia >8600).

Regards
Ian Dobson

---

### Post by marco.hahn on 2011-12-28
Hello Ian,

why should the playback settings influence a recording memory leak?

Thanks,
marco.hahn

---

### Post by ian dobson on 2011-12-28
Hi,

I don't think your problem is a memory leak. Linux caches what's just been written as there's a good chance a program will request the information within a short time.

If you want to see how much memory the backend process uses, type

ps auxww | grep mythbackend
this will show:-
```
 
root     16389  0.0  0.0   7892   900 pts/0    S+   14:05   0:00 grep mythbackend
mythtv   19906  1.6  0.4 850408 76700 ?        Sl   00:32  13:22 /usr/bin/mythbackend --noupnp -v eit --user mythtv --logfile /var/log/mythtv/mythbackend.log
```

Only the line with  /usr/bin/mythbackend is interesting,The forth value is the % memory used.

Regards
Ian Dobson

---

