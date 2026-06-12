---
title: "[SOLVED] Suddenly Sound Doesn't Work"
date: 2008-10-07
forum: Multimedia Software
---

### Post by kramer2718 on 2008-10-07
Hi.  I'm running Ubuntu server with KDE on top.  Sound had been working fine up until recently, but now it doesn't work.  The only thing that I changed on my system were video drivers (at least I think).  It all began when I tried to install the native Nvidia drivers. They didn't work... I finally got them installed by installing Envy.  Now my sound doesn't work, but I'm not sure what exactly changed.

I tried to fix it by re-installing all the sound related packages on my system.  Those packages are as follows:

kmix
arts
libarts1c2a
libartsc0
libsdl1.2debian-alsa
alsa-base
linux-sound-base
lib32asound2
libasound2
alsa-utils
esound-common
libesd-alsa0


My sound driver (from lspci):
```

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
        Subsystem: Elitegroup Computer Systems Unknown device 2609
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0 (500ns min, 1250ns max)
        Interrupt: pin A routed to IRQ 20
        Region 0: Memory at febf8000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```


Any help would be appreciated:)

---

### Post by der_hede on 2008-10-07
Are there any error messages? For example trying to play audio from the command line via mpg321 or mplayer.

What is the output of the following two commands (entered in a shell):
```
sudo lshw -C multimedia
cat /proc/asound/cards 
```

---

### Post by stromdal on 2008-10-07
Did you check out this thread ([http://ubuntuforums.org/showthread.php?t=205449)?](http://ubuntuforums.org/showthread.php?t=205449)?)

Regards
/stromdal

---

### Post by minky311 on 2008-10-07
[http://ubuntuforums.org/showthread.php?t=939628](http://ubuntuforums.org/showthread.php?t=939628)
Is this the same problem you are having? If so try what was posted there as the solution.

---

### Post by kramer2718 on 2008-10-08
Got it.  Thanks.  Turns out all of the fiddling had fudged up my alsamixer settings.

---

