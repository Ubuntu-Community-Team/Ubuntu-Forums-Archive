---
title: "Soundcard rec. by Alsa &amp; activ. but not showing up in aplay"
date: 2012-07-11
forum: Multimedia Software
---

### Post by Greescom on 2012-07-11
Been wanting to try Linux for ages and finally taken the plunge. Everything has gone very smoothly except for the sound.

Spent hours on this prob now, been through both the troubleshooting guides on this site, plus countless others. On the plus side I'm getting used to the terminal now ;-)

I'm using the lightweight Lubuntu build.

I have three sound devices in my system - 
1.graphics hdmi audio
2.onboard sound
3. Creative Labs X-Fi XtremeGamer FATAL1TY PRO

To start I had no sound. 
Switching on audio in user account, installing pulseaudio, & blacklisting my graphics cards hdmi audio has the onboard sound working perfectly.
Still no joy on x-fi.

as you can see below x-fi is recognized by alsa & activated.....
-----------------------------
Sound cards recognized by the system:
00:0e.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series] [1002:aa38]
Sound cards recognized by ALSA:
00:0e.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series] [1002:aa38]
Sound cards recognized by ALSA, and activated:
00:0e.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]
00:11.5 Multimedia audio controller [0401]: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller [1106:3059] (rev 60)
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI RV710/730 HDMI Audio [Radeon HD 4000 series] [1002:aa38]
-------------------------------------

....but does not show up in aplay
-------------------------
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
-----------------------

Something i did notice in my pci device list was there is no 'Driver kernel in use' flag in the x-fi's list check:

-----------
00:0e.0 Multimedia audio controller: Creative Labs SB X-Fi
    Subsystem: Creative Labs X-Fi XtremeGamer FATAL1TY PRO
    Flags: medium devsel, IRQ 19
    I/O ports at c000 [size=32]
    Memory at fdc00000 (64-bit, non-prefetchable) [size=2M]
    Memory at f8000000 (64-bit, non-prefetchable) [size=64M]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
    Kernel modules: snd-ctxfi
------------

Any kind soul have ideas?

Aran.

---

### Post by Greescom on 2012-07-12
Searched and read through every thread with 'xfi' in it on this forum. Everything points to this card being supported & the fact it has a module loaded for it and is recognised by alsa confirms this... Why is it not appearing in aplay list or alsa mixer?

Tried different pci slots, no change.
Reinstalled using Ubuntu, no change.
Blacklisted onboard sound module, no change.
Switched off onboard sound in bios, no change.

Should point out that this card worked perfectly in my last windows XP install for years.

---

### Post by Greescom on 2012-07-12
I'm starting to think it's definitely the kernel driver that's the prob.

Every other working device has a 'driver kernel in use'.

I even know exactly what it should say : Kernel driver in use: SB-XFi 

Kernel modules: snd-ctxfi is loaded correctly.

Anyone know how to force the card to use a specific kernel driver.....?

---

### Post by Greescom on 2012-07-13
I officially give up.

The x-fi is not completely supported anyway,  just basic functionality.

If I'm still loving Ubuntu in a couple of months I'll ebay this card & get myself one that's fully supported by Linux.... maybe Asus D1.

In the meantime I'm using my onboard audio.

---

