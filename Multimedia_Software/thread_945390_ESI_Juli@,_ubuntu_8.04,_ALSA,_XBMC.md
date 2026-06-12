---
title: "ESI Juli@, ubuntu 8.04, ALSA, XBMC"
date: 2008-10-12
forum: Multimedia Software
---

### Post by DrErling on 2008-10-12
I got a setup with "a few" soundcards
[LIST]
[*]onboard ATI HD2600 gpu
[*]onboard Asus M3A32-MVP motherboard
[*]ESI Juli@ PCI card with IEC1724 and IEC958
[/LIST]

Running aplay -l gives me this output:
 ```
htpc@XBMC-htpc:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Juli [ESI Juli@], device 0: ICE1724 [ICE1724]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Juli [ESI Juli@], device 1: IEC1724 IEC958 [IEC1724 IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
htpc@XBMC-htpc:~$ 

```

The card I plan to use is the ESI Juli@ digital optical spdif out. I guess it is the "hw:2,1" one.
Trying to find out what card it is using "aplay -D":

```
htpc@XBMC-htpc:~$ aplay -D hw:2,1 /usr/share/sounds/alsa/Noise.wav
Playing WAVE '/usr/share/sounds/alsa/Noise.wav' : Signed 16 bit Little Endian, Rate 48000 Hz, Mono
aplay: set_params:901: Sample format non available
htpc@XBMC-htpc:~$ 

```

no sound.

When opening Rhythmbox and playing a .mp3/.wav/.flac I get sound of good quality.

Problem is, I cannot yet get sound from inside XBMC. Does anyone have a sollution or tip?

DrE

---

### Post by DrErling on 2008-10-12
Only by choosing IEC1724 IEC958 can I get sound

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=88143&stc=1&d=1223855018[/IMG]

I cannot hear login/logout sounds or sounds inside XBMC.

DrE

---

### Post by Tom Mann on 2008-12-10
try adding

blacklist snd-hda-intel

to your /etc/modprobe.d/blacklist file - I had a similar problem where the ATI HDMI took over all sound, and this was how I cleared it.

---

