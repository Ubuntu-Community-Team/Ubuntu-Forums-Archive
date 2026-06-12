---
title: "Change default sound card in Hardy"
date: 2008-05-19
forum: Multimedia Software
---

### Post by leemid on 2008-05-19
Hi,
I'm having trouble selecting the default sound card in Hardy. I have a Dell Dimension 5150 with onboard sound and a USB headset I use for conferencing. After the login screen all system sounds play on the headset, although Rhythmbox etc. all play correctly through the onboard sound. The settings I make in System -> Preferences -> Sound seem to make no difference whatsoever.

If I type aplay -l into a terminal I get the following output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

...so I think I just need so make it choose card 0 as the default. Any ideas?

---

### Post by leemid on 2008-06-04
I found the answer in the end, the workaround on [this page]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/229137") worked for me perfectly.

---

### Post by boris.abramov on 2010-11-28
Here is a gnome-applet for that
[http://boris-abramov.livejournal.com/159079.html](http://boris-abramov.livejournal.com/159079.html)

> **leemid said:**
> Hi,
I'm having trouble selecting the default sound card in Hardy. I have a Dell Dimension 5150 with onboard sound and a USB headset I use for conferencing. After the login screen all system sounds play on the headset, although Rhythmbox etc. all play correctly through the onboard sound. The settings I make in System -> Preferences -> Sound seem to make no difference whatsoever.

If I type aplay -l into a terminal I get the following output:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

...so I think I just need so make it choose card 0 as the default. Any ideas?

---

