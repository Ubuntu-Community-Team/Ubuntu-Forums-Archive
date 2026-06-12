---
title: "left &amp; right channel problems"
date: 2008-08-31
forum: Multimedia Software
---

### Post by mathgenius on 2008-08-31
I just updated my 8.04 installation (doh!)
I have two sound devices. One device (the built-in intel one) has lost a channel entirely. The other device (c-media) is extremely difficult to set the balance in either the sound control gui or alsamixer. Both programs behave eratically. The left and right channel continue to "unlock" from each other, if i move the left or right channel, the left channel keeps on jerking around and tending to peg at zero... something like that.. it's obviously not working right.

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

$ dpkg -s alsa-base
Package: alsa-base
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 384
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Architecture: all
Source: alsa-driver
Version: 1.0.16-0ubuntu4

thanks,
Simon.

---

### Post by minky311 on 2008-08-31
I have that same C-Media usb sound adapter and just so you know in order to move the two channels specifically the left one there shouldn't be any sound playing otherwise the left channel just keeps moving to the bottom.
Feel free to ask me any other questions since I got mine working.

---

### Post by mathgenius on 2008-09-01
> **minky311 said:**
> I have that same C-Media usb sound adapter and just so you know in order to move the two channels specifically the left one there shouldn't be any sound playing otherwise the left channel just keeps moving to the bottom.
Feel free to ask me any other questions since I got mine working.

Thanks minky but this didn't seem to help.

---

### Post by minky311 on 2008-09-01
Try using a different mixer for this by going into the synaptic package manager and searching for gnome-alsamixer and installing that which doesn't seem to suffer the same problems as the other ones.

---

### Post by spamer on 2008-09-24
My solution :KS: install gamix using System/SynapticPackageManager.

It works with USB sound devices without mainboard soundcard being detected, what is probably problem of default Ubuntu ALSA mixer GUI.

---

