---
title: "ffmpeg screen capture"
date: 2012-10-05
forum: Multimedia Software
---

### Post by 3dmatrix on 2012-10-05
I am using the following command to capture video being played in my browser.

**ffmpeg -f x11grab -s 768x576 -r 30 -i :0.0+300,150 ~/output.mpg -ab 64k**

I can capture the video but there are two problems
* Video quality is too poor how can i improve it ?
* Sound is not being recorded, perhaps i have not mentioned the sound capture device. But i do not have much idea abt it.

Can any one plz help me with this ?

.

---

### Post by Bucky Ball on 2012-10-05
*Thread moved to **Multimedia & Video***

---

### Post by 3dmatrix on 2012-10-05
Any solution ?

---

### Post by FakeOutdoorsman on 2012-10-05
See [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

---

### Post by 3dmatrix on 2012-10-05
> **FakeOutdoorsman said:**
> See [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

Thats a wonderful thread ! Things are mentioned in great details. But when i use the following code :

**ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 618x474 -i :0.0+450,134 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv**

I get the following error :

[B][matroska @ 0x8309ba0] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1 >= 1
av_interleaved_write_frame(): Invalid argument[/B]

With this command :

**ffmpeg -f alsa -i hw:0,0 -f x11grab -r 30 -s 1024x768 -i :0.0 -vcodec libx264 -preset ultrafast -crf 0 -an -y output.mkv -acodec pcm_s16le -y output.wav**

I get this error :
[B]
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
[alsa @ 0x87f6240] Estimating duration from bitrate, this may be inaccurate
Input #0, alsa, from 'hw:0,0':
  Duration: N/A, start: 35358.999152, bitrate: N/A
    Stream #0.0: Audio: pcm_s16le, 48000 Hz, 2 channels, s16, 1536 kb/s
[x11grab @ 0x8806740] device: :0.0 -> display: :0.0 x: 0 y: 0 width: 1024 height: 768
[x11grab @ 0x8806740] shared memory extension  found
[x11grab @ 0x8806740] Estimating duration from bitrate, this may be inaccurate
Input #1, x11grab, from ':0.0':
  Duration: N/A, start: 1349473809.635993, bitrate: 754974 kb/s
    Stream #1.0: Video: rawvideo, bgra, 1024x768, 754974 kb/s, 30 tbr, 1000k tbn, 30 tbc
Output #1, wav, to 'output.wav':
Output file #1 does not contain any stream[/B]

Moreover if i only use ffmpeg -f alsa -i hw:0,0 -acodec pcm_s16le -y output.wav command it captures sound from the ic and not the application / speaker sound. How do i change over to it ?

As mentioned earlier i can always record the video by ffmpeg -f x11grab -s 768x576 -r 30 -i :0.0+300,150 ~/output.mpg command.

Can you kindly tell me what is going wrong ? 

This command is working 
**ffmpeg -f alsa -i hw:0,0 -acodec pcm_s16le -f x11grab -s 320x240 -r 30 -i :0.0 ~/out3.mpg**
but the video quality is too poor (i would like to record a lossless video) and the sound is being captured from the mic and not from the speaker / application. And with this command **ffmpeg -f alsa -i hw:0,0 -acodec pcm_s16le -f x11grab -r 30 -s  618x474 -i :0.0+350,134 ~/out4.m4v** the video quality is good, but the sound is not sync with the video and again the sound is captured from the mic.

.

---

### Post by FakeOutdoorsman on 2012-10-05
> **3dmatrix said:**
> Thats a wonderful thread ! Things are mentioned in great details. But when i use the following code :

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 618x474 -i :0.0+450,134 -acodec pcm_s16le -vcodec libx264 -preset ultrafast -crf 0 -threads 0 output.mkv
```

I get the following error :

```
[matroska @ 0x8309ba0] Application provided invalid, non monotonically increasing dts to muxer in stream 1: 1 >= 1
av_interleaved_write_frame(): Invalid argument
```

The guide was written for FFmpeg. Ubuntu no longer uses FFmpeg, but supplies a "fake" ffmpeg package from a fork called libav. It may work as expected with the real ffmpeg (it works for me). You can either compile it as shown here: [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide), or perhaps use [Jon Severinsson's FFmpeg PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg). I recommend compiling since the PPA will not provide the latest FFmpeg code.

> **3dmatrix said:**
> Moreover if i only use ffmpeg -f alsa -i hw:0,0 -acodec pcm_s16le -y output.wav command it captures sound from the ic and not the application / speaker sound. How do i change over to it ?

See [Capturing audio with FFmpeg and ALSA](https://ffmpeg.org/trac/ffmpeg/wiki/Capturing%20audio%20with%20FFmpeg%20and%20ALSA), or if you use pulse instead of alsa see the FAQ in the screencast guide.

---

### Post by 3dmatrix on 2012-10-06
> **FakeOutdoorsman said:**
> Ubuntu no longer uses FFmpeg, but supplies a "fake" ffmpeg package from a fork called libav. It may work as expected with the real ffmpeg (it works for me). [/url]

I think it works for me too because i could capture the video, just that i am not too sure abt how to control various parameters and how to capture from the speaker.

> **FakeOutdoorsman said:**
> If you use pulse instead of alsa see the FAQ in the screencast guide.

Sorry for my ignorance :) how do i check which one i am using !
My sound settings just says :  _Built in Audio Analogue Stereo_

Code : **arecord -l**
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Code : **arecord -L**
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC269VB Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Front speakers . . . . . . . . . .  Displays a big long list of device :)

So not sure what i need to type for my speakers !


.

---

### Post by 3dmatrix on 2012-10-26
As usual when i use the code :

ffmpeg -f alsa -i hw:0,0 -acodec pcm_s16le -f x11grab -r 30 -s  720x474 -i :0.0+380,134 ~/out5.m4v

I capture the screen video but capture the sound from the speakers.

As i could not get any proper solution here, i tried to capture the screen video with the speaker sound. Then split and delete that sound. Next i recorded the sound of that video by running it the second time and recording the sound by sound recorder application. Initially it was recording the sound from the speaker but when i changed the System Settings > Sound to Analog Stereo Output instead of Analog Stereo Duplex, the recorder could record sound directly from the sound card. And then finally i had to join the video and this new sound to get my final video. But some times it is not possible to run the video or record the screen activity 2 times. Even after making that change in the settings i could not use the above code to record the desired video with the sound from the sound card.

What changes should i do in the above code to be able to do that ?

---

### Post by danielbauwens on 2012-10-26
I would actually suggest using recordmydesktop.
It records in full HD and there are lots of tutorials on the internet too.
The interface is simple, but easy.

Ps: in case in need of a proffesional video editor. I would suggest Cinelerra.

---

### Post by 3dmatrix on 2012-10-26
> **danielbauwens said:**
> I would actually suggest using recordmydesktop.
It records in full HD and there are lots of tutorials on the internet too.
The interface is simple, but easy.

Ps: in case in need of a proffesional video editor. I would suggest Cinelerra.

I tried that application many times, but some how it does not works on my system. When i try to record the desktop there is a black border showing the desktop area that is being recorded and after that nothing happens. Neither, the video gets recorded nor am i able to stop it. If some how i kill the application, still i have that black border till i restart the system.

---

