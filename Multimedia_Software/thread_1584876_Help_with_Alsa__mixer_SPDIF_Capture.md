---
title: "Help with Alsa / mixer SPDIF Capture"
date: 2010-09-29
forum: Multimedia Software
---

### Post by gaz2373 on 2010-09-29
Hi I have managed to set up a usb soundcard and alsamixer shows the SPDIF capture input but it is always set to zero. Can anyone help in explaining how to get thisorking or point me in the right direction.

Cheers

---

### Post by lidex on 2010-09-30
In 'Sound Preferences', on the 'Hardware' tab, select the device and in the drop-down menu below for 'Profile' make sure you have selected a profile with 'Digital Stereo (Iec958) Input'

---

### Post by gaz2373 on 2010-10-04
Hi Thanks for your reply, I have tried this but the only reference I can find is for the ice958 switch no volume control. When I look at amixer output below. The iec958 is reported as mono! The card isn't being picked up right but I'm not sure how to load the driver etc.

Thanks.

root@ubuntu:/etc/init.d# amixer
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch pswitch-joined penum
  Playback channels: Front Left - Front Right - Rear Left - Rear Right - Front Center - Woofer - Side Left - Side Right
  Limits: Playback 0 - 197
  Mono:
  Front Left: Playback 157 [80%] [0.00dB] [on]
  Front Right: Playback 157 [80%] [0.00dB] [on]
  Rear Left: Playback 157 [80%] [0.00dB] [on]
  Rear Right: Playback 157 [80%] [0.00dB] [on]
  Front Center: Playback 157 [80%] [0.00dB] [on]
  Woofer: Playback 157 [80%] [0.00dB] [on]
  Side Left: Playback 157 [80%] [0.00dB] [on]
  Side Right: Playback 157 [80%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: cvolume cswitch cswitch-joined penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 6928
  Front Left: Capture 6928 [100%] [11.06dB] [on]
  Front Right: Capture 6928 [100%] [11.06dB] [on]
Simple mixer control 'PCM Capture Source',0
  Capabilities: enum
  Items: 'Mic' 'Line' 'IEC958 In' 'Mixer'
  Item0: 'IEC958 In'
Simple mixer control 'Line',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 8065 Capture 0 - 6928
  Front Left: Playback 0 [0%] [0.00dB] [off] Capture 0 [0%] [0.00dB] [off]
  Front Right: Playback 0 [0%] [0.00dB] [off] Capture 0 [0%] [0.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 8065 Capture 0 - 6928
  Front Left: Playback 0 [0%] [0.00dB] [off] Capture 0 [0%] [0.00dB] [on]
  Front Right: Playback 0 [0%] [0.00dB] [off] Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'IEC958 In',0
  Capabilities: cswitch cswitch-joined penum
  Capture channels: Mono
  Mono: Capture [on]

---

### Post by gaz2373 on 2010-10-05
If I compile alsa based with a patch submitted to the mailing list editing the usbaudio.c script SPDIF out works, but not SPDIF input. Looking at the data sheet for the chip in my device I think there are some commands not being used to active the input. 
Not sure if this is the right area of the forum but can someone help explain how reg and byte assignments for the usb drivers work.   

e.g the patch uses
        snd_usb_cm106_write_int_reg(dev, 1, 0xb000)
        snd_usb_cm106_write_int_reg(dev, 2, 0x8004)
        snd_usb_cm106_write_int_reg(dev, 3, 0x007f);

which are rest commands but how do you specify a reg and byte value?

---

