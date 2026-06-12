---
title: "simple screen recorder is not recording sound"
date: 2021-10-03
forum: Multimedia Software
---

### Post by rahul_bhise on 2021-10-03
i am using ubuntu 21.04.
while recording screen, playing a video on screen. only video gets recorded no audio from screen is recorded (only video no sound).
 while logging i use ubuntu on xorg. 
i have tried almost all combinations from setting>sound>input. 
also kazam software is not recording the sound.

---

### Post by T6&amp;sfpER35% on 2021-10-03
does your settings on simplescreenrecorder look like this ?

---

### Post by rahul_bhise on 2021-10-04
found the answer here

[https://www.maartenbaert.be/simplescreenrecorder/troubleshooting/#no-sound-when-recording-the-speakers-with-pulseaudio](https://www.maartenbaert.be/simplescreenrecorder/troubleshooting/#no-sound-when-recording-the-speakers-with-pulseaudio)

If no sound is recorded, make sure the monitor channel is not muted. To do this, go to the "Input devices" tab in PulseAudio Volume Control, select "Show: All input devices" and make sure the "Mute audio" button of the monitor channel is not enabled. (credit goes to 'scrawl' for figuring this out)

---

