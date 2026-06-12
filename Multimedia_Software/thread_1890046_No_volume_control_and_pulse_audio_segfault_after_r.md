---
title: "No volume control and pulse audio segfault after recent updates"
date: 2011-12-02
forum: Multimedia Software
---

### Post by Chav on 2011-12-02
After a recent update which included a new kernel (last 2 weeks?) I noticed that the gnome applet volume control no longer works. 

I ran alsamixer from the terminal and got:

```
ALSA lib conf.c:3288:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:882:(snd_ctl_open_noupdate) Invalid CTL default
cannot open mixer: No such file or directory
```

After doing an strace I could see that alsamixer was looking for libasound_module_conf_pulse.so so I did:

```
sudo ln -s /usr/lib/x86_64-linux-gnu/alsa-lib/libasound_module_conf_pulse.so /usr/lib/libasound_module_conf_pulse.so
```

Now alsamixer runs and I can control my audio, but still the gnome applet wouldn't work. 

Tail of kern.log reports the following:

```
kernel: [11389.517970] pulseaudio[8714]: segfault at 1b86 ip 0000000000001b86 sp 00007fff633264d8 error 14 in pulseaudio[400000+13000]
```

Looks like a pulseaudio problem. So I did the normal removal of .pulse etc. and ran pulseaudio -vvv which reports:

```
D: [pulseaudio] module-udev-detect.c: Loading module-alsa-card with arguments 'device_id="1" name="pci-0000_01_00.1" card_name="alsa_card.pci-0000_01_00.1" namereg_fail=false tsched=yes ignore_dB=no deferred_volume=yes card_properties="module-udev-detect.discovered=1"'
Segmentation fault
```

I also followed the guide to reinstall pulseaudio and the kernel which did not help.

Finally, I tried to run the alsa-info script but it would hang. I traced the hang down to the withaplay() function. After commenting that function out I get the following output:
[http://www.alsa-project.org/db/?f=be05fff37df73a73fee66fe4a4722346c176c828](http://www.alsa-project.org/db/?f=be05fff37df73a73fee66fe4a4722346c176c828)

And the manual output of the withaplay() code:

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: Cirrus Digital [Cirrus Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: Cirrus Analog [Cirrus Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: Cirrus Digital [Cirrus Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I have the same issue on two laptops. The macbook 8,2 I'm currently on and a Lenovo Thinkpad t61.

---

### Post by Chav on 2011-12-05
bump

---

### Post by Chav on 2011-12-14
ttt

---

