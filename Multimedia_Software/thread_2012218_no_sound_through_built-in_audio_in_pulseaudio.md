---
title: "no sound through built-in audio in pulseaudio"
date: 2012-06-28
forum: Multimedia Software
---

### Post by dpstatic on 2012-06-28
I can hear audio through speakers and headphones (both built-in audio), but on pulse audio it does not recognize any sound from the monitor of built-in audio (built-in audio is my microphone, which it does recognize).  Although I can hear, I am unable to record sound through the sound card, which I need to do when screencasting. 

How can I fix this?

---

### Post by flemur13013 on 2012-06-28
I always end up installing "pavucontrol" to record from the card.

 - Start the recording program and make it try to record.

 - pavucontrol -> Recording -> select "Monitor of..." in the upper-right.

pavucontrol won't show the recording options unless something's trying to record...

---

### Post by dpstatic on 2012-06-29
Pavucontrol seems to be the same thing as pulseaudio. and that is exactly what I have been trying to do (record from monitor of built-in audio). Even though I can hear the audio, pulseaudio doesn't seem to recognize any audio going through the output of of built-in audio.

---

### Post by ickefes on 2012-08-20
I have the exact same problem with my *Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller [8086:1c20] (rev 05)*. I can't use SKype which I hoped I would be able to.

I can record through my internal microphone using ALSA in Audacity but it is as soon as a program that use Pulseaudio that I am not able to record or send audio using my built in microphone.

My computer has an internal microphone located above the display and there is a 3.5mm input on the side next to the 3.5mm output. In windows 7 the computer recognizes if I have a mic plugged into the 3.5mm or not and chooses the correct "capture method". But I wonder if Ubuntu/Linux does this incorrect.

How would one edit the pulseaudio configuration files to manually specify which soundcard input that should be used and not rely on automatic settings?

Regards.

---

