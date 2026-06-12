---
title: "No Microphone input acer 3820tg"
date: 2012-01-20
forum: Multimedia Software
---

### Post by trackman44 on 2012-01-20
Hi, I'm new to the forum. I have an Acer Timelinex 3820tg with no microphone input. I go to the sound preferences, I choose the Input tab and there is no option for a input device. I would like to use the internal microphone for comunicating via Skype. I uploaded my alsa results to the alsa project web page. Here is the link.

[http://www.alsa-project.org/db/?f=97ab092704c654782b0fc2d0d954f18af1066380](http://www.alsa-project.org/db/?f=97ab092704c654782b0fc2d0d954f18af1066380)

Any help would be appreciated.

---

### Post by trackman44 on 2012-01-20
I forgot to mention that i'm using Ubuntu 11.10 and the video mode in BIOS is set to 'exclusive'. I also tried the external audio input jack, no luck there either. Please help, I'm at a loss.

---

### Post by trackman44 on 2012-01-20
I figured out what the problem was. In the Sound settings, choose the hardware tag. My laptop has 2 options for sound output, Manhattan HDMI oudio out (thru the HDMI port) and Internal Analog Stereo out, 1 input and 1 output (either thru the internal stereo speakers and internal mic or thru the audio jacks on the side of my laptop). At the bottom there is an option for the settings of audio device. What a dufus i am! It was always set on the "Analog Stereo Output" option( this option disables the internal microphone and input jack). I changed it to "Analog Stereo Duplex" mode. This mode turns on your internal mic or the input jack for external mic or line in. Hope this helps others who have a similar problem.

---

### Post by skullnbones on 2012-12-11
Just wanted to say thanks for this.  It solved my issue since I am using a jack to input a microphone.


Thank you!!!

---

