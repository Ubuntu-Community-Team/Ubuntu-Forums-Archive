---
title: "Problem with multiple USB sound cards"
date: 2009-10-17
forum: Multimedia Software
---

### Post by kakan on 2009-10-17
Hello, my OS is Ubuntu 9.04 and I have 4 sound cards at the moment:
1x some Intel integrated into the motherboard
1x USB card named "USB AUDIO"
2x USB card named "C-Media USB Headphone Set USB Audio"

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: default_2 [USB  AUDIO  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 4: default_3 [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 5: default_4 [USB  AUDIO  ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

How it looks in System->Preferences->Sound
[[IMG]http://img17.imageshack.us/img17/4801/screenshotlg.th.png[/IMG]](http://img17.imageshack.us/i/screenshotlg.png/)
Why is the "C-Media USB Headphone Set USB Audio (OSS)" listed 6 times while there're only 2 such devices plugged?

When trying to use gnome-alsamixer:
```
(gnome-alsamixer:5393): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault
```

Ofcourse cards are changing every boot. Tried to fix it, but /etc/modprobe.d/alsa-base in empty on my OS.

**Could anyone help me to get this done properly?**
All I want is to get working my simple application that's playing 4 different songs on 4 different sound cards at the same time. I wrote it using [BASS for Linux]("http://www.un4seen.com/forum/?topic=8682"). Compiled for Win32 works great, but compiled for Linux doesn't play anything.

Any chance of getting it to work? Thanks in advance.

---

