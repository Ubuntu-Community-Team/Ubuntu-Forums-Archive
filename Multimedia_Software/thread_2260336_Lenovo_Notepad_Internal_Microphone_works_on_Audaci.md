---
title: "Lenovo Notepad Internal Microphone works on Audacity but not on Google Hangout."
date: 2015-01-11
forum: Multimedia Software
---

### Post by kagashe on 2015-01-11
As posted on previous posts I have installed Ubuntu 14.04 (64 Bit) in dual boot with pre-installed Windows 8.1 on Lenovo G5--45 Notepad.

Yesterday I tried Video Call through Google Hangout but the internal microphone did not work.

I checked Sound_Settings/Input/Internal_Microphone the Input_Level seems to work but I am not sure.

I can record on Audacity and the play back works/

Somewhere I have read about ~/.config/google-googletalkplugin/options and changed "audio-flags=15" to "audio-flags=1" but it does not work.

Note: Apart from the above instructions to set audio-flags=1 there was one more instruction to set left channel of audio input to zero and right channel to max in volume control (pavucontrol) which I had not done. After doing that Google hangout seems to work.

Kamalakar

---

