---
title: "[SOLVED] winff mp4 to mpeg"
date: 2008-06-08
forum: Multimedia Software
---

### Post by ben@layer on 2008-06-08
winff is not encoding. I am trying to get a movie to play on rockbox.org(the coolst thing for mp3 player and ipods) e200
and this is my error code that I get 

Unsupported codec for output stream #0.1 
output for #0.1 
stream #0.1:audio: 0x0000, 44100 hz, stereo, 0 kb/s
please help :(

ps: sorry for my spelling :(

---

### Post by gandaran on 2008-06-09
did you install **ffmpeg** from the normal synaptic repository's or from the medibuntu repository?
medibuntu's ffmpeg has more codecs, this is the package recommended for winff.

---

### Post by ben@layer on 2008-06-09
now it's input stream #0.1

input
stream #0.0: video: mpeg4, yuv420p, 320240, 30.00 fps(r)
stream #0.1: audio: *** 


the error I get is

[acc Q 0xb7acc9a8]FAAD library; cannot resolve faacdecgeterrormesseage in libfaad.so.o! 
error while opening codec for input stream #0.1:confused:

I reinstalled faad and faac and it still didn't work please help me
thinks

---

### Post by FakeOutdoorsman on 2008-06-09
You are doing nothing wrong.  Your error message is related to this bug:
[Bug #225060: ffmpeg doesn't work with hardy FAAD library]("https://bugs.launchpad.net/medibuntu/+bug/225060")

You can use the old Gutsy Gibbon faad as described in the first comment of the bug report.  Another solution is to compile ffmpeg yourself:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by ben@layer on 2008-06-09
NEW ERROR Unknown  encoder mp3
please please HELP!!!

??is Ubuntu 8.04 still in beta or what??
 

and a big thinks to all

---

### Post by FakeOutdoorsman on 2008-06-09
> **ben@layer said:**
> NEW ERROR Unknown  encoder mp3
please please HELP!!!

??is Ubuntu 8.04 still in beta or what??
 

and a big thinks to all

Patent and copyright restrictions keep Ubuntu from enabling some formats and codecs by default.  They leave it up to the user and is one of the ways to keep Ubuntu free.  Providing only free software "out of the box" is an important part of the [Ubuntu Philosophy]("http://www.ubuntu.com/community/ubuntustory/philosophy"), but unfortunately can cause some problems for users.

How did you install ffmpeg?  From the ubuntu repository, Medibuntu repository, or did you compile it yourself?  Can you show me your ffmpeg command and the complete ffmpeg output?  This will give me the details I need to help you debug this.  I don't use winff, but if you run it from the terminal it might show the ffmpeg output.

---

### Post by ben@layer on 2008-06-09
this is what I used for in the console its a script some one made to make mpg for rockbox 

the code is :ben@ben-desktop:~$ '/home/ben/Desktop/mkvid-ffmpeg.sh' '/home/ben/Desktop/300' /home/ben/300mpeg

Configuration for /home/ben/Desktop/300

Screen width (default 220): 
Screen height (default 176): 
screenwidth=220 screenheight=176
Output aspect ratio (5:4 is full screen):
1) 4:3
2) 5:4
3) 16:9
4) 221:100
5) other
#? 3
width=220 height=124
Crop top/bottom by amount (in pixels) (default 0): 
Crop left/right by amount (in pixels) (default 0): 
crop top/bottom= left/right=
Output frame rate (25):
1) 24
2) 25
3) 29.97
4) 30
5) other
#? 3
framerate=29.97
Output video bitrate (256): 
videobr=256
Output audio bitrate (64): 
audiobr=64
FFmpeg version SVN-r13737, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-libvorbis --enable-libtheora --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-pthreads --enable-libx264
  libavutil version: 49.7.0
  libavcodec version: 51.57.2
  libavformat version: 52.16.0
  libavdevice version: 52.0.0
  built on Jun  9 2008 20:38:00, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/ben/Desktop/300':
  Duration: 01:56:24.00, start: 0.000000, bitrate: 1001 kb/s
    Stream #0.0(eng): Video: mpeg4, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 30.00 tb(r)
    Stream #0.1(eng): Audio: libfaad, 44100 Hz, stereo
Unknown encoder 'mp3'

---

### Post by FakeOutdoorsman on 2008-06-09
The names of encoding options in ffmpeg often annoyingly change between revisions, so your script needed to be updated.  I renamed "-acodec mp3" to "-acodec libmp3lame" on line 180, but I didn't test the script.

---

### Post by ben@layer on 2008-06-09
THANKS THANKS THANKS AND NICE TUT ON BUILDING FFMPEG FROM SORCE THANKS THANKS THANKS
it running now I hope with 0 errors
thank you
I,ll this enfo to rockbox forums in put you name ALL over it

---

### Post by ben@layer on 2008-06-10
videos done encoding good video NO sound what so aver

---

### Post by FakeOutdoorsman on 2008-06-10
I should have tested the script first.  I got it working here after I removed "-f mpeg2video" from line 180.  It was preventing the audio from being added to the file.  It worked for me with this command:
```
./mkvid-ffmpeg.sh pasteeater.avi pasteeater.mpg
```
I recommend passing the "-vframes" option to the script to test it.  vframes tells ffmpeg to encode only a certain number of frames.  This is useful because you can test the script without needing to encode your whole video. In this example, only the first 30 frames will be encoded:
```
./mkvid-ffmpeg.sh -o "-vframes 30" pasteeater.avi pasteeater.mpg
```

---

### Post by ben@layer on 2008-06-10
It works good video good sound and even better on my mp3 play
now I can put movies on my mp3 with out using my moms computer(M$ vista)
THANKS!

---

### Post by ben@layer on 2008-06-10
is it save to do two at a time in a another console

---

### Post by FakeOutdoorsman on 2008-06-10
Glad you got it working despite a few bugs, lack of restricted codec support in ffmpeg, and script errors.  I recommend encoding just one video at a time because it should use most of your CPU power to encode just one.

---

### Post by cesaregb on 2008-08-12
Hi all i dont know why but I have probles with this program i get this error 

Seems stream 0 codec frame rate differs from container frame rate: 29.97 (30000/1001) -> 59.94 (60000/1001)
Input #0, mpeg, from '/media/disk/Documents and Settings/cesar/Desktop/lost/VTS_04_1.VOB':
  Duration: 00:41:46.3, start: 0.280633, bitrate: 3427 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480, 9800 kb/s, 59.94 fps(r)
  Stream #0.1[0x80]: Audio: 0x0000, 48000 Hz, 5 channels, 384 kb/s
  Stream #0.2[0x81]: Audio: 0x0000, 48000 Hz, stereo, 192 kb/s
  Stream #0.3[0x82]: Audio: 0x0000, 48000 Hz, stereo, 192 kb/s
  Stream #0.4[0x20]: Subtitle: dvdsub
  Stream #0.5[0x21]: Subtitle: dvdsub
  Stream #0.6[0x22]: Subtitle: dvdsub
  Stream #0.7[0x23]: Subtitle: dvdsub
  Stream #0.8[0x24]: Subtitle: dvdsub
  Stream #0.9[0x25]: Subtitle: dvdsub
  Stream #0.10[0x26]: Subtitle: dvdsub
  Stream #0.11[0x27]: Subtitle: dvdsub
Unknown codec 'xvid'

could anyone help me i already install the ffmpeg_0.cvs20070307-5ubuntu7.1+medibuntu1_i386.deb 

and the w32codecs_20071007-0medibuntu3_i386.deb files 
im on ubuntu 8 this has something wrong please help me ..  

is there anything else that i can do, i install this same program in the same machine with windows so dont know what a.... can be

---

### Post by FakeOutdoorsman on 2008-08-13
This thread has already been marked as solved, so people might not see your question.

Are you using WinFF or plain ffmpeg?  Paste the output from this command:
```
ffmpeg -version
```

If you are using WinFF, which preset are you using?  Are you using the latest WinFF and the latest Ubuntu?

---

### Post by vikhr on 2010-02-08
Unknown codec ['xvid' or 'libmp3lame'..etc..etc.] error
is coz you need libavcodec-unstripped-52 and libavcodec-extra-52 to make
winff work..these packages are not installed a dependencies..may be for legal reasons..so to get over it..
**sudo apt-get install libavcodec-unstripped-52 libavcodec-extra-52**
Hope this settles it! happy hacking..

---

### Post by kim062 on 2010-02-08
hello i need help for my gyache why i cant log in to my other yahoo id..pls help me...[-o<i really need some help..huhuhuh

---

