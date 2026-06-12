---
title: "One channel sound: ATI SB600 Azalia"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by stuporglue on 2007-03-10
I have a Compaq Presario SR2170NX with a sound card that 1/2 works. lspci reports it as:
```

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
        Subsystem: Hewlett-Packard Company Unknown device 2a4f
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at ff6f4000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

On the front panel, I have full stereo sound. When plugged into the back panel I have only mono sound (left channel only). 

I just upgraded to Feisty, but it was the same on Edgy. 

Anyone have an idea how to solve this problem?

---

### Post by jjalocha on 2007-04-21
I guess, this might be a problem with corrupt hardware. I have the same hardware here, perfect sound output (L and R channels) with both edgy and feisty:

```

$ lspci -v
[...]
00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
        Subsystem: Dell Unknown device 01f6
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at d0000000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
[...]

```

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

But i DO have problems with microphone input, specially with Feisty. How to make it work in Skype?

---

### Post by hotani on 2007-06-23
I have the same device on a Dell latitude D531 laptop and there is no sound at all. Any fixes?

This is what alsamixer reports:

```

shell> alsamixer 

alsamixer: function snd_ctl_open failed for default: No such device

```

And from "lspci -v":
```

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
        Subsystem: Dell Unknown device 0206
        Flags: slow devsel, IRQ 17
        Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

---

### Post by stuporglue on 2007-06-23
No idea here...

I did a fresh install of Feisty, and it's still only one channel. I have a USB media card reader/USB sound card thing installed now which gives me stereo, so I haven't worried about it much....it's still obnoxious though.

---

### Post by konungursvia on 2007-11-04
Try installing this and then reboot:

sudo apt-get install linux-backports-modules-generic

That worked for me on a Dell D531 with the same Toshiba soundcard (Azalia)

---

