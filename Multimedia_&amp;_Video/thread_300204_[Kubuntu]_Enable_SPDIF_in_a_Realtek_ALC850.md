---
title: "[Kubuntu] Enable SPDIF in a Realtek ALC850"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by etamax on 2006-11-15
Hi to all!
I am new to the world of Linux but I am trying to make it daily use. The biggest problem that I encountered is to enable the SPDIF output in a Realtek ALC850 integrated in a DFI Lanparty NF4 Ultra-D.
The analogic sound is not good and I want to check if I can improve it using the digital one.
I have already tried to search over the internet but I did not find a solution. I downloaded the driver from the Realtek official site and I installed it. What should I enable now? I.E., how should I set:
kmix
alsamixer
xine parameters
etc?

In kmix I set the "'IEC958 Playback AC97-SPSA" as primary channel. Or have I to choose "Master" or PCM"?

In alsamixer I tried to activate what concern the IEC958 but I found 3 columns:
IEC958: the column is stuck at 00 and the only change that I can do is to make it mute (MM)
'IEC958 Playback AC97-SPSA: I can increase the volume control to 100%
'IEC958 Playback Source: I can change it from Analog to PCM. I set it to PCM.

The xine parameters I don't know how they should be set.

In the audio configuration of KDE and xine I set "auto", without specifing it to alsa or oss.

Ah, obviously I changed the jumper on the motherboard to enable Realtek.

I tried to open Amarok as root, to verify if there were authorization problem, but the problem still remains the same.

What should I do?



Thank you for your answers



PS: sorry for my english :-/

---

