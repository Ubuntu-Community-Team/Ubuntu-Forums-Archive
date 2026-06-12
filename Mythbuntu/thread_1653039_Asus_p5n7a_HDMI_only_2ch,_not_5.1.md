---
title: "Asus p5n7a HDMI only 2ch, not 5.1"
date: 2010-12-26
forum: Mythbuntu
---

### Post by daniel53 on 2010-12-26
So I've set it to hdmi output in the BIOS. I've unmuted all "SPDIF" devices in alsamixer.

I get sound when i play movies, however only the front L/R speakers work. There is no voices, since these usually play through the center channel, which does not work.

This is a very frustrating problem, any help would be greatly appreciated. Running alsa 1.0.23 on the latest 10.10 ubuntu. 

I've setup mythbuntu to play thru plughw:0,3.

I've tried everything I can to get it to output the full 5.1 channels over hdmi, but I'm at my end. Someone please help! This is on an Asus p5n7a motherboard.

---

### Post by BicyclerBoy on 2011-01-06
HDMI & S/PDIF are not one in the same..

On 1st gen video cards the S/PDIF header was linked to the video card for hdmi audio.

The current gen video cards has/appears with its own audio device (>1).

Your 2ch S/PDIF is PCM
To get 5.1 S/PDIF you must use AC3 DTS matrix encoded digital pass thru' to AVR HT amp.

Your player is decoding 5.1 audio & down-mixing it to 2 ch PCM.
The down-mixing is badly configured (maybe ffmpeg bug).

S/PDIF does not support: 5.1 LPCM or EAC3 DTS-MA.

I guess you are trying use the on-board video GPU & hdmi audio.

Problem could be the video driver..

What does 
aplay -l
aplay -L
return ?

---

