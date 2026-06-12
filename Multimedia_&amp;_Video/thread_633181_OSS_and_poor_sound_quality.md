---
title: "OSS and poor sound quality"
date: 2007-12-06
forum: Multimedia &amp; Video
---

### Post by kc0eks on 2007-12-06
Hello all,

So long story short is ALSA has never, ever worked right for me in one way or another so I have installed OSS. Now I finally have sound in everything I could want it in. But my problem now is the sound quality is poor.

It is scratchy and poppy I suppose is how I would describe it. Oddly enough the right sound channel seems to be the source of the popping noises. I have used ossxmix to adjust the volumes of the various channels but nothing really helps. If I take the right channel down all the way the left channel sounds half decent.

Any ideas? Thanks all!
-----Info------
Card: Soundblaster Audigy Se
Kubuntu 7.10

Version info: OSS 4.0 (b1009/200711300206) (0x00040003)
Platform: Linux/i686 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 (kc0e
ks-desktop)

Number of audio devices:        4
Number of audio engines:        13
Number of MIDI devices:         0
Number of mixer devices:        1


Device objects
 0: osscore0 OSS core services
 1: audigyls0 AudigyLS
 2: ossusb0 USB audio core services
 3: vmix0 OSS transparent virtual support

MIDI devices (/dev/midi*)

Mixer devices (/dev/mixer*)
 0: AudigyLS Mixer (Mixer 0 of device object 1)

Audio devices
/dev/oss/audigyls0/pcm0 AudigyLS front  (device index 0)
/dev/oss/audigyls0/pcm1 AudigyLS center/lfe  (device index 1)
/dev/oss/audigyls0/pcm2 AudigyLS surround  (device index 2)
/dev/oss/audigyls0/pcm3 AudigyLS 5.1 output  (device index 3)

---

### Post by kyphi on 2007-12-06
ALSA works fine for me via a Creative Soundblaster Live.  The driver is the same as for your Creative Soundblaster Audigy.

The following URLs may be of some use to you:

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs)

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

Have you disabled your on-board sound chip in the BIOS?

---

### Post by kc0eks on 2007-12-06
> **kyphi said:**
> ALSA works fine for me via a Creative Soundblaster Live.  The driver is the same as for your Creative Soundblaster Audigy.

The following URLs may be of some use to you:

[https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCardsCreativeLabs)

[http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound](http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound)

Have you disabled your on-board sound chip in the BIOS?

Hello and thanks for your reply :)

Firstly ALSA worked, it just sucked at working in a large portion of things I wanted it to work in. I tried everything under the sun to fix that, and never got very far. So for the time being I want to try and fix OSS, if that fails I will go back again to ALSA...unless their is a third alternative.

I have disabled my onboard sound, one of the first things I did ;)

I will check out your links for the info thank you much :)

---

