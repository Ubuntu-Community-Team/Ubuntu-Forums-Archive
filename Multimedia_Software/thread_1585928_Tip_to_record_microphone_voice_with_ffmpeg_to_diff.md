---
title: "Tip to record microphone voice with ffmpeg to different formats"
date: 2010-10-01
forum: Multimedia Software
---

### Post by shantiq on 2010-10-01
Just record your voice with a microphone to a wave file and leave it on your Desktop



     
     ```
ffmpeg -f alsa -ac 2 -i pulse   -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0  -y  ./Desktop/myVOICE.wav 
```AND just record your voice with a microphone to an alac file


     
```
      ffmpeg -f alsa -ac 2 -i pulse -acodec alac  -y ./Desktop/RecordingMYvoice.m4a 
```to flac


     
```
      ffmpeg -f alsa -ac 2 -i pulse -acodec flac  -y ./Desktop/RecordingMYvoice.flac 
```to aac


     
     ```
ffmpeg -f alsa -ac 2 -i pulse -acodec aac -strict experimental -ab 399k  -y ./Desktop/RecordingMYvoice.aac
```

---

### Post by shantiq on 2010-10-01
not found a way to do this to wavpack/ape and mp3 or ogg yet  ffmpeg says the codecs are not there 


gives message like    ```
Unknown encoder 'oggenc'
```

    but i have all 4    not sure why it says that

---

### Post by ron999 on 2010-10-01
> **shantiq said:**
> not found a way to do this to wavpack/ape and mp3 or ogg yet  ffmpeg says the codecs are not there 


gives message like    ```
Unknown encoder 'oggenc'
```

    but i have all 4    not sure why it says that
You probably need to use **[FONT="Courier New"]-acodec libvorbis[/FONT]**.
If you type **[FONT="Courier New"]ffmpeg -codecs[/FONT]** it will show what's available.

---

### Post by shantiq on 2010-10-01
ok so   wavpack and mp3 only decode and do not encode in ffmpeg that is the answer     thanx


ogg works with libvorbis not oggenc


so if you want to record from mike to ogg



```
ffmpeg -f alsa -ac 2 -i pulse -acodec libvorbis -ab 499k  -y ./Desktop/RecordingMYvoice.ogg

```

499k is the highest in ogg    set it yo what you want most people are probably happy with 120 or even less for voice only recordings



to wma2 


 i think that is lossless but i am not sure you end up with a 1000kbps about very high sound quality




```
ffmpeg -f alsa -ac 2 -i pulse -acodec wmav2 -ab 599k  -y ./Desktop/RecordingMYvoice.wma

```


and for the fun bit if you love to hear your voice in perfect reproduction  why not treat yourself to Microsoft Wav (64-bit float)




your voice will be clearer than a bell   in the 5000kbps region    only for short messages   maybe a love declaration :::)))     maybe not your memoirs in an audio version    but that is clear God it is clear


```
ffmpeg -f alsa -ac 2 -i pulse -acodec pcm_f64le  -y ./Desktop/RecordingMYvoice.wav
```



will record an acoustic guitar off a mike in astounding clarity


for you musicians who cannot be arsed to fire up the big guns and want a quick but quality recording this certainly works then take it to audacity for polishing

---

### Post by FakeOutdoorsman on 2010-10-01
> **shantiq said:**
> to aac
```
ffmpeg -f alsa -ac 2 -i pulse -acodec aac -strict experimental -ab 399k  -y ./Desktop/RecordingMYvoice.aac
```

It's currently generally recommended to use libfaac instead of faac due to the quality differences of their outputs.  Also, the *-aq* option is worth trying out instead of *-ab*.  Unfortunately, the appropriate values are codec specific so what works for one encoder may not work with another.  See each encoder for a good idea of what numbers to use.  faac example:
```
$ man faac
-q <quality>
              Set  default variable bitrate (VBR) quantizer quality in percent
              (default: 100).
```
So a good value for *-acodec libfaac* could be *-aq 100*.

---

### Post by shantiq on 2010-10-01
hi Outdoors

libfaac won't play ball on my system or libfaac0 which is the one in my synaptic    gives me a ```
Duration: N/A, start: 1285956463.992986, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 44100 Hz, 2 channels, s16, 1411 kb/s
Unknown encoder 'libfaac'  or  Unknown encoder 'libfaac0'

```


it is happy with -acodec aac tho   not sure why   but it asks that i use -strict experimental 


ok a clue might be the version of ffmpeg i use   FFmpeg 0.6-4:0.6-2ubuntu3   the default one on maverick so far


 does not have it listed see

```
 D V    kgv1            Kega Game Video
 D V D  kmvc            Karl Morton's video codec
  EV    libdirac        libdirac Dirac 2.2
 D A    libfaad         libfaad AAC (Advanced Audio Codec)
 DEA    libgsm          libgsm GSM
 DEA    libgsm_ms       libgsm GSM Microsoft variant
  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)
 D V D  libopenjpeg     OpenJPEG based JPEG 2000 decoder
 DEV    libschroedinger libschroedinger Dirac 2.2
 D A    libspeex        libspeex Speex
  EV    libtheora       libtheora Theora
  EA    libvorbis       libvorbis Vorbis

```



maybe time for an update

---

### Post by FakeOutdoorsman on 2010-10-01
If *-acodec aac* sounds good for you then you can just use that.  Otherwise you can use **libavcodec-extra-52** from Medibuntu when/if it becomes available to enable *libfaac* in FFmpeg, or compile FFmpeg yourself:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by shantiq on 2010-10-02
ok so a better quality aac/m4a   goes like this   i have set the quality really high  499    take it down to the level you want maybe 150 or 100 to suit your needs 






```
ffmpeg -f alsa -ac 2 -i pulse -acodec libfaac  -aq 499  -y ./Desktop/RecordingMYvoice.aac
```


Aac/m4a   makes sense to be used for a voice recording; there is much literature all over the net to say that for the same size it is always higher sound quality than mp3


and in any case there is no way i can see to record your voice to mp3 directly here with ffmpeg.  Aac is universal and probably a better choice anyway.

---

### Post by ron999 on 2010-10-02
> **shantiq said:**
> 

```

 DEV D  jpegls          JPEG-LS
 D V    kgv1            Kega Game Video
 D V D  kmvc            Karl Morton's video codec
  EA    libfaac         libfaac AAC (Advanced Audio Codec)
  [COLOR="Red"]EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)[/COLOR]
 DEA    libopencore_amrnb OpenCORE Adaptive Multi-Rate (AMR)
```


and in any case there is no way i can see to record your voice to mp3 directly here with ffmpeg.  

It's up there, **[FONT="Courier New"]-acodec libmp3lame[/FONT]**
:)

---

### Post by shantiq on 2010-10-02
MP3
===



```
ffmpeg -f alsa -ac 2 -i pulse -acodec libmp3lame  -aq 0  -y ./Desktop/RecordingMYvoice.mp3
```


or else use -ab  



```
ffmpeg -f alsa -ac 2 -i pulse -acodec libmp3lame  -ab 320k  -y ./Desktop/RecordingMYvoice.mp3
```

---

### Post by aungaung on 2011-01-12
hi, friends.
How to use your command to record voice from microphone?
with php , or not?
And if you can guide me, please example php source code for it.
I am very new to php.
Please......

---

### Post by shantiq on 2011-03-06
also if one just wants a desktop grab** with no sound**


these 2 are good



JUST DESKTOP
=============


```
ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 25 -i :0.0 -sameq ./Desktop/mydesktop.mkv
```


higher quality ==  Careful tough on CPU
----------------


```
ffmpeg -f x11grab -s `xdpyinfo | grep 'dimensions:'|awk '{print $2}'` -r 30 -qscale 1  -i :0.0  ./Desktop/mydesktop.mkv
```

---

### Post by shantiq on 2011-03-10
To maximize the quality of a voice recording to m4a/aac there is yet another route


Many say that **neroAacEnc** knocks spots of the other encoders (attached)


so since ffmpeg does not process that encoder a workaround goes like this

```
  ffmpeg -f alsa -ac 2 -i pulse   -y RecordingMYvoice.wav   && neroAacEnc -cbr 499000 -if RecordingMYvoice.wav -of RecordingMYvoice.m4a  && rm RecordingMYvoice.wav 
```


it seems to go as high as 516k but many will need a lower bitrate



ps    once you have the neroAacEnc in your home folder make sure to do this first

go  1. ```
sudo cp neroAacEnc /usr/bin
```
    2. ```
cd /usr/bin
```
    3. ```
sudo chmod +x neroAacEnc 
```



This should provide one with the highest possible m4a/aac file (alledgedly)

---

### Post by FakeOutdoorsman on 2011-03-10
You can also pipe to neroAacEnc to avoid the intermediate file:
```
ffmpeg -i input -f wav - | neroAacEnc -ignorelength -if - -of output.mp4
```

---

### Post by ron999 on 2011-03-10
Such a pity we don't have a command like this:-
```
ffmpeg -i input -acodec libnero output.mp4
```

:D

---

### Post by shantiq on 2011-03-16
also a few pointers to use [SoX]("http://ubuntuforums.org/showpost.php?p=10565567&postcount=2") to record your voice instead of ffmpeg

---

### Post by seess on 2011-03-16
> **shantiq said:**
> ok so a better quality aac/m4a   goes like this   i have set the quality really high  499    take it down to the level you want maybe 150 or 100 to suit your needs 






```
ffmpeg -f alsa -ac 2 -i pulse -acodec libfaac  -aq 499  -y ./Desktop/RecordingMYvoice.aac
```
Aac/m4a   makes sense to be used for a voice recording; there is much literature all over the net to say that for the same size it is always higher sound[r4](http://www.r4-buy.co.uk) quality than mp3


and in any case there is no way i can see to record your voice to mp3 directly here with ffmpeg.  Aac is universal and probably a better choice anyway.
I like your idea very much. I hope I can help you, but I am sorry...

---

### Post by shantiq on 2011-03-16
no worries seesss      Ron999 had already helped with that one


[URL="http://ubuntuforums.org/showpost.php?p=9915277&postcount=10"]the answer is here for mp3
[/URL]

---

