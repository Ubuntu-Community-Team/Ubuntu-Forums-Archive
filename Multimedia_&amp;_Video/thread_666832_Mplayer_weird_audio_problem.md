---
title: "Mplayer weird audio problem"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by Snyper64 on 2008-01-13
I am getting weird messages in Mplayer(flickers on and off and have to pause video to read it) that says "[AO_ALSA] Mixer attach default error: No such device" but the audio is working fine. I have 2 sound cards but I blacklisted my on-board sound card and use a USB Turtle Beach Audio Advantage Amigo card. Heres my Aplay output: ```
snyper64@snyper64-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: U0x10f50x210 [USB Device 0x10f5:0x210], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
snyper64@snyper64-laptop:~$
```

I am using hw1,0 for my sound card in Mplayer. I have set up an asoundrc file a while ago but I guess mplayer ignores it. Also in the drop-down for devices in the Mplayer ALSA config the only hardware that shows up are the following(but none of them work): default driver default hw=o,o hw=0.1 hw=0.2 surround40 surround51 plug=surround40 plug=surround51

Any help would be truly appreciated as I have 13 eps of Shakugan no Shana Second in mkv format that I want to watch but no other media player I have(VLC, Movie Player, Gxine) plays the subs right.

EDIT: Also my sound works fine for every other media player I have using hw1,0 and I recieve no other errors in any of them about sound devices being missing.

---

### Post by Snyper64 on 2008-01-14
bump

---

### Post by Snyper64 on 2008-01-21
bump

---

### Post by Snyper64 on 2008-01-28
bump

---

### Post by elcasey on 2008-02-07
Instead of blacklisting the driver for your onboard sound, why don't you disable it in the BIOS? This might help...just a suggestion.

---

### Post by Snyper64 on 2008-02-07
I have already tried that, but since I am on a laptop it doesn't give me that option.

---

