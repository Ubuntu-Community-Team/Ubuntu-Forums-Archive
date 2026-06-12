---
title: "Change the default systemwide audio card"
date: 2007-04-01
forum: Multimedia &amp; Video
---

### Post by vladk2k on 2007-04-01
Hello. I have two usb-based audio cards, one is integrated (C-Media CM6501B) and one is an USB headset (Gembird something).

If I boot with the headphones unplugged, all is fine, meaning the system defaults to C-Media as the sound card. However, with the two of them enabled, it defaults on the headset. In Edgy I had the option in the Sound panel to change the default card (on the tab with the login/logout sounds) but that doesn't work anymore in feisty.

I've read [this ALSA-wiki](http://alsa.opensrc.org/FAQ026) and [this bugreport](https://launchpad.net/ubuntu/+source/alsa-driver/+bug/45786) but my problem is that the audio cards use the same audio driver (snd-usb-audio)
```
vladk2k@AthlonuXP:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default_1 [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
You see, the only difference between the two is that the C-Media soundcard is called "PNP Audio Device" instead of USB Audio CODEC.

So, what file do I have to edit and how, to make the system (I'd prefer the system instead of only just my user) to default to PnP Audio Device instead of USB Audio CODEC?

P.S.: I have modified /etc/modprobe.d/alsa-base so that the starting index for snd-usb-audio is 0, not -2 as it is by default.

---

