---
title: "Problems with front panel audio and audio capture"
date: 2011-07-17
forum: Multimedia Software
---

### Post by KGigi on 2011-07-17
Hi!

I installed Kubuntu 11.04 a few days ago. This is the first linux on this PC so I don't have any experiences. The relevant part of my configuration is:
Creative X-fi Xtreme Audio PCI-Express sound card
Leadtek DTV 2000H tuner card
ATI Radeon HD 3870 video card with HDMI (two of them in CF)
Cooler Master CM-690 case with the front panel audio.

I have three problems with audio and I think they are related.
[list=1][*]If I plug in my headphones to the front panel, the speakers don't get muted. This works fine if I plug it in to the speakers' jack. I have a channel called 'headphones' in alsamixer, but it doesn't seem to control anything. PCM affects the speakers and the headphones too.
[*]I cannot use neither the front panel mic jack, nor the line in, and I cannot see anything happens in Pulseaudio when I use my microphone.
[*]The tuner card's audio out is connected to the sound card with an external cable via the sound card's line in. With TVtime I have picture and I can find the channels, but I have no sound. At Windows, I have to capture the line in to get sound but here I can hear nothing. I use alsamixer or Pulseaudio to turn on the capture. However I see sound input on a sound card that doesn't exist: Conexant CX8801. This is the chip on the tuner card, but it doesn't have an audio output, it uses the external cable. This card has disappeared when I have updated the ALSA driver, but I still have nothing at line in.
[/list]

What I have tried:
[list=1][*]Upgrade the ALSA driver to the latest.
[*]Modify alsa-base.conf with "options snd-hda-intel model=X", X = { ca0110, CA0110, auto }.
[/list]

The sound card is identified as card 2 (0 and 1 are the video cards) and uses snd-hda-intel (CA0110 chipset), the codec is Creative CA0110-IBG. The speaker profile is Analog Surround 7.1 Output + Analog Stereo Input. (The speakers set is a Creative Inspire T7900.)

Thank you for your help!

---

