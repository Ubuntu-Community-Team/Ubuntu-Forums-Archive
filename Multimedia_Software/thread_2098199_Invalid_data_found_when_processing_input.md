---
title: "Invalid data found when processing input"
date: 2012-12-25
forum: Multimedia Software
---

### Post by alfirdaous on 2012-12-25
Hello everybody,

I am trying to add some tags into an MP3 file, the error output is:

```

Invalid data found when processing input

```

Code:

```

ffmpeg -i 001.mp3 -metadata title="001" -metadata genre="Music" -metadata date="2012" -metadata comment="www.MyWeb.com" -metadata creation_time="Dec 26 2012 07:40:52" -metadata disc="1" -metadata language="English" -metadata track="001" -metadata variant_bitrate="0" -acodec copy 001C.mp3

```


mediaInfo:

```

General
Complete name                    : 001.mp3
Format                           : MPEG Audio
File size                        : 6.15 MiB
Duration                         : 6mn 43s
Overall bit rate                 : 128 Kbps

Audio
Format                           : MPEG Audio
Format version                   : Version 1
Format profile                   : Layer 3
Format_Settings_Mode             : Joint stereo
Format_Settings_ModeExtension    : MS Stereo
Duration                         : 6mn 43s
Bit rate mode                    : Constant
Bit rate                         : 128 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 44.1 KHz
Stream size                      : 6.15 MiB


```

The input file is in good format and playable

Thx in advance

---

### Post by FakeOutdoorsman on 2012-12-26
Please provide the complete ffmpeg console output that shows up after you enter your ffmpeg command.

---

### Post by alfirdaous on 2012-12-26
I sort it out by adding -f MP3, it seems strange

---

