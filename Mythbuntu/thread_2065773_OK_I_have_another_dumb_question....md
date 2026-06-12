---
title: "OK I have another dumb question..."
date: 2012-10-02
forum: Mythbuntu
---

### Post by cptrohn on 2012-10-02
I had my mythbox hooked up to the TV with a DVI-VGA adapter and then had the VGA cable hooked up to the TV..

When I would power on the mythbox I would notice that I would drop channels (using OTA HDTV signal in the USA)

So as a test to solve this issue I had a DVI to HDMI adapter that I used to connect it to the HDTV.  Bingo, no more dropped channels as far as reception goes..

LOL Only now there is no sound to the TV.......

Is the HDMI taking over the sound throughput to the TV?  I have an NVIDIA based Graphics card installed as well....  Is this an issue other folks have run into?  Any work arounds?

Thanks for taking the time to read this and any help at all is appreciated!

---

### Post by larsolav on 2012-10-03
How did you get sound to the TV before?
If I understand you correctly, before your TV would get the video signal to its VGA input. Your TV probably has an audio input (probably RCA audio input) which it used as the audio source when you selected the VGA input as your video source. But now, when your TV uses the HDMI input as the video source, your TV will expect that the audio also will come over the HDMI. But DVI does not include sound, so no sound is going through the HDMI cable... I doubt your TV can be set up to have HDMI video input and RCA audio input at the same time....

---

### Post by albandy on 2012-10-03
My Tv let use the image from HDMI and the audio from the audio connector for PC. So check you tv setup, maybe your tv can do this.

---

### Post by Rotak on 2012-10-05
To find out whether you can send audio via HDMI, you can open a terminal and run "aplay -l". If it shows HDMI audio device/s, you can post the output here and I can help you with the setup.

To make this work, it usually requires to have the NVIDIA driver installed.

---

