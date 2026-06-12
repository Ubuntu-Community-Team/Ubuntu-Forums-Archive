---
title: "Can't get higher bitrate pcm stream"
date: 2013-09-27
forum: Multimedia Software
---

### Post by Magellan on 2013-09-27
I hvae some flac files that are 96khz/24bit.

I've tried playing them through mulitple players to my AVR (Denon 1909) via the optical connection, and the AVR reports them as 44.1 kHz files.

cat /proc/asound/card0/codec#2 returns:

```
Codec: SigmaTel STAC9271D
Address: 2
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x83847627
Subsystem Id: 0x80864001
Revision Id: 0x100201
No Modem Function Group found
Default PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: ofs=0x00, nsteps=0x0e, stepsize=0x05, mute=0
Default Amp-Out caps: ofs=0x7f, nsteps=0x7f, stepsize=0x02, mute=1
GPIO: io=3, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=1, dir=1, wake=0, sticky=0, data=1, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[2]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Analog Loopback: 0x00
...
Node 0x1e [Audio Output] wcaps 0x40211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="STAC92xx Digital", type="SPDIF", device=1
  Converter: stream=7, channel=0
  Digital: Enabled
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7e0]: 44100 48000 88200 96000 176400 192000
    bits [0xe]: 16 20 24
    formats [0x5]: PCM AC3
  Delay: 4 samples

```

I can't say that I understand all of this, but it seems my sound card is capable of 24 bit 96khz.
Is there anything I should try to get the higher bitrate stream sent to my AVR?

Thanks.

---

### Post by tgalati4 on 2013-09-27
Use *audacity* to create some tones and set the bitrate to 24-bit at 96kHz.  Your card will actually go to 192kHz.  Then play them.  It's possible that your SPIDF connection on your Denon AVR will only do 44.1kHz.  You will have to do some research on that.

---

### Post by Magellan on 2013-10-05
I installed MPD and the Gnome client and was able to conifigure MPD to just send the PCM stream without trying to decode it.  When using MPD, my AV receiver reports receiving a 96kHz file.  
I'll have to figure out where to configure Pulse for this.

---

### Post by tgalati4 on 2013-10-05
There may be some useful stuff in:  [https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)

[http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/Developer/Passthrough/](http://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/Developer/Passthrough/)

Let us know what finally works for you.

---

