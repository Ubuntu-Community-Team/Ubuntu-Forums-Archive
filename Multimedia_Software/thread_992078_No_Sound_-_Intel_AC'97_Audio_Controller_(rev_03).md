---
title: "No Sound - Intel AC'97 Audio Controller (rev 03)"
date: 2008-11-24
forum: Multimedia Software
---

### Post by eekrazyk on 2008-11-24
I've recently installed Kubuntu 8.04 on a new machine and have a weird sound problem.

aplay -l
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v
```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 3008
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1000 [size=256]
        I/O ports at 1400 [size=64]
        Memory at f0200800 (32-bit, non-prefetchable) [size=512]
        Memory at f0200a00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```

My problem is that the sound plays through the PC speaker and not my headphones.  I've messed around with the Kmix switches and outputs and cannot come up with any combination that works.

I've followed the [Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449") and everything appears to be okay.

cat /etc/modules
```
fuse
lp
snd-intel8x0

```

Anyone have any ideas?

---

### Post by psyke83 on 2008-11-24
> **eekrazyk said:**
> I've recently installed Kubuntu 8.04 on a new machine and have a weird sound problem.

aplay -l
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v
```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 3008
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1000 [size=256]
        I/O ports at 1400 [size=64]
        Memory at f0200800 (32-bit, non-prefetchable) [size=512]
        Memory at f0200a00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```

My problem is that the sound plays through the PC speaker and not my headphones.  I've messed around with the Kmix switches and outputs and cannot come up with any combination that works.

I've followed the [Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449") and everything appears to be okay.

cat /etc/modules
```
fuse
lp
snd-intel8x0

```

Anyone have any ideas?

Have you got the latest updates installed?

Look in the file /etc/modprobe.d/blacklist.

This block of text fixes the issues with the PC Speaker being assigned as the default ALSA sound device:
```
# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

```

You should have these lines in that file. If not... add them manually.

Edit: the comments may be different on your system (as I pasted this from a Jaunty installation, and I recall the text being different on Intrepid). The important line is "blacklist snd_pcsp".

---

### Post by eekrazyk on 2008-11-24
I thought it worked at first, but it was playing over both the headphones and the pc speaker.  When I switch over to my cordless headphones, it only plays over the pc speaker.

---

### Post by psyke83 on 2008-11-24
Ok, I understand your problem now. You need to enable a specific quirk for your sound card.

From [ALSA-Configuration.txt]("http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt"):
```
AC97 Quirk Option
=================

The ac97_quirk option is used to enable/override the workaround for
specific devices on drivers for on-board AC'97 controllers like
snd-intel8x0.  Some hardware have swapped output pins between Master
and Headphone, or Surround (thanks to confusion of AC'97
specifications from version to version :-)

The driver provides the auto-detection of known problematic devices,
but some might be unknown or wrongly detected.  In such a case, pass
the proper value with this option.

The following strings are accepted:
    - default	Don't override the default setting
    - none	Disable the quirk
    - hp_only	Bind Master and Headphone controls as a single control
    - swap_hp	Swap headphone and master controls
    - swap_surround  Swap master and surround controls
    - ad_sharing  For AD1985, turn on OMS bit and use headphone
    - alc_jack	For ALC65x, turn on the jack sense mode
    - inv_eapd	Inverted EAPD implementation
    - mute_led	Bind EAPD bit for turning on/off mute LED

```

One of those quirks applies to your hardware (I recommend you first try [COLOR="Blue"]hp_only[/COLOR], though there's no guarantee that's the correct one).

Edit /etc/modprobe.d/alsa-base, and add a line to the end:

```
options snd-intel8x0 ac97_quirk=[COLOR="Blue"]hp_only[/COLOR]
```

You need to reboot for changes to take effect. If a specific quirk doesn't work, edit the file and change the quirk type again.

---

### Post by eekrazyk on 2008-11-24
Huh.  I've tried each of them.  hp_only and swap_hp both still played through my corded headphones, but only in mono.  I'm still messing around with things, but none of the other settings produced any audio at all.

---

### Post by eekrazyk on 2008-11-25
Still no sound yet.  I've played around with each of these settings and nothing seems to work properly.  I'm only able to get mono out of one corded headphone with ac97_quirk=hp_only.

---

