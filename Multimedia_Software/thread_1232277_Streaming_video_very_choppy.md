---
title: "Streaming video very choppy???"
date: 2009-08-05
forum: Multimedia Software
---

### Post by TheMustangZone on 2009-08-05
I'm a new user of Ubuntu 9.04, but a long time computer geek. I finally could not take anymore Windows crap and wiped it from my hard drive. I have everthing up and running fine, but I noticed when I try to watch streaming videos in Firefox, the video feed looks like it's playing frame-by-frame. Is this a Firefox issue or a hardware driver issue I need to fix? Any advice would be appreciated. Thanks.
 
Rob

---

### Post by TheMustangZone on 2009-08-05
BUMP. Anyone?

---

### Post by kickwin on 2009-08-05
I had the same problem on my Dell Inspiron with Intel graphics card and [this]("http://ubuntuforums.org/showthread.php?t=1190199&page=2#13") is how I fixed it. I no more have choppy video but still CPU usage is close to 100% when viewing flash videos in full-screen mode. Try searching "cpu usage flash videos ubuntu" and you may find a solution for that. I haven't tried any though.

---

### Post by kickwin on 2009-08-05
Once you fix the choppy video issue, try what is given [here]("https://answers.launchpad.net/ubuntu/+question/74681") and see if it fixes high cpu usage problem (of course if you have this problem but there is a very good chance you have it).

---

### Post by cyrylski on 2009-08-05
that helped me as well, thank you!

still, it's damn annoying we still have to resort to some workarounds when using ubuntu, especially if it's for something as basic as flash (for me at least).

---

### Post by TheMustangZone on 2009-08-05
Thanks a lot for the help.  I will keep trudging forward.  It's like learning how to use a computer all over again.:D

---

### Post by TheMustangZone on 2009-08-06
> **kickwin said:**
> I had the same problem on my Dell Inspiron with Intel graphics card and [this]("http://ubuntuforums.org/showthread.php?t=1190199&page=2#13") is how I fixed it. I no more have choppy video but still CPU usage is close to 100% when viewing flash videos in full-screen mode. Try searching "cpu usage flash videos ubuntu" and you may find a solution for that. I haven't tried any though.

I have followed your instructions and here is what I found:

03:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV280 [Radeon 9200] [1002:5961] (rev 01)
    Subsystem: C.P. Technology Co. Ltd Device [148c:2062]
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (2000ns min), Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 19
    [COLOR=Red]Region 0: Memory at d8000000 (32-bit, prefetchable) [size=128M][/COLOR]
    Region 1: I/O ports at c000 [size=256]
    Region 2: Memory at e9000000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at e8000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeonfb

03:00.1 Display controller [0380]: ATI Technologies Inc RV280 [Radeon 9200] (Secondary) [1002:5941] (rev 01)
    Subsystem: C.P. Technology Co. Ltd Device [148c:2063]
    Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Region 0: Memory at e0000000 (32-bit, prefetchable) [disabled] [size=128M]
    Region 1: Memory at e9010000 (32-bit, non-prefetchable) [disabled] [size=64K]
    Capabilities: <access denied>

rob@1badasspc:~$ cat /proc/mtrr
reg00: base=0x000000000 (    0MB), size= 1024MB, count=1: write-back
reg01: base=0x0d0000000 ( 3328MB), size=  128MB, count=2: write-combining
[COLOR=Red]reg02: base=0x0d8000000 ( 3456MB), size=  128MB, count=1: write-combining[/COLOR]
rob@1badasspc:~$ 

If I'm reading this correctly, it looks like "d8000000" ***is*** in the list.  Do I go ahead and proceed or do I need to try a different solution?  Thanks again.

---

### Post by kickwin on 2009-08-06
I am not sure if the solution would work for graphics cards other than [Intel]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/314928"). I recommend you research about it in this forum or on google.

---

### Post by Leoncio on 2010-06-18
I've got that same problem, but ony on Chromium. Firefox handles flash videos fine.

---

### Post by themadukrainian on 2010-11-30
Mustang, sent you an email on this subject. I have exactly same video specs as you posted, also looking for a cure.
the Mad Ukrainian

---

