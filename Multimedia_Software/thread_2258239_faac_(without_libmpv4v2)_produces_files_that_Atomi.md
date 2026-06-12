---
title: "faac (without libmpv4v2) produces files that AtomicParsley cannot tag..."
date: 2014-12-25
forum: Multimedia Software
---

### Post by andrew.46 on 2014-12-25
I was hoping for a work around for a difficult bug that I have picked up while working an abcde:

[LIST=1]
[*] In Ubuntu faac is shipped without libmp4v2 support so much mp4 support is missing.
[*] As a quick and dirty fix for aac tagging abcde uses AtomicParsley.
[*] However I have found that AtomicParsley refuses to tag such files.
[*]
[/LIST]

An example of the problem is here:

```

andrew@corinth:~/Desktop$ **[COLOR="#FF0000"]faac luckynight.wav -o test.m4a[/COLOR]**
Freeware Advanced Audio Coder
FAAC 1.28

WARNING: MP4 support unavailable!
Quantization quality: 100
Bandwidth: 16000 Hz
Object type: Low Complexity(MPEG-2) + M/S
Container format: Transport Stream (ADTS)
Encoding luckynight.wav to test.m4a
   frame          | bitrate | elapsed/estim | play/CPU | ETA
 2606/2606  (100%)|  133.0  |    1.5/1.5    |   40.72x | 0.0 

andrew@corinth:~/Desktop$ **[COLOR="#FF0000"]AtomicParsley test.m4a --title "Lucky Night" [/COLOR]**

AtomicParsley error: bad mpeg4 file (ftyp atom missing or alignment error).

andrew@corinth:~/Desktop$ 

```

An exasperating issue as I am attempting to resurrect aac encoding with abcde :(. Any thoughts on this issue which has probably been in place since Ubuntu stopped compiling in mp4 support for faac?

---

### Post by Yellow Pasque on 2014-12-26
It looks like AP only operates on MPEG-4. So, you'll have to use an encoder that supports mp4, or you can take the output of faac and find some other way to put it in an mp4 container, like in the example below.

Normally, when you use an .m4a extension with faac, it will automatically use an mp4 container, but in your example, faac is forced to use mpeg-2/ADTS, so giving that file an .m4a extension is misleading. A .aac extension would be more appropriate for such a file. [https://en.wikipedia.org/wiki/Advanced_Audio_Coding#Container_formats](https://en.wikipedia.org/wiki/Advanced_Audio_Coding#Container_formats)

```
$ faac example.wav -o example.aac
Freeware Advanced Audio Coder
FAAC 1.28

Quantization quality: 100
Bandwidth: 16000 Hz
Object type: Low Complexity(MPEG-2) + M/S
Container format: Transport Stream (ADTS)
Encoding example.wav to example.aac
   frame          | bitrate | elapsed/estim | play/CPU | ETA

$ mediainfo example.aac
General
Complete name                            : example.aac
Format                                   : ADTS
Format/Info                              : Audio Data Transport Stream
File size                                : 9.46 KiB
Overall bit rate mode                    : Variable

Audio
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format version                           : Version 2
Format profile                           : LC
Bit rate mode                            : Variable
Channel(s)                               : 1 channel
Channel positions                        : Front: C
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 9.46 KiB (100%)


$ ffmpeg -i example.aac -c:a copy -bsf:a aac_adtstoasc example.m4a
Input #0, aac, from 'example.aac':
  Duration: 00:00:00.98, bitrate: 79 kb/s
    Stream #0:0: Audio: aac (LC), 48000 Hz, mono, fltp, 79 kb/s
Output #0, ipod, to 'example.m4a':
  Metadata:
    encoder         : Lavf56.15.102
    Stream #0:0: Audio: aac (mp4a / 0x6134706D), 48000 Hz, mono, 79 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (copy)


$ mediainfo example.m4a 
General
Complete name                            : example.m4a
Format                                   : MPEG-4
Format profile                           : Apple audio with iTunes info
Codec ID                                 : M4A 
File size                                : 9.98 KiB
Duration                                 : 1s 515ms
Overall bit rate mode                    : Variable
Overall bit rate                         : 53.9 Kbps
Writing application                      : Lavf56.15.102

Audio
ID                                       : 1
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 1s 515ms
Bit rate mode                            : Variable
Bit rate                                 : 48.0 Kbps
Maximum bit rate                         : 79.1 Kbps
Channel(s)                               : 2 channels
Channel(s)_Original                      : 1 channel
Channel positions                        : Front: C
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 8.98 KiB (90%)
```

---

### Post by andrew.46 on 2014-12-26
Thanks, that all makes sense. What I had not realised was that faac has *zero* capacity on its own to utilise an mp4 container and my commandlinie simply tried unsuccessfully to cram an adts stream into an mp4 container. And that the stock Ubuntu abcde has a problem with faac as by default that is exactly what it does...

---

