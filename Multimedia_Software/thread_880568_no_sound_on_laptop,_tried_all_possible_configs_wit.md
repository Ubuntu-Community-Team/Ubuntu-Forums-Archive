---
title: "no sound on laptop, tried all possible configs with alsa-base"
date: 2008-08-05
forum: Multimedia Software
---

### Post by Yoctosecond on 2008-08-05
The laptop I have is a Asus m50vm-a1. I've tried to configure my alsa-base in all possibilities but I still have no sound whatsoever. my aplay -l reads ```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` cat /proc/asound/card0/codec#* | grep Codec outputs ... ```
Codec: Realtek ID 663
Codec: LSI ID 1040
Codec: Generic 10de ID 6

```
so far, I've already tried all the drivers that's listed under ALC662/663 in one of the alsa files. So far, I've had no luck for the last two weeks or so and it's getting beyond frustating. Any help would be awesome before I scrap my linux partition :mad: OSS also won't really work since my driver is a ICH9 family and that isn't compatible with OSS the last time I checked the list.

---

### Post by xc3RnbFO8P on 2008-08-05
Did you Read this:
[http://ubuntuforums.org/showthread.php?t=820959]("http://ubuntuforums.org/showthread.php?t=820959")

---

### Post by Yoctosecond on 2008-08-05
Yes, I've read that page already and ran the updated script. Tried it last night, however still no sound and it doesn't seem like alsa updates properly. Alsamixer still shows that I'm in 1.0.7, when I hit F2 it still says 1.0.6. I've already ran into this problem in the past, but couldn't get around it.

---

### Post by RaZe42 on 2008-09-10
AFAIK OSS4 should work with the M50VM, maybe you should at least try it out?

---

### Post by Yellow Pasque on 2008-09-10
ICH9 is supported in OSS4.1rc1
> oss_hdaudio	pci8086,293f	Intel High Definition Audio (ICH9)
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by ^[H3ad-Tr1p]^ on 2008-09-15
> **Temüjin said:**
> ICH9 is supported in OSS4.1rc1

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

hi friends

as well you,I have the same problem and I tried to install oss instead alsa,but following that guide I have meet one problem

At the point where I must to type:

sudo apt-get install -y esound esound-clients esound-common libesd0-dev

apt want to uninstall pulseaudio-esound-compat and ubuntu-desktop,so,I have installed only the packages that I could withouth esound



how I install esound without uninstall ubuntu-desktop?

thanks

---

### Post by Yellow Pasque on 2008-09-15
> how I install esound without uninstall ubuntu-desktop
You can't, but uninstalling ubuntu-desktop won't hurt anything. ubuntu-desktop is a metapackage that depends on all of the packages that make up Ubuntu's default configuration. It is there for convenience. For example, if someone running KDE/Kubuntu wanted to try the GNOME version of ubuntu, they would install this package (and they could use aptitude to uninstall all associated packages if they no longer wanted them)
Ubuntu Hardy uses pulseaudio for system sounds by default, so using OSS and esound is incompatible with the default configuration.

---

### Post by ^[H3ad-Tr1p]^ on 2008-09-15
> **Temüjin said:**
> You can't, but uninstalling ubuntu-desktop won't hurt anything. ubuntu-desktop is a metapackage that depends on all of the packages that make up Ubuntu's default configuration. It is there for convenience. For example, if someone running KDE/Kubuntu wanted to try the GNOME version of ubuntu, they would install this package (and they could use aptitude to uninstall all associated packages if they no longer wanted them)
Ubuntu Hardy uses pulseaudio for system sounds by default, so using OSS and esound is incompatible with the default configuration.

thanks for your support Temüjin

I believed that it was many important becouse I seem to remember that without ubuntu-desktop ,the system it wasn't able to start

so,now,it seems that my system is working almost fine....there is still a problem: my volume is at top but it is too much low

have some suggestion to lift volume

on my desktop ,on the applet near the clock it is already at maximum

---

