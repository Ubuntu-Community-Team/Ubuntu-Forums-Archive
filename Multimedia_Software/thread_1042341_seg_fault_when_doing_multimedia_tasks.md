---
title: "seg fault when doing multimedia tasks"
date: 2009-01-17
forum: Multimedia Software
---

### Post by Bil-E-daKid on 2009-01-17
Hey guys,

I'm stumped by this one and need some help to track down the root cause.

These issues seem to have started after installing intrepid but I have since gone back to hardy (and even tried etch) and the same thing is happening.

I suspect it may be hardware but I'm not sure which log files to look in for that kind of thing.

The first noticeable place where this happens is exporting a ~60Mb WAV to an MP3 file using audacity.  Part way through the process, the audacity window disappears.  Starting audacity from a terminal to see what the problem is, just shows 'SEGMENTATION FAULT' (and I didn't grab the dmesg line for that one sorry).

The second place this happens is trying to extract a DVD to OGV using Thoggen.  Thoggen window disappears part way in (usually only a couple of minutes - sometimes less). Starting from the terminal shows a segmentation fault too - and no other errors.  Dmesg had this to say:

[  506.030295] thoggen[6471]: segfault at 00000018 eip b74fa407 esp 874f0000 error 4
[27475.973538] thoggen[6646]: segfault at 00000018 eip b74f4407 esp bf99a060 error 4

(First line from last night when I set it off before going to bed, second line from this morning when I got up, saw it had seg faulted and tried it again.)

I have replaced my DDR400 RAM with some more borrowed from a friend and that didn't make the problem go away.

General stability of this machine is great - it's normally on for weeks at a time serving the familys various document/web/email/printing needs - and has done this for about four years with the only major hardware change being a new 7600GT graphics card (most recently - about 12 months ago) and a new Socket 478 P4 Extreme Edition CPU about 18 months ago).

So, what do you guys think?  Hardware or software? And how do I troubleshoot this one further? (BTW, I've been a linux user for about 8 years now, so I'm not really a guru and definetely not a noob.  Perhaps more of a goob. :D   )

Any and all help would be greatly appreciated.

---

### Post by Bil-E-daKid on 2009-01-19
Here's some more after rebuilding from fresh to intrepid.  Looks like NX is segfaulting now too.  Not sure what canberra-gtk-pl even is.

Jan 18 23:50:42 josiah kernel: [ 9450.043309] nxserver[24168]: segfault at 600d ip 0000600d sp bfb0035c error 4 in nxserver[8048000+692000]
Jan 18 23:52:43 josiah kernel: [ 9571.355684] nxserver[24208]: segfault at 600d ip 0000600d sp bfedaa6c error 4 in nxserver[8048000+692000]
Jan 18 23:56:01 josiah kernel: [ 9769.405700] nxserver[24248]: segfault at 600d ip 0000600d sp bf9344cc error 4 in nxserver[8048000+692000]
Jan 19 08:34:27 josiah kernel: [40875.594784] nxserver[26334]: segfault at 600d ip 0000600d sp bfdb794c error 4 in nxserver[8048000+692000]
Jan 19 08:37:33 josiah kernel: [41061.587390] nxserver[26374]: segfault at 600d ip 0000600d sp bfd128ac error 4 in nxserver[8048000+692000]
Jan 19 22:44:58 josiah kernel: [91906.495739] canberra-gtk-pl[8501]: segfault at 5442f3d8 ip b71fe84d sp b6f9bf10 error 6 in libpulse.so.0.4.1[b71bf000+4e000]
Jan 20 07:27:33 josiah kernel: [123261.825392] audacity[17758]: segfault at bfb0c0e8 ip b5e1e021 sp bfafd9dc error 4 in libmp3lame.so.0.0.0[b5def000+42000]

---

### Post by Bil-E-daKid on 2009-01-24
Ok - sorted.

Turned out to be the CPU overheating.  Interesting, there was **nothing** in dmesg about the CPU overheating - though, when I had Debian on, it did show messages about that - and, when I booted into the Fedora 10 Live CD, it also complained about the CPU overheating in dmesg.

So, to solve the problem, I transplanted the guts of my box into a new case which breathes better and also used the correct heatsink for my CPU (one with a copper core).

The problem was that I was using the same case and heatsink from my old P4 2.8Ghz which wasn't cutting it with the new P4EE 3.4Ghz and the amount of heat it generates.

Hopefully this helps someone else out too.

---

### Post by Bil-E-daKid on 2009-01-24
If anyone is interested, here's some temps from lm-sensors that show the difference in internal temps between the two cases and heatsinks.  These are both just at system idle with no loading.

**Before**
SDA: 37C | SDB: 34C | GPU: 57C | CPU: 40C

**After**
SDA: 33C | SDB: 28C | GPU: 40C | CPU: 23C

During loading, the CPU was getting to around 70C, now its able to stay around the 57C - and with no segfaulting going on!  Yaay! 

I'm guessing that Windows would have merely bluescreened rather than segfaulting the process that was running the CPU hot.  Very nice.

---

### Post by byStanderone on 2009-01-29
...hi,

try: sudo rm /var/cache/apt/*.bin

---

### Post by Bil-E-daKid on 2009-01-29
Thanks for the reply byStanderone,

I have solved the problem through better cooling thanks.

Though, I must admit, I'm confused as to how removing the package cache /bin files would resolve seg fault issues.  Would you please explain that?

Regards
Bil-E-dakid

---

### Post by byStanderone on 2009-03-10
...just an idea, sometimes bins clutter the cache, specially when the download process is interrupted unexpectedly without completion...access of this uncompleted data, misleads the system process.

as for the cpu overheat, sync problems could also be the cause.

---

### Post by Bil-E-daKid on 2009-03-10
Ahh - ok - thanks for that!

---

