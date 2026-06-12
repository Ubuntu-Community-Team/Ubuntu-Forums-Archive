---
title: "HDMI sound card not working"
date: 2010-12-26
forum: Multimedia Software
---

### Post by EZonme on 2010-12-26
Hi, 

I have just installed kubuntu 10. My mobo is ASUS p7h55, which has two on board sound cards, one for stereo and the other for outputting sound through the hdmi link. When I connect my TV through HDMI, there is no sound. 
I go to Phonom, and there is only one card in the card selection box.
I run aplay -l, and both cards are listed.
Any idea how I can get sound through the HDMI card?

---

### Post by Tom G. on 2011-01-01
Hello,

Sorry to hear that.  I have found a workaround though.

My situation is a bit different, in that the MULTIMEDIA settings in kde show both cards, but the test button does not output any sound when the HDMI is selected.

The gstreamer phonon backend:
      seems to play sound out of the non-hdmi output reguardless of the HDMI being the default .  

While the xine backend does not play any sound when the HDMI is default

WORKAROUND:
In VLC audio settings, choose the ALSA driver, and select the HDMI output.  This bypasses phonon and pulseaudio...  Only trouble is that is will not follow the multimedia setting default.

Look at this link to test your HDMI output [http://crunchbanglinux.org/forums/topic/2310/hdmi-ati-hda-sound-how-i-got-hdmi-sound-working-in/](http://crunchbanglinux.org/forums/topic/2310/hdmi-ati-hda-sound-how-i-got-hdmi-sound-working-in/)

[tom@Cisco Downloads]$ aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

