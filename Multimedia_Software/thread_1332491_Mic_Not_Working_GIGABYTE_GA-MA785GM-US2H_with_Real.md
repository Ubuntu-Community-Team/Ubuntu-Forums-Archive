---
title: "Mic Not Working: GIGABYTE GA-MA785GM-US2H with Realtek ALC889A audio"
date: 2009-11-20
forum: Multimedia Software
---

### Post by MaindotC on 2009-11-20
I tried following the directions on the [HDA Sound HowTo](https://help.ubuntu.com/community/HdaIntelSoundHowto).  When I first boot, the mic works, but if I try using anything that requires capture the mic seems to get shut off.  If I use sound recorder, I can record my voice, but when I play it back it is shortened so I basically only hear parts of the beginning and end.

The problem I have with the HowTo is that I don't have my model listed in /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz.  Here's what the HowTo asks to output:
```

x@x:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC889A

```
and here's my lspci:
```

x@x:~$ lspci | grep Audio
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)

```
but when Ilook in that ALSA-Configuration.txt.gz file I couldn't find an entry for ALC889A.  Since I can't continue with the troubleshooting, what is the next step?

Anyone have this board w/ a working mic?

---

### Post by MaindotC on 2009-11-20
bump

---

### Post by MaindotC on 2009-11-23
Just downloaded and installed latest updates for linux-backports-modules-alsa-karmic and still no dice :(

---

### Post by depaulmatthew on 2009-11-23
> **strAlan said:**
> Just downloaded and installed latest updates for linux-backports-modules-alsa-karmic and still no dice :(

I got the same problem.

---

### Post by MaindotC on 2010-07-27
Well, it's been a while and for the time being I've been getting by with a C-Media USB headset that allows input/output.  Anyone get the soundcard on the Gigabyte mobo working?

---

### Post by meng1usa on 2010-10-23
I have the same problem.
ALC889 chipset

---

