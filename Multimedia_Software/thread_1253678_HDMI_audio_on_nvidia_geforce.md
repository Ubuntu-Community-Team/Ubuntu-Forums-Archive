---
title: "HDMI audio on nvidia geforce?"
date: 2009-08-30
forum: Multimedia Software
---

### Post by shudders on 2009-08-30
Right, I've noticed that this appears to be an area with several different solutions. However, none appear to work for me. I've noticed that most succesful attempts involve Nforce so I'm not sure it's possible to get audio via hdmi with a geforce card. I got an Nvidia 8600GT, that should support audio over hdmi.

I think I've tried all the guides that I can find now.

aplay -l only lists my onboard audio
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC885 Analog [ALC885 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC885 Digital [ALC885 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I have installed the latest alsa-drivers (1.0.20) but no luck. I noticed in the alsa-configuration.txt that it seems only NForce is supported. Is this correct?

I also found a post ([http://ubuntuforums.org/archive/index.php/t-1173022.html](http://ubuntuforums.org/archive/index.php/t-1173022.html)) on this forum where they managed to patch the alsa-driver to include their Geforce card. That didn't work for med unfortunately. :( Using lspci -vvn I found that the vendor ID for 8600GT should be 0x10de0402 (I think)
```

01:00.0 0300: 10de:0402 (rev a1)

```

So i patched patch_nvhdmi.c by adding
```

{ .id = 0x10de0402, .name = "8600G HDMI", .patch = patch_nvhdmi },

and

MODULE_ALIAS("snd-hda-codec-id:10de0402");

```

However, I noticed a difference on my ubuntu machine. 
```

cat /proc/asound/card0/codec#* | grep Codec 
Codec: Realtek ALC889A

```
In other posts an nvidia codec is listed there, so I'm guessing that might be the missing piece. Anyone know how I would get that codec listed? Or should that appear when I install the alsa-drivers?

I'm totally lost now so any help is greatly appreciated. I'm using Linux version 2.6.28-15-generic if that would make any difference.

---

### Post by shudders on 2009-08-30
oh, and if it's not possible to get audio over hdmi, is it possible to somehow mute it anyway? Cause when I connect my TV and computer via hdmi I get a lot of annoying static background sounds.

---

