---
title: "No sound over HDMI after upgrade from 9.04 to 9.10 (64 bit)"
date: 2010-01-23
forum: Multimedia Software
---

### Post by uellue on 2010-01-23
Hi,
On Ubuntu 9.04, sound over HDMI was working fine after I set HDMI output as default in .asoundrc. Now I upgraded to 9.10, and by no means I can get any sound via HDMI. Analog output to headphones works, however.

The HDMI output device is present in the output of aplay -l and aplay -L, but whenever I try to direct sound to it (like, for example, aplay -Dplug:hdmi  test.wav), the result is silence (both headphones and connected TV via HDMI) without any error message. It's like redirecting the sound to a black hole. If I use Windows Vista on the same machine, sound via HDMI still works.

I've tried unmuting all sorts of channels in alsamixer.
I've also tried to remove pulseaudio and work directly with alsa.
Although I found a lot of posts reporting similar problems, I could get none of the presented solutions working.

Now I am at the end of my wits. My last choice would be to switch back to 9.04. Or do you think that recompiling alsa drivers or downloading the latest graphics driver from NVidia would make any difference?

System information:
The computer is a media center PC from Medion with NVidia MCP79 chipset and GeForce 9300 onboard graphics card.

Do you need more information than in the attached files?
Thank you for your suggestions!

---

