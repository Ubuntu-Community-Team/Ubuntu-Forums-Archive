---
title: "ima4 converter"
date: 2012-12-04
forum: Multimedia Software
---

### Post by unrealdude24 on 2012-12-04
I'm looking for a converter that can convert .CAF audio files encoded with ima4 to mp3 or even just software capable of playing ima4 on Ubuntu.

Thanks for your help in advance.

---

### Post by ron999 on 2012-12-04
Please provide a sample file.

---

### Post by FakeOutdoorsman on 2012-12-04
What does ffmpeg say about it?
```
ffmpeg -i input.caf
```

---

### Post by andrew.46 on 2012-12-04
Hmmm..... ima/adpcm is reasonably well supported in MPlayer but indeed a sample would be nice just to check this particular file.

---

### Post by unrealdude24 on 2012-12-05
Here's a sample file: 
[https://docs.google.com/file/d/0By3sO1Ekj2YVeVlITjNhbmZSUDg/edit](https://docs.google.com/file/d/0By3sO1Ekj2YVeVlITjNhbmZSUDg/edit)

The output after running ffmpeg -i:
```
ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:50:25 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[caf @ 0x8d5e240] Estimating duration from bitrate, this may be inaccurate
Input #0, caf, from 'last elec lecture.CAF':
  Duration: 01:19:06.20, start: 0.000000, bitrate: 68 kb/s
    Stream #0.0: Audio: adpcm_ima_qt, 16000 Hz, 1 channels, s16, 64 kb/s
At least one output file must be specified

```

---

### Post by shantiq on 2012-12-05
```
ffplay *.CAF
```   plays it as is  [ once placed in your home folder ]



> ffmpeg -i lecture.CAF -ab 64k  lecture.mp3   converts it to mp3 with same bitrate

---

### Post by unrealdude24 on 2012-12-05
That worked perfectly. It's odd that this file wouldn't open without converting first as rythmbox or mplayer refused to play it. Not even VLC or codec packs on my windows machine would play it.

Thanks a lot, I appreciate it!

Edit: Noticed a bug with ffplay (without converting), seeking results in a whole bunch of errors and distorted audio. The console outputs the following when clicking anywhere in the window:
> [adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 92
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 98=    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 108
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 112    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 91=    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 97=    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 91=    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 94=    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 107    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 115
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 90=    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 100    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 114    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 123
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 97=    0B f=0/0   
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 113
[adpcm_ima_qt @ 0xaff01980] ERROR: step_index = 96
...


---

### Post by shantiq on 2012-12-05
> =Noticed a bug with ffplay (without converting), seeking results in a whole bunch of errors and distorted audio. The console outputs the following when clicking anywhere in the window:


probably version of ffmpeg  


i use  

> ffplay *.CAF
[B]ffplay version N-35917-ge4fe4d0 Copyright (c) 2003-2012 the FFmpeg developers
  built on Sep 10 2012 11:04:03 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)[/B]
  configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3 --enable-libaacplus
  
[caf @ 0x7f662c0008c0] Estimating duration from bitrate, this may be inaccurate
Input #0, caf, from 'last elec lecture.CAF':
  Duration: 01:19:06.20, start: 0.000000, bitrate: 68 kb/s
    Stream #0:0: Audio: adpcm_ima_qt (ima4 / 0x34616D69), 16000 Hz, 1 channels, s16, 64 kb/s
^Z22.51 A-V:  0.000 fd=   0 aq=    0KB vq=    0KB sq=    0B f=0/0


which i installed with FakeOutdoorsman's excellent guide [**here**]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide")  if you have the time and/ or inclination  Really good it is

But as you saw the CAF converts very fast anyway ...

---

### Post by andrew.46 on 2012-12-05
> **unrealdude24 said:**
>  It's odd that this file wouldn't open without converting first as rythmbox or mplayer refused to play it. 

You might need to update your copy of MPlayer as well as the most recent version of MPlayer plays your sample file flawlessly:

```

andrew@skamandros~/media/Sorting$ mplayer last\ elec\ lecture.CAF 
MPlayer SVN-r35434-4.7.1 (C) 2000-2012 MPlayer Team

Playing last elec lecture.CAF.
libavformat version 54.37.100 (internal)
libavformat file format detected.
[caf @ 0xf119a0]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: audio (adpcm_ima_qt), -aid 0
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
libavcodec version 54.74.100 (internal)
AUDIO: 16000 Hz, 1 ch, s16le, 68.0 kbit/26.56% (ratio: 8500->32000)
**[COLOR="Red"]Selected audio codec: [ffadpcmimaqt] afm: ffmpeg (FFmpeg QT IMA ADPCM audio)[/COLOR]**
==========================================================================
AO: [oss] 16000Hz 1ch s16le (2 bytes per sample)
Video: no video
  =====  PAUSE  =====
A: 268.6 (04:28.6) of 4746.2 ( 1:19:06.2)  0.1% 

```

although I could not sit through that entire lecture :)

---

### Post by shantiq on 2012-12-05
ok Andrew where do i find a guide for this? I know you concocted one but where is it please? i shall try it too:KS
[**ha ok found it?**]("http://www.andrews-corner.org/mplayer.html") and thank you.

---

### Post by ron999 on 2012-12-05
> **unrealdude24 said:**
> That worked perfectly.
Hi
If there are more of these long files to convert to mp3...
The job can be speeded up using **gogo-no-coda**. :cool:
```
sudo apt-get install gogo
```
Then
```
ffmpeg -i "last elec lecture.CAF" -f wav - | gogo -b 64 -nopsy -q 9 -m m -d 44.1 stdin lecture.mp3
```

---

### Post by ron999 on 2012-12-05
Hi
Looks like **gogo** in repository might be broken.:(
deb file is attached.
Unzip it then 
```
sudo dpkg -i "gogo_3.13-1.deb"
```

---

