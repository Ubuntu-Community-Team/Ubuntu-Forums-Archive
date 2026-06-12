---
title: "how to extract 24-bit PCM_bluray audio from a bluray disc?"
date: 2012-12-10
forum: Multimedia Software
---

### Post by shantiq on 2012-12-10
the bluray rip of the disc comes to 32GB !  

now very nice it is indeed but now having viewed it [it is a classical concert]


i want to keep the audio only


i can run this

> for f in *.m2ts; do ffmpeg -i "$f"   "${f%.m2ts}.flac"; done    

or the same to wav but it does not keep the 24-bit

i tried

> **ffmpeg -i 00002.m2ts   -acodec pcm_s24be  -y  00002.wav**
ffmpeg version N-35917-ge4fe4d0 Copyright (c) 2000-2012 the FFmpeg developers
 
Stream mapping:
  Stream #0:1 -> #0:0 (pcm_bluray -> pcm_s24be)
Could not write header for output file #0 (incorrect codec parameters ?): Operation not permitted


i turned to Mencoder/Mplayer



this here i found seems to remove the pcm_bluray but in a format which i see no way of playing


>     mplayer -dumpaudio 00002.m2ts    gives a **stream.dump** file which is the right size 1.1Gb   [see below]  but what do i do with this


anyone one knows how to handle this type of file?






original  specs are


> **Mediainfo**

Audio
ID                                       : 4352 (0x1100)
Menu ID                                  : 1 (0x1)
Format                                   : PCM
Format settings, Endianness              : Big
Format settings, Sign                    : Signed
Muxing mode                              : Blu-ray
Codec ID                                 : 128
Duration                                 : 1h 3mn
Bit rate mode                            : Constant
Bit rate                                 : 2 304 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Bit depth                                : 24 bits
Stream size                              : 1.02 GiB (7%)


**ffmpeg**

    Stream #0:1[0x1100]: Audio: pcm_bluray (HDMV / 0x564D4448), 48000 Hz, stereo, s32, 2304 kb/s

---

### Post by evilsoup on 2012-12-10
Acording to [this]("https://ffmpeg.org/trac/ffmpeg/ticket/210"), what you are describing is a known ffmpeg bug (that ticket is marked as fixed, but that was only last month, so the version you're using probably doesn't have the fix in yet). You could try using flac

```
flac input.wav
```
will produce a file called input.flac

---

### Post by andrew.46 on 2012-12-11
I am not sure if this a great deal of help to you but the latest FFmpeg appears to have preserved 24bit sound from Dolby TruHD to flac. I have to admit that although I have a blueray drive I have only one title which I use for testing purposes :).

After ripping with Makemkv the audio was as follows:

```

Audio #1
ID                                       : 2
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Format settings, Endianness              : Big
Codec ID                                 : A_AC3
Duration                                 : 2h 16mn
Bit rate mode                            : Constant
Bit rate                                 : 640 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 624 MiB (3%)
Title                                    : 3/2+1
Language                                 : English
Default                                  : Yes
Forced                                   : No

**[COLOR="Red"]Audio #2[/COLOR]**
ID                                       : 3
Format                                   : TrueHD
Codec ID                                 : A_TRUEHD
Duration                                 : 2h 16mn
Bit rate mode                            : Variable
Maximum bit rate                         : 3 345 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
**[COLOR="Red"]Bit depth                                : 24 bits[/COLOR]**
Compression mode                         : Lossless
Title                                    : 5.1
Language                                 : English
Default                                  : No
Forced                                   : No

Audio #3
ID                                       : 4
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Format settings, Endianness              : Big
Codec ID                                 : A_AC3
Duration                                 : 2h 16mn
Bit rate mode                            : Constant
Bit rate                                 : 640 Kbps
Channel(s)                               : 6 channels
Channel positions                        : Front: L C R, Side: L R, LFE
Sampling rate                            : 48.0 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 624 MiB (3%)
Title                                    : 3/2+1
Language                                 : English
Default                                  : No
Forced                                   : No

```

and when I converted this to flac with a simple:

```

ffmpeg -i title00.mkv -vn -map 0:2 test.flac

```

the resulting file appears to have preserved 24bit:

```

andrew@skamandros~/Videos/THE_MATRIX$ mediainfo test.flac 
General
Complete name                            : test.flac
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
File size                                : 1.42 GiB
Duration                                 : 2h 16mn
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 486 Kbps
Writing application                      : Lavf54.49.101

Audio
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
Duration                                 : 2h 16mn
Bit rate mode                            : Variable
Bit rate                                 : 1 486 Kbps
Channel(s)                               : 6 channels
Sampling rate                            : 48.0 KHz
**[COLOR="Red"]Bit depth                                : 24 bits[/COLOR]**
Stream size                              : 1.42 GiB (100%)
Writing library                          : Lavf54.49.101

```

I had almost forgotten how working with bluray eats your drive!!

---

### Post by shantiq on 2012-12-11
Thanx guys [both sets of info helped]

esoup indeed was ok once i updated ffmpeg using [guide]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")


it now retains 24-bit whereas previously it turned it to 16

Excellent!!


so now all hi-spec audio can be plucked easily:KS   if it is 5.1 you will need to add ** -ac 6 ** to the line to retain that

```
ffmpeg -i filename.m2ts filename.flac
```

>  mediainfo 00002.flac
General
Complete name                            : 00002.flac
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
File size                                : 562 MiB
Duration                                 : 1h 3mn
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 237 Kbps
Writing application                      : Lavf54.49.101

Audio
Format                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
Duration                                 : 1h 3mn
Bit rate mode                            : Variable
Bit rate                                 : 1 237 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Bit depth                                : **[COLOR="DarkRed"]24 bits[/COLOR]**
Stream size                              : 562 MiB (100%)
Writing library                          : Lavf54.49.101


---

### Post by andrew.46 on 2012-12-11
Again you have good news on these forums Shantiq :)

---

