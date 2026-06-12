---
title: "DragonFly DAC, Ubuntu 16.04: just 48 khz instead of 96"
date: 2019-02-12
forum: Multimedia Software
---

### Post by Elwro on 2019-02-12
Hello,

I'm trying to use my DragonFly Black 1.5 DAC with Ubuntu 16.04 on a laptop. I'm playing 96khz files via qmmp; the log contains stuff like:
```
BITRATE = 2744
SAMPLERATE = 96000
CHANNELS = 2
BITS_PER_SAMPLE = 32
FORMAT_NAME = FLAC
DECODER = flac
FILE_SIZE = 21263646

```

However, the DragonFly only plays them at 48 khz:

```
~$ cat /proc/asound/card1/stream0
AudioQuest AudioQuest DragonFly Black v1.5 at usb-0000:00:14.0-3, full speed : USB Audio


Playback:
  Status: Running
    Interface = 1
    Altset = 1
    Packet Size = 360
    Momentary freq = 48000 Hz (0x30.0000)
    Feedback Format = 10.14
  Interface 1
    Altset 1
    Format: S24_3LE
    Channels: 2
    Endpoint: 1 OUT (ASYNC)
    Rates: 44100, 48000, 88200, 96000

```


My Qmmp uses ALSA.

What should I do to achieve the desired 96 khz?

Thanks in advance!

I tried searching for stuff to put into .asoundrc and related, but only managed to corrupt my system, hence the question.

---

