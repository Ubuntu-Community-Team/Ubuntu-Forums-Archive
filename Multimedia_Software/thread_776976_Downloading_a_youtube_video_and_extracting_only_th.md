---
title: "Downloading a youtube video and extracting only the audio"
date: 2008-05-01
forum: Multimedia Software
---

### Post by go_beep_yourself on 2008-05-01
I succesfully downloaded a youtube video in .flv
 format after lots of googling. However following
 directions to extract the audio has not worked
 for me with no obvious reasons to me why. I checked
 the video I download with VLC. It does have
 audio.

Here's what I've tried to extract the audio. On
 other places on the net, I saw the same two
 commands working for others. Here's the video.

[http://www.youtube.com/watch?v=Ejb8QOyjz-E&](http://www.youtube.com/watch?v=Ejb8QOyjz-E&)

In order to get the video.flv, I did some tricky
 stuff with wget I found from google that worked!
 I just wished extracting the audio was as easy.
 Here's how I did it.

[http://www.go2linux.org/wget-to-download-youtube-videos](http://www.go2linux.org/wget-to-download-youtube-videos)

Attempt #1


```
$ mplayer -dumpaudio video.flv 
 MPlayer 1.0rc2-4.1.2 (C) 2000-2007 MPlayer Team
 CPU: AMD Athlon(tm) 64 X2 Dual Core Processor
 3800+ (Family: 15, Model: 43, Stepping: 1)
 CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1
 SSE: 1 SSE2: 1
 Compiled with runtime CPU detection.
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be
 able to use your remote control.
 
 Playing video.flv.
 libavformat file format detected.
 [lavf] Video stream found, -vid 0
 [lavf] Audio stream found, -aid 1
 VIDEO:  [FLV1]  320x240  0bpp  25.000 fps    0.0
 kbps ( 0.0 kbyte/s)
 Core dumped ;)
 
 Exiting... (End of file)
$
```

Attempt #2


```
# ffmpeg -i video.flv -f mp3 -vn -acodec copy carsounds2.mp3 
FFmpeg version SVN-r10703, Copyright (c)
 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr
 --incdir=/usr/include/ffmpeg --libdir=/usr/lib64
 --shlibdir=/usr/lib64 --mandir=/usr/share/man --arch=x86_64
 --extra-cflags=-O2 -g -pipe -Wall
 -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector
 --param=ssp-buffer-size=4 -m64 -mtune=generic --enable-liba52
 --enable-libfaac --enable-libfaad --enable-libgsm
 --enable-libmp3lame --enable-libogg
 --enable-libtheora --enable-libvorbis --enable-libxvid
 --enable-libx264 --enable-pp --enable-pthreads
 --disable-static --enable-shared --enable-gpl
 --disable-debug --disable-opts --disable-strip
  libavutil version: 49.5.0
  libavcodec version: 51.45.0
  libavformat version: 51.14.0
  built on Oct 18 2007 03:18:27, gcc: 4.1.2
 20070925 (Red Hat 4.1.2-31)

Seems stream 0 codec frame rate differs from
 container frame rate: 1000.00 (1000/1) -> 25.00
 (25/1)
Input #0, flv, from 'video.flv':
  Duration: 00:09:58.7, start: 0.000000, bitrate:
 56 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x240,
 25.00 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 56
 kb/s
Output #0, mp3, to 'carsounds2.mp3':
  Stream #0.0: Audio: libmp3lame, 22050 Hz, mono,
 56 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=    4188kB time=598.8 bitrate=  57.3kbits/s
    
video:0kB audio:4188kB global headers:0kB muxing
 overhead 0.000746%
#
```

HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Thank you.

---

### Post by hyperair on 2008-05-01
> **go_beep_yourself said:**
> 
In order to get the video.flv, I did some tricky
 stuff with wget I found from google that worked!
 I just wished extracting the audio was as easy.
 Here's how I did it.

Tricky wget stuff? You obviously don't make full use of the APT repository. "apt-cache search youtube" or searching for it in Synaptic yields a program called "youtube-dl". Upon installing, you can grab any Youtube video by this command: "youtube-dl <url>". Simple.

> **go_beep_yourself said:**
> 
Attempt #1


```
$ mplayer -dumpaudio video.flv 
 MPlayer 1.0rc2-4.1.2 (C) 2000-2007 MPlayer Team
 CPU: AMD Athlon(tm) 64 X2 Dual Core Processor
 3800+ (Family: 15, Model: 43, Stepping: 1)
 CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1
 SSE: 1 SSE2: 1
 Compiled with runtime CPU detection.
 mplayer: could not connect to socket
 mplayer: No such file or directory
 Failed to open LIRC support. You will not be
 able to use your remote control.
 
 Playing video.flv.
 libavformat file format detected.
 [lavf] Video stream found, -vid 0
 [lavf] Audio stream found, -aid 1
 VIDEO:  [FLV1]  320x240  0bpp  25.000 fps    0.0
 kbps ( 0.0 kbyte/s)
 Core dumped ;)
 
 Exiting... (End of file)
$
```

Attempt #2


```
# ffmpeg -i video.flv -f mp3 -vn -acodec copy carsounds2.mp3 
FFmpeg version SVN-r10703, Copyright (c)
 2000-2007 Fabrice Bellard, et al.
  configuration: --prefix=/usr
 --incdir=/usr/include/ffmpeg --libdir=/usr/lib64
 --shlibdir=/usr/lib64 --mandir=/usr/share/man --arch=x86_64
 --extra-cflags=-O2 -g -pipe -Wall
 -Wp,-D_FORTIFY_SOURCE=2 -fexceptions -fstack-protector
 --param=ssp-buffer-size=4 -m64 -mtune=generic --enable-liba52
 --enable-libfaac --enable-libfaad --enable-libgsm
 --enable-libmp3lame --enable-libogg
 --enable-libtheora --enable-libvorbis --enable-libxvid
 --enable-libx264 --enable-pp --enable-pthreads
 --disable-static --enable-shared --enable-gpl
 --disable-debug --disable-opts --disable-strip
  libavutil version: 49.5.0
  libavcodec version: 51.45.0
  libavformat version: 51.14.0
  built on Oct 18 2007 03:18:27, gcc: 4.1.2
 20070925 (Red Hat 4.1.2-31)

Seems stream 0 codec frame rate differs from
 container frame rate: 1000.00 (1000/1) -> 25.00
 (25/1)
Input #0, flv, from 'video.flv':
  Duration: 00:09:58.7, start: 0.000000, bitrate:
 56 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x240,
 25.00 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 56
 kb/s
Output #0, mp3, to 'carsounds2.mp3':
  Stream #0.0: Audio: libmp3lame, 22050 Hz, mono,
 56 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=    4188kB time=598.8 bitrate=  57.3kbits/s
    
video:0kB audio:4188kB global headers:0kB muxing
 overhead 0.000746%
#
```

HELP!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Thank you.

Both commands look like they have succeeded to me. Have you tried looking in the directory for the mp3s? The second attempt should yield "carsounds2.mp3", and the first should yield output.mp3 or something of that sort.

---

### Post by vishzilla on 2008-05-01
Or you can use [http://flvto.com/](http://flvto.com/)
[http://catchvideo.net/](http://catchvideo.net/)
[http://vidtomp3.com/](http://vidtomp3.com/)

---

### Post by gabkdlly on 2008-05-10
I think this is the command you are looking for:
```
mplayer -ao pcm:waveheader -vc dummy -vo null video.flv
```
This will generate a file called audiodump.wav

---

### Post by hyperair on 2008-05-10
> **gabkdlly said:**
> I think this is the command you are looking for:
```
mplayer -ao pcm:waveheader -vc dummy -vo null video.flv
```
This will generate a file called audiodump.wav

That creates a wave file of the audio from the video, in other words decoding the audio from . The commands go_beep_yourself used extracts the audio data without decoding it from the original encoded format found in the video. 

I've also posted that the commands he used have actually succeeded, but he didn't look for the file. 

Please read the thread before posting next time, or you may waste your and other people's time by posting something that is redundant and/or wrong.

---

### Post by go_beep_yourself on 2008-05-10
I did find a solution that works when all others failed. Avidemux did the trick. First I opened the file in Avidemux. Second I went to an audio or sound menu and saved the audio only. I don't know exactly because I'm trying to translate between Spanish and English now. English is my first language and Spanish is what I'm trying to learn, so I am using Stardict with converted Babylon dictionaries and changed my computer's language to Spanish. It shouldn't be too difficult to figure it out. Avidemux does work. For anyone who would like to check it out, here is the url to my home linux server where you may stream the audio.

[PHP]http://l33t0rb4it.homelinux.com/~chris/music/ultimate_car_sounds_2.mp3[/PHP]

---

### Post by richandcreamy on 2008-05-29
I don't see the audio only option!

---

### Post by go_beep_yourself on 2008-05-30
> **richandcreamy said:**
> I don't see the audio only option!

Anyone else see it? I know there's a way to do it with Avidemux. Also be sure that you are up to date. To tell you the truth, I probably have later software versions than you because I was using Fedora 8 64-bit Raid level 1 :guitar: at the time. Since upgrading to Fedora 9 with all the same setup mentioned earlier, I do not have Avidemux now and rarely if ever would need to use it. So anyone else see it with Avidemux? Check your version.

---

### Post by LucidLoon on 2009-01-24
I use Avidemux(GTK+) for this. It's in Synaptic package manager for Ibex. I just open the file I want to take the sound from, go to the top menu bar and select "Audio". Click "save" on the drop down menu. Select the folder I want to save to and give the file a title with an .mp3 extension. Click on the "Save" button and I'm done. 30 seconds and I don't have to pull my hair out trying to figure out why ffmpeg -i didn't work again.

---

