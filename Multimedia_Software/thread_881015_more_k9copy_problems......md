---
title: "more k9copy problems....."
date: 2008-08-05
forum: Multimedia Software
---

### Post by porphiron on 2008-08-05
Lo folks, many months ago I had a few problems with k9copy, they were solved both by removing the overclock on my machine and also using a dedicated drive to encode to instead of an lvm volume...right that said.

I now have a new machine to faf with all this:

 an ASROCK amd mobo w/ athlon64 running @3300Ghz (no overclock)
and onboard mem @ 128mb
2Gig Mem (2x1Gig sticks)
x1 160Gb Hdd (that holds the o/s and has a separate "/Temp" partition where the encodes..."would" go!)

it has various other hard drives that are stuck on a pci ide card as there is  only one ide slot that is used for the DVD/RW

and a bog standard install of Xubuntu 8.04.1.

i am trying to use it to encode a 2 pass Xvid with mp3 audio

right, the system has the medibuntu version of mencoder and mplayer installed with the non-free codecs, for some reason k9copy will encode small files say up to 100mb, but over that it just seems to carry on as if mencoder has silently crashed, now the last time i left it running it went over 8hrs, which seems a very long time to convert a shrunk dvd of 4.7gb to 700mb, in the end i canceled it as it was saying 08:40:33 / 00:00:15 and it had been stuck @ 15 seconds for the last hour???

I have also tried this with the stock versions of mencoder and mplayer from the reps to no avail

the only thing i have noticed is that when i run "top" in a terminal there appears to be two copies of k9copy running:

```


23418 cerberus  20   0 45768  19m 4328 R 61.3  1.0   0:08.02 mencoder           
23337 cerberus  20   0  231m 106m  22m R 34.6  5.4   4:40.66 firefox            
23039 root      20   0 63512  36m 7824 S  2.7  1.9   0:38.64 Xorg               
22536 root      15  -5     0    0    0 S  0.7  0.0   0:00.28 ntdriver           
23407 cerberus  20   0 58644  21m  16m S  0.7  1.1   0:01.58 k9copy             
23417 cerberus  20   0 74836  30m  11m S  0.7  1.6   0:02.75 k9copy             
    1 root      20   0  2844 1692  544 S  0.0  0.1   0:01.18 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:01.72 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.02 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.36 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.20 khelper 


```

removing the higher number pid causes k9copy to go into pass two of the encode

any ideas anyone?

---

### Post by mc4man on 2008-08-05
> it just seems to carry on as if mencoder has silently crashed,
that's exactly what's happening and k9 will go on forever doing nothing.
While I've actually stopped using k9, for me after 2 or 3 attempts it started working right (in gutsy)
I use this instead (interactive cli)
It's in constant dev. so may not be suitable for you but anyway (not as much as h264enc)

[http://xvidenc.sourceforge.net/](http://xvidenc.sourceforge.net/)

forum on it and other 2 (h264enc, divxenc) and other good stuff

[http://forum.doom9.org/forumdisplay.php?f=63](http://forum.doom9.org/forumdisplay.php?f=63)

---

### Post by porphiron on 2008-08-05
cheers fella for the swift reply, will give have a look,

damn, k9copy works a treat when it works.........anyways

cheers again!

---

### Post by porphiron on 2008-08-05
fingers X'd xvidenc seems to be working a treat, pity about the lack of splitting the files as sometimes XBMC throws a wobbly with large avi files but......feh

thanks again!

---

### Post by mc4man on 2008-08-05
> k9copy works a treat when it works.
You can always try it again, for me and IIRC some others it just suddenly started working. (again it was on gutsy)
You could open system monitor while using k9 and if you see mencoder closing prematurely then cancel the encode

---

