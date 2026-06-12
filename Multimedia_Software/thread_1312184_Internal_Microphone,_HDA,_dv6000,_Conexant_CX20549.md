---
title: "Internal Microphone, HDA, dv6000, Conexant CX20549"
date: 2009-11-02
forum: Multimedia Software
---

### Post by chari on 2009-11-02
Hey guys,
I'm more than frustrated, after 4 days of working on my sound settings and reading thousand of guides that all promise to solve my problem, I still don't get my internal microphone to work. 
I know, that many people have problems with their microphone on HDA Intel Cards, but many of them seem to find a solution, so I still have hope.

Some Information:
-Ubuntu 9.10
-pulseaudio 0.9.19
-recompiled my ALSA drivers as described in [Comprehensive Sound Problem Solutions Guide]("http://ubuntuforums.org/showthread.php?t=205449")
-while recompiling, I choose the **hda-intel driver** and the **intel8x0 driver**
-I tried different models in the /etc/modprobe.d/alsa-base.conf file, as described in [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
-my current setting is:
>                                   **options snd-hda-intel model=auto probe_mask=1**
 **options snd-intel8x0 ac97_quirk=3**
 -my laptop is a HP dv6000
-my soundcard information is:
                          > 00:1b.0 Audio device: **Intel Corporation 82801G (ICH7 Family)** High Definition Audio Controller (rev 02) 
     Subsystem: Hewlett-Packard Company Device 30bb 
     Flags: bus master, fast devsel, latency 0, IRQ 22 
     Memory at de300000 (64-bit, non-prefetchable) [size=16K] 
     Capabilities: <access denied> 
     Kernel driver in use: HDA Intel 
     Kernel modules: snd-hda-intel 
-my sound codec is:
                          > charly@lucy:~$ cat /proc/asound/card0/codec#* | grep Codec 
 **Codec: Conexant CX20549 (Venice) **
-my alsamixer settings look like this:
[http://img5.imagebanana.com/img/f60y74/BildschirmfotoTerminalcharlylucy.png](http://img5.imagebanana.com/img/f60y74/BildschirmfotoTerminalcharlylucy.png)
-I tried a manual fixed, described here:
[http://ubuntuforums.org/showpost.php?p=6952168&postcount=7](http://ubuntuforums.org/showpost.php?p=6952168&postcount=7)
the full thread is here:
[http://ubuntuforums.org/showthread.php?t=1039685](http://ubuntuforums.org/showthread.php?t=1039685)
The screen I got looked like this:
[http://img5.imagebanana.com/img/21ohvybd/BildschirmfotoHDAAnalyzer.png](http://img5.imagebanana.com/img/21ohvybd/BildschirmfotoHDAAnalyzer.png)
the information about the pin, that probably belongs to my internal mic looks like this:
[http://img5.imagebanana.com/img/1czd9jje/BildschirmfotoHDAAnalyzer1.png](http://img5.imagebanana.com/img/1czd9jje/BildschirmfotoHDAAnalyzer1.png)
Changing the pins, like described in the guide didn't work, altough my sound recorder shows different volumes depending on which pin I choose.


I would be really happy if anyone could help me. Two other problems are, while trying to fix the microphone, I messed up the ALSA / OSS settings, know only one program at a time can produce sound. Another probably more relevant problem is, that I get only sound through my earphones, this seems to be a common problem as well of the HDA Intel series, because some pins are messed up.

Has anyone encountered the same problem? Has anyone an idea, what I could try? Does anyone have the same hardware and a working microphone?
Please help me,
Chari

---

### Post by chari on 2009-11-06
Please anyone?!

---

### Post by a3moura on 2010-11-27
Windows! It's works!

---

