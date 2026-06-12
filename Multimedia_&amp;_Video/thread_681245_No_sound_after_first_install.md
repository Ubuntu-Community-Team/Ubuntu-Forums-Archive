---
title: "No sound after first install"
date: 2008-01-28
forum: Multimedia &amp; Video
---

### Post by reggit on 2008-01-28
Hi there,
     I just installed ubuntu and cannot get any sound to play.  aplay -l lists:
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

However, under sound preferences it lists the device being used as Realtek ALC885?
I am trying to use some logitech usb headphones as well.  I've tried installing several new drivers but nothing works as I am not really sure what the problem is.  I have an integrated sound card on a GIGABYTE GA-P35-DS3R LGA 775 Intel P35 ATX Intel Motherboard which is supposed to have a Realtek ALC889A sound chipset.  Thanks for any help or suggestions.

---

### Post by Metaljaz on 2008-01-29
Right click on the volume button in the top right hand corner. Open volume control and make sure that PCM is not muted. Mute PC speaker and Line in to start with.
Then again right click on the volume control button and select preferences. try selecting alsa mixer and then scroll down to PCM. Give that a try.

if all else fails try these troubleshooting threads/wiki:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by FuturistCorporation on 2008-01-30
Are you using a macbook by chance?

---

