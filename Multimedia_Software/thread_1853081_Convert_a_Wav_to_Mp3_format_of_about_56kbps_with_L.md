---
title: "Convert a Wav to Mp3 format of about 56kbps with LINUX"
date: 2011-10-01
forum: Multimedia Software
---

### Post by honeybear on 2011-10-01
Hello,

I would like to know if it can be converted with linux: 

 Wav to Mp3 format of about 56kbps

I would like to do it with something else than lame. Can it be possible? 

Thank you !!

---

### Post by AnotherMuggle on 2011-10-01
> **honeybear said:**
> Hello,

I would like to know if it can be converted with linux: 

 Wav to Mp3 format of about 56kbps

I would like to do it with something else than lame. Can it be possible? 

Thank you !!

Sound Converter will do the conversion, but the lowest bitrate is 64kbps and the Gstreamer lame plugin is required for MP3... that may or may not help you!?

---

### Post by nothingspecial on 2011-10-01
Yes, you can use ffmpeg with the -ab option.

The people to tell you how do do exactly what you want to do will be more likely to find your question here.

Moved to Multimedia & Video

---

### Post by TeoBigusGeekus on 2011-10-01
```
ffmpeg -i /path/filename.wmv -acodec libmp3lame -ab 56k /path/filename.mp3
```

---

### Post by FakeOutdoorsman on 2011-10-01
> **honeybear said:**
> I would like to do it with something else than lame.

Why not LAME? If you change your mind:
```
lame --abr 56 input.wav output.mp3
```
[HydrogenAudio LAME](http://wiki.hydrogenaudio.org/index.php?title=LAME#Very_low_bitrate.2C_small_sizes:_eg._for_voice.2C_radio.2C_mono_encoding_etc.) page claims ABR is the way to go for bitrates below 100kbps.

---

### Post by honeybear on 2011-10-01
> **nothingspecial said:**
> Yes, you can use ffmpeg with the -ab option.

The people to tell you how do do exactly what you want to do will be more likely to find your question here.

Moved to Multimedia & Video


I havent liblame installed into my PC at collegue :(  :( 
```
 ffmpeg  -ab -i 20110928-210058_do.wav  20110928-210058_do_test.mp3
FFmpeg version SVN-r0.5.2-4:0.5.2-6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.2-6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct  5 2010 08:33:07, gcc: 4.4.5
Unable to parse option value "i": undefined constant or missing (
Invalid value '-i' for option 'ab'

```

---

### Post by TeoBigusGeekus on 2011-10-01
```
ffmpeg -i 20110928-210058_do.wav -acodec libmp3lame -ab 56k 20110928-210058_do.mp3
```

---

### Post by Paddy Landau on 2011-10-01
As I understand it, MP3 format is copyright and you need Lame to convert it. I have never seen MP3 conversion without it (but I'm not expert, so I may be mistaken).

Can you not request a Lame library to be installed?

---

### Post by honeybear on 2011-10-01
> **Paddy Landau said:**
> As I understand it, MP3 format is copyright and you need Lame to convert it. I have never seen MP3 conversion without it (but I'm not expert, so I may be mistaken).

Can you not request a Lame library to be installed?
on this machine, nope. 


Well, from your input, - thank you, I might go to opensource direction. 

I think that there is only OGG that is opensource. I have read that OGG is also very good. 

How would you advice to convert a WAV to OGG to achieve the highest quality performances and keep a moderate size? 
Is actually MP3 better than OGG? I have heard that the best format is mp3pro.

I would use mencoder, mplayer, ffmpeg that are installed on any linux machines, in most cases.

- And the other question. If I use OGG, then, it is likely  not installed on Windows W95, W98, ...or W2000, or likely not work...(on default installed OS system) is it true?

---

### Post by FakeOutdoorsman on 2011-10-01
> **honeybear said:**
> I havent liblame installed into my PC at collegue :(  :(
MP3 encoding with FFmpeg must be enabled manually by the user. You just need to install one package. See option B at:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

> **honeybear said:**
> 
```
 ffmpeg  -ab -i 20110928-210058_do.wav  20110928-210058_do_test.mp3
...
Unable to parse option value "i": undefined constant or missing (
Invalid value '-i' for option 'ab'

```

Your ffmpeg command is incorrect. Options placed before "-i" generally apply to the input, and you also did not provide a value for *-ab*. See posts #4 and #7 by TeoBigusGeekus for some examples with proper option placement.

> **honeybear said:**
> I think that there is only OGG that is opensource.
LAME is open source too. Anyone can freely view the source code.

> **honeybear said:**
> How would you advice to convert a WAV to OGG to achieve the highest quality performances and keep a moderate size?
Ogg is a container format that can hold several audio formats including Vorbis, FLAC. and a few others. Examples:
```
ffmpeg -i input.wav -acodec libvorbis -aq 4 output.ogg
```
or install the vorbis-tools package which will provide oggenc:
```
oggenc -q 4 input.wav output.ogg
```
Increase the *-aq* value in FFmpeg or *-q* value in oggenc to increase the audio quality. There are also a number of graphical applications that you can use to encode with, but I'm not familar with any.

---

### Post by shantiq on 2011-10-02
this should do it altho i am not sure whether libsox-fmt-all goes and grabs lame or not



```
sudo apt-get install sox libsox-fmt-all

```    to install sox


then

```
sox filename.wav -C 56 final.mp3 
```


=======================BATCH CONVERT=================


```
for f in *.wav; do sox "$f" -C 56 "${f%.wav}.mp3"; done
```

---

### Post by honeybear on 2011-10-02
another important question, if choosing OGG, is it compatible with windows95 or windows98 ?

---

### Post by shantiq on 2011-10-02
> **honeybear said:**
> another important question, if choosing OGG, is it compatible with windows95 or windows98 ?


no problem


run


```
oggenc -b 56k  filename.wav
```



and you are sorted :KS


or use soundconverter or soundkonverter    both of which are in your synaptic

---

### Post by honeybear on 2011-10-02
> **shantiq said:**
> no problem


run


```
oggenc -b 56k  filename.wav
```



and you are sorted :KS


or use soundconverter or soundkonverter    both of which are in your synaptic

I tried ogg but it displayed an error.

I have here too some mssage but I am still unsure if it okay or not... 

```


 ogg123  -b 56k   20110928-210058_pa.wav  20110928-210058_pa_2.ogg

Audio Device:   Advanced Linux Sound Architecture (ALSA) output

Error opening 20110928-210058_pa.wav using the oggvorbis module.  **The file may be corrupted.**

Playing: 20110928-210058_pa_2.ogg
Ogg FLAC stream: 16 bits, 2 channel, 44100 Hz
                                                         
Done.

```

from a 353k wav file, I get: 

> ffmpeg -i input.wav -acodec libvorbis -aq 4 output.ogg
11k

> ffmpeg -i audio.wav -acodec vorbis -aq 60 audio.ogg
33k
and no error displayed. 

Maybe -aq 60 has higher quality than mp3pro ...

---

### Post by shantiq on 2011-10-02
honeybear


tried your ogg123 and got same result as yours but this works

```
oggenc -b 56k  filename.wav

```


are you trying to convert a long lecture or similar is that why you want such low kbps?


never heard of [**mp3pro**]("http://www.mp3prozone.com/index.htm") sounds intriguing


==================================

ok tried it very good you can install it under Wine works perfectly

---

### Post by honeybear on 2011-10-03
> **shantiq said:**
> honeybear

never heard of [**mp3pro**]("http://www.mp3prozone.com/index.htm") sounds intriguing


I have been often said that mp3pro was the best sound quality/size ratio. But who really knows. OGG might certainly do the same ... 
(but not sure if all old w95 and all PC's can read it in a possible complex codec case)

---

### Post by andrew.46 on 2011-10-04
ogg123 is a decoder of course, not an encoder. It used to have a distant relative called flac123 I seem to remember...

---

### Post by v1ad on 2011-10-04
[http://audacity.sourceforge.net/download/](http://audacity.sourceforge.net/download/)

Audacity just did some work :D has a gui too

---

### Post by andrew.46 on 2011-10-06
> **shantiq said:**
> ```
sox filename.wav -C 56 final.mp3 
```

Just a final thought about sox and mp3 encoding..... Rather than use a set bitrate it is possible to setup VBR encoding through sox and lame, aiming at roughly 56k output file, by using a commandline like the following:

```
sox --show-progress test.wav -C -9 output.mp3
```

I encoded using the above syntax and mediainfo reveals the gory details of the output file:

```

andrew@skamandros~/Desktop$ mediainfo output.mp3 
General
Complete name                            : output.mp3
Format                                   : MPEG Audio
File size                                : 16.2 MiB
Duration                                 : 29mn 4s
Overall bit rate mode                    : Variable
Overall bit rate                         : 77.9 Kbps
Writing library                          : LAME3.98r

Audio
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Duration                                 : 29mn 4s
[B][COLOR="Red"]Bit rate mode                            : Variable
Bit rate                                 : 77.9 Kbps
Minimum bit rate                         : 32.0 Kbps
Channel(s)                               : 2 channels[/COLOR][/B]
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 16.2 MiB (100%)
Writing library                          : LAME3.98r
Encoding settings                        : -m j -V 9 -q 0 -lowpass 9.5 --vbr-new -b 32


```

The negative settings for the -C option are of course taken [from here]("http://wiki.hydrogenaudio.org/index.php?title=LAME#VBR_.28variable_bitrate.29_settings").

---

### Post by shantiq on 2011-10-07
nice refinement there Andrew :KS

---

