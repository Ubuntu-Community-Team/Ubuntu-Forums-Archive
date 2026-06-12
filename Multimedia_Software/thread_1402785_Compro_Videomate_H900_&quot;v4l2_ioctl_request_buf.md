---
title: "Compro Videomate H900: &quot;v4l2: ioctl request buffers failed: Invalid argument&quot; error"
date: 2010-02-09
forum: Multimedia Software
---

### Post by vvasili on 2010-02-09
Hello to all.
I have got TV tuner Compro Videomate H900. When I installed the MPlayer and ran with parameters
```
mplayer tv:// -tv driver=v4l2:device=/dev/video0
```
I got the following error "v4l2: ioctl request buffers failed: Invalid argument"
Full message ```
mplayer tv:// -tv driver=v4l2:device=/dev/video0
MPlayer UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing tv://.
TV file format detected.
Selected driver: v4l2
 name: Video 4 Linux 2 input
 author: Martin Olschewski <olschewski@zpr.uni-koeln.de>
 comment: first try, more to come ;-)
Selected device: Compro VideoMate H900
 Tuner cap: STEREO LANG1 LANG2
 Tuner rxs: MONO
 Capabilites:  video capture  VBI capture device  tuner  audio  read/write
 supported norms: 0 = NTSC; 1 = NTSC-M; 2 = NTSC-M-JP; 3 = NTSC-M-KR; 4 = NTSC-443; 5 = PAL; 6 = PAL-BG; 7 = PAL-H; 8 = PAL-I; 9 = PAL-DK; 10 = PAL-M; 11 = PAL-N; 12 = PAL-Nc; 13 = PAL-60; 14 = SECAM; 15 = SECAM-B; 16 = SECAM-G; 17 = SECAM-H; 18 = SECAM-DK; 19 = SECAM-L; 20 = SECAM-Lc;
 inputs: 0 = Tuner 1; 1 = S-Video 1; 2 = Composite 1;
 Current input: 0
 Current format: unknown (0x4745504d)
v4l2: current audio mode is : LANG1
v4l2: ioctl request buffers failed: Invalid argument
v4l2: 0 frames successfully processed, 0 frames dropped.
```

Someone writes that I should recompile MPlayer with enable debug flag. I really don't understand this. But if it is only way I should try to do it.

P.S. The tuner fine works on Windows, I think that problem is not hardware.
"uname -a" gives
Linux station 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

---

### Post by HappyFeet on 2010-02-09
Are you sure it's a v4l2 device, and not a pvr or dvb?

---

### Post by xc3RnbFO8P on 2010-02-09
Maybe this will help:
[http://www.linuxquestions.org/questions/linux-software-2/getting-tv-card-to-work-is-proving-to-be-troublesome-541152/]("http://www.linuxquestions.org/questions/linux-software-2/getting-tv-card-to-work-is-proving-to-be-troublesome-541152/")

---

### Post by vvasili on 2010-02-10
Ubuntu is my home OS. This evening I will try to do it and give us the results.

---

### Post by vvasili on 2010-02-11
The command "sudo module-assistant auto-install ivtv" returns error
```

&#9474; Ignoring this package. Maybe you need to add something to
&#9474; sources.list, maybe the contrib and non-free archives.

```

My source.list is ```
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027.1)]/ karmic main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.datacenter.by/ubuntu/ karmic main restricted
deb-src http://mirror.datacenter.by/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.datacenter.by/ubuntu/ karmic-updates main restricted
deb-src http://mirror.datacenter.by/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.datacenter.by/ubuntu/ karmic universe
deb http://mirror.datacenter.by/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.datacenter.by/ubuntu/ karmic multiverse
deb http://mirror.datacenter.by/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://by.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://by.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://mirror.datacenter.by/ubuntu/ karmic-security main restricted
deb-src http://mirror.datacenter.by/ubuntu/ karmic-security restricted main multiverse universe #Added by software-properties
deb http://mirror.datacenter.by/ubuntu/ karmic-security universe
deb http://mirror.datacenter.by/ubuntu/ karmic-proposed restricted main multiverse universe
deb-src http://mirror.datacenter.by/ubuntu/ karmic-proposed restricted main multiverse universe #Added by software-properties
deb http://mirror.datacenter.by/ubuntu/ karmic-security multiverse
deb http://mirror.datacenter.by/ubuntu/ karmic multiverse
deb http://mirror.datacenter.by/ubuntu/ karmic multiverse
```

What do I need add to sources?

[http://mirror.datacenter.by/ubuntu/](http://mirror.datacenter.by/ubuntu/) is one of the official mirrors.

---

