---
title: "Distorted sound with xVid playback"
date: 2008-07-31
forum: Multimedia Software
---

### Post by mstephens on 2008-07-31
I've created some xVid DVD backups using AutoGK on Windows. The files playback fine on a Windows system but when I play them on my Ubuntu 7.04 PC the video is great but the sound is rubbish.

I have tried two different versions one with MPEG Layer 3 sound and one with AC3 (basically a straight 192kbps copy from the DVD) but both have the same problem - essentially a tinny sound which sounds similar to a poor signal on a DAB radio.

I have tried loading every codec package I can find but nothing seems to make any difference. The problem exists with Totem. Mplayer and VLC. 

I can playback audio files (MP3 and WMA) without a problem and WMV video files work OK with good sound as well. I haven't tried any other video formats yet.

The soundcard is a Creative Technologies CT4502 Soundblaster AWE64 ISA card which I have never been able to get to work under ALSA despite dmesg showing that the card has been recognised, manually adding various lines to files etc so I have to use the OSS drivers - however I assume that codecs work at a higher level than the soundcard drivers and that the same codecs are used whatever the underlying sound system is.

The codecs being used according to VLC are XVID and mpga (for the mp3 version of the file) and a52 (for the AC3 version).


Any ideas ?

Added:
Should have mentioned that the Ubuntu box is an ancient  350MHz Compaq. Don't think that the fact it's a relatively slow machine is the problem as video playback is very smooth and there is a low loss rate of audio buffers according to VLC ( 60 out of 32000)

---

### Post by mstephens on 2008-08-01
I eventually worked out the problem was caused by the sound bitrate being too high!

Using exactly the same conversion software but forcing down the bitrate to around 60kbps produced a file which was playable.

Not sure whether it is the ISA Soundblaster AWE64 card which can't cope, the fact I am using OSS instead of ALSA or what. 

In trying to resolve this problem I had several more attempts at getting the Soundblaster to work with ALSA - all the tips on here failed so I will probably get a cheapo PCI soundcard at some point.

---

