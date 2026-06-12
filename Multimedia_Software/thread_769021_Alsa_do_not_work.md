---
title: "Alsa do not work"
date: 2008-04-26
forum: Multimedia Software
---

### Post by presston on 2008-04-26
My system is ubuntu 7.10
Motherboard Asus P4P8x (s478, i865) with integrated audio card AD1985 (analog AC97)

Alsa is last version. But sound working only on oss.
Any tutorial and forums didn't help me to configure it.

Also, there are no multiple sound (from few applications), i thought that without alsa it will continous

Help me please to fix it :confused:

---

### Post by presston on 2008-04-26
there are some resolves which i tried:
[http://ubuntuforums.org/showpost.php?p=4298894&postcount=2&#1089;](http://ubuntuforums.org/showpost.php?p=4298894&postcount=2&#1089;) (after it sound desapeared at all, i had to reinstall alsa)
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) (no result)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) (no result :( )

---

### Post by presston on 2008-04-27
Hey, guys ... did nobody had such problems? pleaaaaz help, it very big trouble in workong

---

### Post by presston on 2008-04-27
also, alsaconf find and install soundcard as ok (intel8x0). but no changes after that

---

### Post by divali on 2008-04-27
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Have you really tried this **comprehensive sound problems** post. If so at what point did you have problems?

---

### Post by presston on 2008-04-27
step by step:  (ubuntu in russian but you can see cards etc normal)

1.> root@X2:~# aplay -l
**** &#1057;&#1087;&#1080;&#1089;&#1086;&#1082; PLAYBACK &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074; ****
&#1082;&#1072;&#1088;&#1090;&#1072; 0: ICH5 [Intel ICH5], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 0: Intel ICH [Intel ICH5]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0
&#1082;&#1072;&#1088;&#1090;&#1072; 0: ICH5 [Intel ICH5], &#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1072;: 1/1
  &#1055;&#1086;&#1076;&#1091;&#1089;&#1090;&#1088;&#1086;&#1081;&#1089;&#1090;&#1074;&#1086; &#8470;0: subdevice #0

2.> 00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. P4P800 Mainboard
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at e800 [size=256]
        I/O ports at ee80 [size=64]
        Memory at febff400 (32-bit, non-prefetchable) [size=512]
        Memory at febff000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [50] Power Management version 2

3.done
4.
modules
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
snd-intel8x0  (tried snd-card-intel8x0 to)

> root@X2:~# modprobe snd-card-intel8x0
FATAL: Module snd_card_intel8x0 not found.

that's all.

---

### Post by presston on 2008-04-27
aslo

> root@X2:~# modprobe snd-seq-virmidi
FATAL: Error inserting snd_seq_virmidi (/lib/modules/2.6.22-14-generic/updates/sound/core/seq/snd-seq-virmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)


at least i've done it with "modprobe snd-intel8x0". in alsamixer all unmuted. i'v reinstall alsa again (as in instruction), but still no sound
||
> Getting the ALSA drivers from a *fresh* kernel

---

### Post by presston on 2008-04-27
also, if i type "aplay" without "-l" i have message:

> presston@X2:~$ aplay
ALSA lib pcm_direct.c:1479:(_snd_pcm_direct_get_slave_ipc_offset) Invalid value for card
aplay: main:545: erorr until open audio device: No such device


---

### Post by presston on 2008-04-27
after a lot os search in this forum branch, i see that many people have such problem as i, but no one got completly resolve :((  

this problem means for me, that i'll could norlamy wo&#1082;&#1083; in ubuntu, please help

---

### Post by presston on 2008-04-27
nobody can help me?

---

### Post by azimut on 2010-02-22
> **presston said:**
> nobody can help me?

```
# modprobe snd**-card-**intel8x0
```
It's not right.

```
# modprobe snd-intel8x0
```
It's ok.

---

### Post by drauchomyn on 2010-02-24
I can. 

I also had problems with the AC97 intel8x0 configuration and just solved them.

Make sure that you have the intel8x0 drivers on your computer:

Type sudo modprobe intel-8x0, then hit tab twice, DO NOT hit enter.  If you see snd-intel8x0 listed there then you can skip the next step.

If not, you will need to obtain the drivers from the alsa website.
Follow these instructions:

```
 
[LEFT][SIZE=2]mkdir src[/SIZE]
[SIZE=2]cd src[/SIZE] [/LEFT]
      
[LEFT][SIZE=2]mkdir alsa[/SIZE] [/LEFT]
      
[LEFT][SIZE=2]cd alsa[/SIZE] [/LEFT]
      
[LEFT][SIZE=2]sudo apt-get install build-essential linux-headers-$(uname -r)[/SIZE][/LEFT]
[SIZE=2]wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.tar.bz2[/SIZE]
[LEFT][SIZE=2]tar xvjf alsa-driver-1.0.22.tar.bz2[/SIZE]
[SIZE=2]cd alsa-driver-1.0.22[/SIZE]
[SIZE=2]sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=[COLOR=blue]intel8x0 [COLOR=black]--with-oss=yes[/COLOR][/COLOR][/SIZE]
[SIZE=2]sudo make[/SIZE]
[SIZE=2]sudo make install[/SIZE][/LEFT]

```

(I modified the instructions above from this post: [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449))

Next, follow the solution I posted at the bottom of this thread:

[http://ubuntuforums.org/showthread.php?t=1383493](http://ubuntuforums.org/showthread.php?t=1383493)

Good luck.

---

