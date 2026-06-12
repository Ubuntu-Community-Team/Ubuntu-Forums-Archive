---
title: "Set up an A2DP receiver without using pulse"
date: 2012-09-21
forum: Multimedia Software
---

### Post by Arthurand on 2012-09-21
Hello everyone,

I use Ubuntu Server 10.04 LTS (64bit) with graphic interface installed and a bluetooth adapter and I would like to use it as an A2DP receiver. I was willing to connect, for example, a tablet and transfer its audio to the computer speakers. I have already read a lot of procedures, including on this forum that works perfectly with pulse. But it happens that I do not use pulse because a series of incompatibities that my scripts have with it, like being unable to be run as root and the enormous delay between the playback of sound files. Anyway, I have done some configuration on /etc/bluetooth/audio.conf and set it to "Enable=Source" and when I run "sdptool search --bdaddr local a2snk", I get this in return:

```

Searching for a2snk on FF:FF:FF:00:00:00 ...
Service Name: Audio Sink
Service RecHandle: 0x10008
Service Class ID List:
  "Audio Sink" (0x110b)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x102
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0102

```By what I read, it means that the PC is in fact reporting to have the audio receiving service enabled. So I got my tablet connected to the PC and it appears to maintain some audio link established by what Blueman shows and there is no sound on my tablet speakers and so on my PC. On other tutorials, I have read that, using some pulse commands, I could route the sound stream to the PC speakers, but I don't know how to do this with alsa, because it shows no new "sound card" anywhere and there isn't any new device on /dev either. Does someone know a non-pulse solution for that?

Thanks in advance.

---

