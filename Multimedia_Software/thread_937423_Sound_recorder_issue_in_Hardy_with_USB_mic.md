---
title: "Sound recorder issue in Hardy with USB mic"
date: 2008-10-03
forum: Multimedia Software
---

### Post by zergnerd on 2008-10-03
**Issue:**  Sound Recorder (nor Audacity 1.3.4) will not will not record sound  from a logitech USB microphone in Ubuntu Hardy.

I have verified that the Alsa drivers do see the microphone.  Using arecord as follows:

$ arecord -f cd -c 1 -D hw:default, 0 -d 5 test.wav

works just fine.  I do notice that I must explicitly specify the number of channels to get arecord to work.  Otherwise I get the classic "Channels count non available" error.

My current suspicion is that a number-of-channels setting is missing from an Alsa config file and this prevents sound recording GUI's from working correctly; however, I don't know where to look for such a setting.

Thank you for your help.

Zergnerd

---

### Post by markbuntu on 2008-10-03
ALsa should automatically set the channels, it does that for my logitec usb webcam and my usb headset. Sound recorder just uses the default capture device that is specified in System/Preferences/Sound/Audio Conferencing/Sound Capture so you should set that to USB Device. If PulseAudio is running, you need to set the default device in the Pulse audio Volume Control. This will not work for Audacity since it does not work with PulseAudio.

---

### Post by shreepads on 2010-01-25
> **markbuntu said:**
> ALsa should automatically set the channels, it does that for my logitec usb webcam and my usb headset. Sound recorder just uses the default capture device that is specified in System/Preferences/Sound/Audio Conferencing/Sound Capture so you should set that to USB Device. If PulseAudio is running, you need to set the default device in the Pulse audio Volume Control. This will not work for Audacity since it does not work with PulseAudio.

Same problem on Ubuntu Hardy...

Tried the setting suggested above, but when I start up Sound Recorder post that I get an error message:

"Your audio capture settings are invalid. Please correct them in the Multimedia settings."

This message doesn't appear when I reset the System/Preferences/Sound/Audio Conferencing/Sound Capture setting to ALSA, but sound recording doesn't work either.

Two things convince me that there is no underlying hardware or driver problem
- The 'Test' button next to System/Preferences/Sound/Audio Conferencing/Sound Capture works fine on selecting 'USB Audio'
- Am using the same usb device on Skype and is working perfectly

Tentative conclusion: Sound Recorder doesn't support USB Audio... Why that is so is a bit of a mystery...

System Details: Ubuntu Hardy 8.04, 2.6.24-26-generic kernel, 2GB RAM, Intel C2D E7200, Intel DG33FB board, Ranger RUP-200 USB VOIP phone

---

### Post by shreepads on 2010-01-31
> **zergnerd said:**
> **Issue:**  Sound Recorder (nor Audacity 1.3.4) will not will not record sound  from a logitech USB microphone in Ubuntu Hardy.

OK installed Audacity thinking this would work there but it didn't at first. Got this working in Audacity 1.3.4 after reading some tips online and the Audacity team blog and some plain dumb luck...

Steps:
- System/Preferences/Sound/Audio Conferencing/Sound Capture -> PulseAudio Sound Server. Hit the 'Test' button next to it and check
- Start Audacity, go to Edit/Preferences:
   a. Audio IO/Recording/Device -> OSS: /dev/dsp1
   b. Audio IO/Recording/Channels -> 1 (Mono)
   c. Quality/Default Sample Rate -> 44100 Hz
   d. Quality/Default Sample Format -> 16 bit
- Hit 'OK' and restart Audacity, check that settings as above have held

Devices : Linux == Oil : Water :-)


EDIT: Now plain old Sound Recorder is working as well!!

---

