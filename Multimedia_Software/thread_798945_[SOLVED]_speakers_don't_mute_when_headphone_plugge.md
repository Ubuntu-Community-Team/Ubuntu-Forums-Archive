---
title: "[SOLVED] speakers don't mute when headphone plugged in"
date: 2008-05-18
forum: Multimedia Software
---

### Post by zakAap on 2008-05-18
hi guys,

When i plug in headphones in my laptop my speakers don't mute like they did in windows. I'm using ubuntu 8.04 (Hardy Heron). My laptop is a fujitsu siemens amilo pi 2530.

> $ lspci -v
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Fujitsu Siemens Computers Unknown device 1107
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I would reallly appreciate it if you guys could help me :guitar:

---

### Post by DieB on 2008-05-19
if you use gnome right click on the volume-control-icon in the top right, choose the second options. Then edit the preferences by turning on Headphone Jack Sense, you then have to enable it also in the main window (it is in a separate tab).

that should fix it.

---

### Post by zakAap on 2008-05-19
Thanks for your reply but I don't see that option. 
In alsa-mixer I think that's what you meant, I enabled all tracks:
[[IMG]http://img329.imageshack.us/img329/1658/screenshotvolumecontrolvq2.th.png[/IMG]](http://img329.imageshack.us/my.php?image=screenshotvolumecontrolvq2.png)
Then I have these tabs in the main window:
Playback:
[[IMG]http://img519.imageshack.us/img519/5140/screenshotvolumecontrolqo6.th.png[/IMG]](http://img519.imageshack.us/my.php?image=screenshotvolumecontrolqo6.png)
Recording:
[[IMG]http://img519.imageshack.us/img519/3196/screenshotvolumecontroliw3.th.png[/IMG]](http://img519.imageshack.us/my.php?image=screenshotvolumecontroliw3.png)
Switches:
[[IMG]http://img519.imageshack.us/img519/7922/screenshotvolumecontrolkx6.th.png[/IMG]](http://img519.imageshack.us/my.php?image=screenshotvolumecontrolkx6.png)
Options:
[[IMG]http://img329.imageshack.us/img329/8648/screenshotvolumecontrolgt6.th.png[/IMG]](http://img329.imageshack.us/my.php?image=screenshotvolumecontrolgt6.png)
Is there something wrong with those settings, or is it something else?

---

### Post by alexforcefive on 2008-05-19
Try file > change device and selecting the name of your sound card. Your mixer might not be controlling the correct device

---

### Post by zakAap on 2008-05-19
I fixed it! :KS
It was controlling the right device, but it wasn't controlling the right model.. 
Here I found the solution: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/114053/comments/30](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/114053/comments/30)
In short I added this line to /etc/modprobe.d/alsa-base
```
options snd-hda-intel model=lenovo-nb0763
```
:guitar:

---

### Post by d3bovo on 2009-03-19
I have a fs amilo pi 2530 too, but this did't work...

---

### Post by xxfrankxx on 2009-11-10
I have a fujitsu-siemens Amilo Pi 1536 and I experienced the same issue, it got solved as well by setting:

options snd-hda-intel model=lenovo-nb0763

in

/etc/modprobe.d/alsa-base.conf

i tried many of the other models, including the more obvious fujitsu but only the above worked, hope it helps.

---

### Post by xfctr on 2009-11-23
> **xxfrankxx said:**
> I have a fujitsu-siemens Amilo Pi 1536 and I experienced the same issue, it got solved as well by setting:

options snd-hda-intel model=lenovo-nb0763


Thanks, man! That worked for my Pi 1536 too (on Karmic). 
Vaguely related - have you managed to make the volume wheel work?

---

### Post by micwo on 2010-08-18
> **xfctr said:**
> Thanks, man! That worked for my Pi 1536 too (on Karmic). 
Vaguely related - have you managed to make the volume wheel work?

That worked also for my Fujitsu Siemens Amilo Pro V3525 laptop! (my soundcard is Realtek ALC883, I use Ubuntu 10.04) I had a problem with my sound: headphones and laptop speakers were playing simultaneously - now everything works fine; when I want to use my headphones, after putting phones jack PC speakers are turning off.
Thx!

I've added this line:
options snd-hda-intel model=lenovo-nb0763
to: /etc/modprobe.d/alsa-base.conf

---

