---
title: "aqualung refuses to start and it was fine before although nothing has been changed"
date: 2010-04-26
forum: Multimedia Software
---

### Post by shantiq on 2010-04-26
[B][COLOR="Blue"]

ok there got problems  starting aqualung on karmic with the synaptic version of aqualung 


 i am getting this at the moment and OSS is not busy so far as i know any ideas anyone?

```
No output driver specified, probing for a usable driver.
Probing OSS driver... device busy
No usable output driver was found. Please see aqualung --help
and the docs for more info on successfully starting the program.

```

ANY IDEAS ANyone?

i have tried ```
aqualung-V
```

got all the info 

```
 

  Decoding support:
    [ ] sndfile (WAV, AIFF, etc.)
    [ ] Free Lossless Audio Codec (FLAC)
    [ ] Ogg Vorbis
    [ ] Ogg Speex
    [ ] MPEG Audio (MPEG 1-2.5 Layer I-III)
    [ ] MOD Audio (MOD, S3M, XM, IT, etc.)
    [ ] Musepack
    [+] Monkey's Audio Codec
    [+] WavPack
    [ ] LAVC (AC3, AAC, WavPack, WMA, etc.)

  Encoding support:
    [ ] sndfile (WAV)
    [ ] Free Lossless Audio Codec (FLAC)
    [ ] Ogg Vorbis
    [ ] LAME (MP3)

  Output driver support:
    [ ] sndio Audio
    [+] OSS Audio
    [ ] ALSA Audio
    [ ] JACK Audio Server
    [ ] PulseAudio
    [ ] Win32 Sound API

```

if i run

```
aqualung -o oss
```

it still tells me it is busy which is horsedung

so i am flummoxed

all clever suggestions welcome

[/COLOR][/B]

---

### Post by shantiq on 2010-04-30
[B][COLOR="Blue"]ok worked it out


tried to install a new package from .bz2 folder


thing is those do not have a lot of the plugins and dependencies in them


so i had to go into the folder again

```
sudo make uninstall
```

and then simply run


```
sudo apt-get install aqualung
```

all fine now

basically i had tried something that was too involved   ( ie having to find all the plugins one by one)


now when i run ```
aqualung -v
```   i get




[/COLOR][/B]```
aqualung -v
Aqualung -- Music player for GNU/Linux
Build version: R-1073
(C) 2004-2009 Tom Szilagyi <tszilagyi@users.sourceforge.net>
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details.

This Aqualung binary is compiled with:

  Optional features:
    [+] LADSPA plugin support
    [+] CDDA (Audio CD) support
    [+] CDDB support
    [+] Sample Rate Converter support
    [+] iRiver iFP driver support
    [+] Loop playback support
    [+] Systray support
    [+] Podcast support
    [+] Lua (programmable title formatting) support

  Decoding support:
    [+] sndfile (WAV, AIFF, etc.)
    [+] Free Lossless Audio Codec (FLAC)
    [+] Ogg Vorbis
    [+] Ogg Speex
    [+] MPEG Audio (MPEG 1-2.5 Layer I-III)
    [+] MOD Audio (MOD, S3M, XM, IT, etc.)
    [+] Musepack
    [ ] Monkey's Audio Codec
    [+] WavPack
    [+] LAVC (AC3, AAC, WavPack, WMA, etc.)

  Encoding support:
    [+] sndfile (WAV)
    [+] Free Lossless Audio Codec (FLAC)
    [+] Ogg Vorbis
    [ ] LAME (MP3)

  Output driver support:
    [ ] sndio Audio
 [COLOR="Red"]   [+] OSS Audio
    [+] ALSA Audio
    [+] JACK Audio Server
    [+] PulseAudio[/COLOR]
    [ ] Win32 Sound API

```

---

