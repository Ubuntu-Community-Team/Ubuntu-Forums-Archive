---
title: "Lucid/ALSA/Sound card ports (pin config??)"
date: 2010-05-03
forum: Multimedia Software
---

### Post by jd4x4 on 2010-05-03
Bear with me as I'm a relative newb.. my upgrade to Lucid didn't detect my sound card (a Gigabyte mb on-board RealTek ALC883) so I've learned a lot (maybe too much?) by installing it manually by adding 'snd-hda-intel: model=alc883-6stack-dig' to alsa.conf and to etc/modules.

That got me basically working, but I dual-boot WinXP and RealTek has a win app that lets me 'map' the in/out jacks and my setup isn't the default HD audio (ie I use 'black' port as another Line In).

I think I understand that this re-mapping is done by 'pin' configurations in the sound drivers, but I'm lost beyond this. Is it possible to change some sort of configuration file to match my windows 'mappings' without recompiling drivers or anything? Does any of this make sense?? 8-[

---

### Post by Tristan Schmelcher on 2010-07-05
I think what you're looking for is the user_pin_configs feature in sysfs, found at, e.g., /sys/class/sound/hwC0D0/user_pin_configs. You can echo (pin, config) pairs to it at run-time to override the start-up defaults. e.g.:

```
$ cat /sys/class/sound/hwC0D0/init_pin_configs    # Reads the defaults
0x08 0x40f000f0
0x09 0x40f000f1
0x0d 0x0421101f
0x0e 0x90170110
0x0f 0x40f000f2
0x10 0x04a11020
0x11 0x40f000f3
0x12 0x40f000f4
$ sudo sh -c "echo 0x08 0x40f000f0 > /sys/class/sound/hwC0D0/user_pin_configs"    # Applies an override
$ cat /sys/class/sound/hwC0D0/user_pin_configs                                    # List all overrides
0x08 0x40f000f0       
$ sudo sh -c "echo 0x09 0x40f000f1 > /sys/class/sound/hwC0D0/user_pin_configs"    # Applies another override
$ cat /sys/class/sound/hwC0D0/user_pin_configs                                    # List all overrides
0x08 0x40f000f0
0x09 0x40f000f1
```

My "overrides" above don't actually change anything, but you get the idea.

I don't think there is any nice GUI app for doing this though.

---

