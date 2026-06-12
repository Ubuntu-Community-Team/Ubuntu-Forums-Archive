---
title: "How to convert video for Blackberry Storm"
date: 2009-03-11
forum: Multimedia Software
---

### Post by rmannon on 2009-03-11
This script will convert video for Blackberry Storm. This is the first script I have ever submitted. It's kind of a sloppy as I hacked a couple others together, so people may have questions.  This is for Ubuntu 9.04 but should also work on 8.10 with the proper codecs installed.  


the script: 

#!/bin/bash
mkdir convert
ls -1 |
while read FILENAME; do
    ffmpeg -i "${FILENAME}" -vcodec mpeg4 -vtag XVID -s 480x360 -qscale 10 -ab 48k -ar 22050 -ac 1 -acodec libmp3lame "./convert/${FILENAME}.mp4" &
done


Save it as blackberry.sh

I assume it will work for any newer Blackberry as long as you change this "480x360" to whatever screen size your Blackberry supports.  

You will need the medibuntu source so:

$ sudo echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free"  >> /etc/apt/sources.list

and:

$ sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

Change "jaunty" to "intrepid" in the first command if needed. 

$ sudo apt-get install libavcodec-unstripped-52 ffmpeg lame

if you are using intrepid:

$ sudo apt-get install libavcodec-unstripped-51 ffmpeg lame


That should do it, any questions please ask. I do this on 64bit but I don't see why it would not work on 32bit.  

To run the script put it in the folder with the files you want converted and locate that folder from the command line.  

Then: 

$ sh blackberry.sh

A word to the wise, this converts all the files at the exact same time. If you have 20 video files in the folder it's going to convert them all simultaneously.  I would love to make this a right click nautilus script that converts each file individually but I do not know how.   

peas & carrots
-rmannon

---

### Post by andrew.46 on 2009-03-12
Hi,

I should say up front that I don't own such a fancy phone :-). But I was wondering at your choice of libxvid instead of FFmpeg's native mpeg4? Certainly on the devices I have used that require xvid encoding this seems to create a better video.

Could you try on your Blackberry? Instead of:

```
-vcodec libxvid
```

simply try:

```
-vcodec mpeg4 -vtag XVID
```

Sorry I can't test this myself, my own phone is apparently 'a brick' my teenager tells me :-).

Andrew

---

### Post by rmannon on 2009-03-12
Hey Andrew

Thats a good question.  The reason I use libxvid is because FFmpeg's native mpeg4 would make the videos but would not play them on my Storm.  But that was under 8.10.  I will try the change tonight when I get home to see if it works under 9.04. If it does I'll update the script.

-ryan

---

### Post by andrew.46 on 2009-03-12
Hi rmannon,

> **rmannon said:**
> Thats a good question.  The reason I use libxvid is because FFmpeg's native mpeg4 would make the videos but would not play them on my Storm.  But that was under 8.10.  I will try the change tonight when I get home to see if it works under 9.04. If it does I'll update the script.

With any luck the '-vtag XVID' option might make it work. This has worked with a few handheld players I have used. The reason being that the native FFmpeg mpeg4 encoder announces itself via fourcc as 'FMP4' which some hardware chokes on while simply changing this fourcc to 'XVID' via -vtag allows playback. Hopefully on the Blackberry as well :-).

Andrew

---

### Post by rmannon on 2009-03-12
Hi Andrew,

Your suggestion works great.  I have updated the script.  It seems to convert a bit faster too. Thanks for your help.

---

### Post by FakeOutdoorsman on 2009-03-13
I recommend dumping Medibuntu because it doesn't offer anything that you need to successfully run your FFmpeg command.  Also, libavcodec-unstripped-5* should provide mp3 encoding within FFmpeg, so you don't need to explicitly install lame.

On a visual note, it would be nice to wrap your commands in the "code" tags to make it easier to differentiate text and commands.

---

### Post by rmannon on 2009-03-13
I was unable to get this to work until I added the medibuntu source.  Maybe when I installed libavcodec-unstripped-52 it added something.  I had to use lame because "-acodec mp3" did not work.  If you know why I would love to know.

---

### Post by FakeOutdoorsman on 2009-03-13
> **rmannon said:**
> I was unable to get this to work until I added the medibuntu source.  Maybe when I installed libavcodec-unstripped-52 it added something.  I had to use lame because "-acodec mp3" did not work.  If you know why I would love to know.
libavcodec-unstripped-52 will provide the restricted encoders that FFmpeg needs.  The option "-acodec mp3" has been obsolete for some time and has been replaced with "-acodec libmp3lame".

---

### Post by Mr_bleu on 2009-03-14
I'll let you know how this turns out.  It's converting files now.  Hope this works.


#!/bin/bash
mkdir convert
ls -1 |
while read FILENAME; do
ffmpeg -i "${FILENAME}" -vcodec mpeg4 -vtag XVID -s 320x240 -qscale 10 -ab 48k -ar 22050 -ac 1 -acodec libmp3lame "./convert/${FILENAME}.mp4" &
done

---

### Post by Mr_bleu on 2009-03-15
Sound doesn't work on the converted video.  Video plays though!!

---

### Post by ububuL on 2009-03-15
I was able to convert an avi file to mp4 on Hardy 64 bit and mplayer played the mp4 file perfectly fine but when I played it on my Storm, there is no video but sound. 


```
ffmpeg -i video.avi -vcodec mpeg4 -vtag XVID -s 480x360 -qscale 10 -ab 48k -ar 22050 -ac 1 -acodec mp3 video.mp4

```


Any idea? ;)

Thanks.

---

### Post by andrew.46 on 2009-03-15
Hi Mr_bleu,

> **Mr_bleu said:**
> Sound doesn't work on the converted video.  Video plays though!!

Is your copy of FFmpeg setup to encode to mp3? Best way to tell is:

```

andrew@skamandros~$ **[COLOR="Red"]ffmpeg -formats | grep lame[/COLOR]**
FFmpeg version SVN-r17954, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --mandir=/usr/man --disable-debug 
--enable-shared --disable-static --enable-postproc --enable-avfilter 
--enable-pthreads --enable-libtheora --enable-libvorbis --enable-x11grab 
**[COLOR="Red"]--enable-libmp3lame[/COLOR]** --enable-libx264 
--enable-libschroedinger --enable-libfaac --enable-libfaad 
--enable-libamr-wb --enable-libamr-nb --enable-libgsm --enable-nonfree
 --enable-gpl
  libavutil     50. 0. 0 / 50. 0. 0
  libavcodec    52.21. 0 / 52.21. 0
  libavformat   52.31. 1 / 52.31. 1
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 14 2009 12:48:26, gcc: 4.2.4
**[COLOR="Red"]  EA    libmp3lame      libmp3lame MP3 (MPEG audio layer 3)[/COLOR]**


```

Andrew

---

### Post by rmannon on 2009-03-16
I bet it is FFmpeg as well.  I think that is where the unstripped package comes in.

$ sudo apt-get install libavcodec-unstripped-5*

---

### Post by Mr_bleu on 2009-03-16
djr@popeye-laptop:~$ ffmpeg -formats | grep lame
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
  EA    libmp3lame



djr@popeye-laptop:~$ sudo apt-get install libavcodec-unstripped-51
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libavcodec-unstripped-51 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
djr@popeye-laptop:~$

---

### Post by rmannon on 2009-03-17
I don't see --enable-libmp3lame after your $ ffmpeg -formats | grep lame

I don't think libavcodec-unstripped-51 is going to work with Hardy.  I think unstripped-51 if for Intrepid as unstripped-52 is for Jaunty. 

I think you added the medibuntu for Intrepid if thats the case you need to change it to Hardy if your using Hardy (8.04).  


Try these commands after you change your medibuntu repo:

$ sudo apt-get remove libavcodec-unstripped-51

$ sudo apt-get install libavcodec-unstripped-5*

---

### Post by Mr_bleu on 2009-03-17
I'm using Intrepid.  THanks.

---

### Post by mc4man on 2009-03-17
mr bleu 
you still may want to try newer version of ffmpeg and libav*'

If you wish to build, FakeOutdoorsman has an excellent guide (tips and tutorials forum

If you'd rather stick with packages/ shared libs ect. then I've tested this ppa on a spare machine and works fine. Will update ffmpeg and your liba*'s to a very recent version.

Just installed on my friends laptop because he doesn't want to build, maintain, ect.

> ffmpeg
FFmpeg version SVN-r17516, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --extra-cflags=-Wall -g -fPIC -DPIC --cc=ccache cc --libdir=${prefix}/lib --shlibdir=${prefix}/lib --bindir=${prefix}/bin --incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir=${prefix}/share/man --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-libamr-nb --enable-libamr-wb --enable-x11grab --enable-libgsm --enable-libx264 --enable-libtheora --enable-swscale --enable-libdc1394 --enable-nonfree --disable-mmx --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --enable-libspeex --enable-avfilter-lavf --cpu=i686 --disable-static --shlibdir=/usr/lib/i686/cmov
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.18. 0 / 52.18. 0
  libavformat   52.29. 2 / 52.29. 2
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 3. 0 /  0. 3. 0
  libswscale     0. 7. 0 /  0. 7. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  2 2009 05:43:46, gcc: 4.3.2



See thread
[http://ubuntuforums.org/showthread.php?p=6827208#post6827208](http://ubuntuforums.org/showthread.php?p=6827208#post6827208)

---

### Post by Mr_bleu on 2009-03-18
How do I enable mp3?  I uninstalled the stripped libs and now mp3 isn't even listed.

djr@popeye-laptop:~$ ffmpeg -formats | grep lame
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
djr@popeye-laptop:~$

---

### Post by FakeOutdoorsman on 2009-03-19
> **Mr_bleu said:**
> How do I enable mp3?  I uninstalled the stripped libs and now mp3 isn't even listed.
You need **libavcodec-unstripped-51** to encode with libmp3lame.  I used the following and the audio worked fine:
```
ffmpeg -i input.mp4 -vcodec mpeg4 -vtag XVID -s 320x240 -qscale 10 -ab 48k -ar 22050 -ac 1 -acodec libmp3lame output.mp4
```
> **Mr_bleu said:**
> Sound doesn't work on the converted video.  Video plays though!!
Did the audio not work on your computer or on the Blackberry Storm?

---

### Post by Mr_bleu on 2009-03-20
> **FakeOutdoorsman said:**
> 
Did the audio not work on your computer or on the Blackberry Storm?

On the Curve 8330.

---

### Post by Mr_bleu on 2009-03-20
> **rmannon said:**
> I don't see --enable-libmp3lame after your $ ffmpeg -formats | grep lame


How do I enable it? 


From today:

djr@popeye-laptop:~$ ffmpeg -formats | grep lame
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:52:45, gcc: 4.3.2
  EA    libmp3lame

---

### Post by FakeOutdoorsman on 2009-03-20
It's already enabled for you.  The EA indicates that you can **E**ncode using libmp3lame which is an **A**udio codec.  The mp3 encoder in FFmpeg is called libmp3lame.  If the audio worked on your computer, then the encoder is working, and if it didn't work on the Blackberry then the file probably doesn't follow whatever specifications the phone demands.

Other users have indicated that the Curve can play H.264 video, but I'm unsure if all Curve models can.  If you would like to try this instead of FFmpeg's MPEG-4 then follow this tutorial:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Then try this command:
```
ffmpeg -i input.avi -an -vcodec libx264 -b 512k -bt 512k -s 480x360 -vpre hq -vpre baseline -pass 1 -threads 0 -f rawvideo /dev/null && ffmpeg -i input.avi -acodec libfaac -ab 96k -ar 44100 -vcodec libx264 -b 512k -bt 512k -s 480x360 -vpre hq -vpre baseline -pass 2 -threads 0 output.mp4
```
Notice that this command is actually two commands in one, so you will need to change both instances of **input.avi** to whatever your input video is.  If your source is widescreen, change 480x360 to 480x270.

---

### Post by FakeOutdoorsman on 2009-03-20
Attached is a video I just encoded using the above command (but with a much lower bitrate so it would upload).  You can test with this so you don't have to compile FFmpeg first.  You can probably extract it with File Roller, Nautilus, or whatever Gnome supplies or just:
```
tar xzvf butterfly.tar.gz
```

---

### Post by Mr_bleu on 2009-03-21
Thanks, I have it encoding a file now.  I used the link:
[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by andrew.46 on 2009-03-21
Hi Mr_bleu,

> **Mr_bleu said:**
> Thanks, I have it encoding a file now.  I used the link:
[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

Best move you have ever made :-). For the most part with the repository version you will be struggling against limitations of age and political / legal choices made by others.

Andrew

---

### Post by Mr_bleu on 2009-03-22
Still no sound on my Curve 8330.  Plays fine. Playback on my laptop is excellent and has sound.  I copy the file to my blackberry and it has no sound.

---

### Post by FakeOutdoorsman on 2009-03-22
> **Mr_bleu said:**
> Still no sound on my Curve 8330.  Plays fine. Playback on my laptop is excellent and has sound.  I copy the file to my blackberry and it has no sound.
No sound from my command from above or one from the earlier posts?  I don't have a Curve 8330 to test any of this, but I'm surprised that none of these commands created a fully working video for you.  I don't know what else to suggest, and I'm a little disappointed that it didn't work especially since you went through the trouble of compiling.  I assumed such a device should be able to play these two formats, but I guess I'm wrong.

---

### Post by andrew.46 on 2009-03-22
Hi Mr_bleu,

> **Mr_bleu said:**
> Still no sound on my Curve 8330.  Plays fine. Playback on my laptop is excellent and has sound.  I copy the file to my blackberry and it has no sound.

Like FakeOutdoorsman I am a little puzzled. Could you run FFmpeg over one of the files that plays on your computer but *not* on your phone:

```
ffmpeg -i myfile.mp4
```

and post the *full* commandline and *full* FFmpeg terminal output? This may give a hint as to what is going wrong.

Although it should not be necessary perhaps you could encode the sound to aac rather than mp3? The Fakeoutdoorsman's guide has left you with a copy of FFmpeg capable of this and I believe your Blackberry has the capability to playback mp3 as well as aac sound.

All the best,

Andrew

---

### Post by Mr_bleu on 2009-03-22
djr@popeye-laptop:~/Videos$ ffmpeg -y -i butterfly.mp4 -pass 1 -vcodec libx264 -vpre fastfirstpass -b 512k -bt 512k -threads 0 -f mp4 -an /dev/null && ffmpeg -i butterfly.mp4 -pass 2 -acodec libfaac -ab 128k -ac 2 -vcodec libx264 -vpre hq -b 512k -bt 512k -threads 0 -f mp4 output.mp4
FFmpeg version SVN-r18128, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 0. 0 / 50. 0. 0
  libavcodec    52.22. 0 / 52.22. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 21 2009 17:15:56, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'butterfly.mp4':
  Duration: 00:00:29.76, start: 0.000000, bitrate: 261 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 480x270, 29.97 tbr, 29.97 tbn, 59.94 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16
[libx264 @ 0x14a0820]width or height not divisible by 16 (480x270), compression will suffer.
[libx264 @ 0x14a0820]using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x14a0820]profile Main, level 2.1
Output #0, mp4, to '/dev/null':
    Stream #0.0(und): Video: libx264, yuv420p, 480x270, q=10-51, pass 1, 512 kb/s, 30k tbn, 29.97 tbc
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
frame=  890 fps=215 q=12.0 Lsize=       0kB time=29.66 bitrate=   0.0kbits/s    
video:1282kB audio:0kB global headers:1kB muxing overhead -99.999924%
[libx264 @ 0x14a0820]slice I:5     Avg QP:12.00  size:  4163
[libx264 @ 0x14a0820]slice P:376   Avg QP:13.09  size:  2135
[libx264 @ 0x14a0820]slice B:509   Avg QP:13.74  size:   961
[libx264 @ 0x14a0820]consecutive B-frames: 27.9%  0.2%  0.3%  0.9% 70.6%
[libx264 @ 0x14a0820]mb I  I16..4: 85.9%  0.0% 14.1%
[libx264 @ 0x14a0820]mb P  I16..4: 14.0%  0.0%  0.0%  P16..4: 11.2%  0.0%  0.0%  0.0%  0.0%    skip:74.8%
[libx264 @ 0x14a0820]mb B  I16..4:  1.3%  0.0%  0.0%  B16..8:  7.2%  0.0%  0.0%  direct: 1.8%  skip:89.6%  L0:47.8% L1:42.7% BI: 9.5%
[libx264 @ 0x14a0820]final ratefactor: 13.03
[libx264 @ 0x14a0820]direct mvs  spatial:93.1%  temporal:6.9%
[libx264 @ 0x14a0820]SSIM Mean Y:0.9989660
[libx264 @ 0x14a0820]kb/s:353.6
FFmpeg version SVN-r18128, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 0. 0 / 50. 0. 0
  libavcodec    52.22. 0 / 52.22. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 21 2009 17:15:56, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'butterfly.mp4':
  Duration: 00:00:29.76, start: 0.000000, bitrate: 261 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 480x270, 29.97 tbr, 29.97 tbn, 59.94 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16
[libx264 @ 0x2a3b8a0]width or height not divisible by 16 (480x270), compression will suffer.
[libx264 @ 0x2a3b8a0]using cpu capabilities: MMX2 SSE2Fast SSSE3 Cache64
[libx264 @ 0x2a3b8a0]Error: 2pass curve failed to converge
[libx264 @ 0x2a3b8a0]target: 512.00 kbit/s, expected: 498.69 kbit/s, avg QP: 10.0022
[libx264 @ 0x2a3b8a0]try reducing target bitrate or reducing qp_min (currently 10)
[libx264 @ 0x2a3b8a0]profile High, level 2.1
Output #0, mp4, to 'output.mp4':
    Stream #0.0(und): Video: libx264, yuv420p, 480x270, q=10-51, pass 2, 512 kb/s, 30k tbn, 29.97 tbc
    Stream #0.1(und): Audio: libfaac, 44100 Hz, stereo, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=  890 fps= 79 q=12.0 Lsize=    1301kB time=29.58 bitrate= 360.2kbits/s    
video:846kB audio:432kB global headers:1kB muxing overhead 1.729673%
[libx264 @ 0x2a3b8a0]slice I:5     Avg QP:11.15  size:  4359
[libx264 @ 0x2a3b8a0]slice P:376   Avg QP:12.30  size:  1641
[libx264 @ 0x2a3b8a0]slice B:509   Avg QP:13.43  size:   447
[libx264 @ 0x2a3b8a0]consecutive B-frames: 27.9%  0.2%  0.3%  0.9% 70.6%
[libx264 @ 0x2a3b8a0]mb I  I16..4: 84.1%  1.2% 14.7%
[libx264 @ 0x2a3b8a0]mb P  I16..4:  8.6%  0.2%  0.6%  P16..4:  5.9%  2.6%  2.4%  0.0%  0.0%    skip:79.8%
[libx264 @ 0x2a3b8a0]mb B  I16..4:  0.1%  0.0%  0.0%  B16..8:  7.5%  0.5%  0.8%  direct: 0.3%  skip:90.8%  L0:52.5% L1:45.0% BI: 2.5%
[libx264 @ 0x2a3b8a0]8x8 transform  intra:2.1%  inter:10.4%
[libx264 @ 0x2a3b8a0]direct mvs  spatial:89.8%  temporal:10.2%
[libx264 @ 0x2a3b8a0]ref P L0  71.7%  8.0%  9.7% 10.7%
[libx264 @ 0x2a3b8a0]ref B L0  76.6% 14.2%  9.3%
[libx264 @ 0x2a3b8a0]ref B L1  95.6%  4.4%
[libx264 @ 0x2a3b8a0]SSIM Mean Y:0.9993770
[libx264 @ 0x2a3b8a0]kb/s:233.4
djr@popeye-laptop:~/Videos

---

### Post by Mr_bleu on 2009-03-22
djr@popeye-laptop:~/Videos$ ffmpeg -i butterfly.mp4
FFmpeg version SVN-r18128, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid
  libavutil     50. 0. 0 / 50. 0. 0
  libavcodec    52.22. 0 / 52.22. 0
  libavformat   52.32. 0 / 52.32. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar 21 2009 17:15:56, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 29.97 (30000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'butterfly.mp4':
  Duration: 00:00:29.76, start: 0.000000, bitrate: 261 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 480x270, 29.97 tbr, 29.97 tbn, 59.94 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16
At least one output file must be specified
djr@popeye-laptop:~/Videos$

---

### Post by Mr_bleu on 2009-03-22
Main Options

-ab <int> : Set audio bitrate in bit/s ( default = 64k ).

-acodec <string> : Force audio codec.
    aac : AAC-LC
    ac3 : AC3 ( Dolby Digital )
    copy : Copy raw codec data as is.
    mp2 : MPEG Audio Layer II
    mp3 : MPEG Audio Layer III
    pcm_s16le : Uncompressed 16-bit PCM Audio
[SIZE="6"]
[COLOR="Red"]**-an : Disable audio. **[/COLOR][/SIZE]

Your code:
[SIZE="7"]ffmpeg -i input.avi -an -vcodec[/SIZE] libx264 -b 512k -bt 512k -s 480x360 -vpre hq -vpre baseline -pass 1 -threads 0 -f rawvideo /dev/null && ffmpeg -i input.avi -acodec libfaac -ab 96k -ar 44100 -vcodec libx264 -b 512k -bt 512k -s 480x360 -vpre hq -vpre baseline -pass 2 -threads 0 output.mp4


I hope I read that right.

---

### Post by FakeOutdoorsman on 2009-03-23
> **Mr_bleu said:**
> Main Options

-ab <int> : Set audio bitrate in bit/s ( default = 64k ).

-acodec <string> : Force audio codec.
    aac : AAC-LC
    ac3 : AC3 ( Dolby Digital )
    copy : Copy raw codec data as is.
    mp2 : MPEG Audio Layer II
    mp3 : MPEG Audio Layer III
    pcm_s16le : Uncompressed 16-bit PCM Audio
[SIZE="6"]
[COLOR="Red"]**-an : Disable audio. **[/COLOR][/SIZE]

Your code:
[SIZE="7"]ffmpeg -i input.avi -an -vcodec[/SIZE] libx264 -b 512k -bt 512k -s 480x360 -vpre hq -vpre baseline -pass 1 -threads 0 -f rawvideo /dev/null && ffmpeg -i input.avi -acodec libfaac -ab 96k -ar 44100 -vcodec libx264 -b 512k -bt 512k -s 480x360 -vpre hq -vpre baseline -pass 2 -threads 0 output.mp4


I hope I read that right.
You did read that right, but the first pass deals with video only.  The second pass has the audio options.  I gave you a two-pass encode because I wanted a specific bitrate.  Some of these devices have a specific max bitrate.

Can your device play a plain audio file fine?
```
ffmpeg -i butterfly.mp4 -acodec copy output.aac
```
or
```
ffmpeg -i butterfly.mp4 -acodec libmp3lame output.mp3
```

---

### Post by Mr_bleu on 2009-03-23
It plays.  Had to crank the volume up, but it played. :D

---

### Post by FakeOutdoorsman on 2009-03-23
Did it play the aac or the mp3 file?  I don't understand why it can not play the audio in the video, but it can play the audio separately.  Maybe your volume was too low?  Maybe it needs to be re-muxed:
```
sudo apt-get install gpac
MP4Box -add butterfly.mp4 newbutterfly.mp4
```

---

### Post by Mr_bleu on 2009-03-23
Funny thing, it would skip to the next song if I tried to raise the volume.

---

### Post by Mr_bleu on 2009-03-29
ffmpeg -i video.mp4  -vcodec libx264 -b 512k -bt 800k -r 17 -s 240x160 -an -vpre hq -vpre baseline -pass 1 -threads 0 -f rawvideo /dev/null && ffmpeg -i video.mp4 -acodec libfaac -ab 196k -ar 44100 -vcodec libx264 -b 512k -bt 800k -r 17 -s 240x160 -vpre hq -vpre baseline -pass 2 -threads 0 output.mp4

That worked for my Blackberry Curve.  Sound works, video plays.  I took a video and viewed the properties on my laptop and tweaked from there.  Thanks for everyone's help.

---

### Post by tcpankon on 2009-04-16
I have used the following on a pearl.  You should be able to modify the resolution (scale=240:180 section) to have it scale properly for the storm.  This script will take all files in the current directory and convert them to mp4 files in a directory called 'pearl' .  These should be capable of playing on a blackberry.  Simply move the script around and run it to transcode various files.
```
#!/bin/bash
VAR="files.txt"
ls *.avi | sort > $VAR
mkdir pearl
cat $VAR | while read line; do
  INPUT=$(echo ${line})
  OUTPUT="pearl/"
  OUTPUT+=${INPUT%.avi}
  OUTPUT+=".mp4"
  mencoder "$INPUT" -oac lavc -ovc lavc -of lavf -lavcopts  global=1:vglobal=1:vcodec=mpeg4:vbitrate=500:acodec=libfaac -af lavcresample=24000 -vf scale=240:180,harddup -ofps 30000/1001 -o "$OUTPUT"
done
rm $VAR
```

---

### Post by PerfectReign on 2009-09-27
I just tried this. I am fiddling with the command but not getting anywhere.

Here's what I get when I run the command. I have one file - l_backstroke.mpg - that is in the folder.

[FONT=Courier New][COLOR=Navy]kai@r2d2:~/Videos/temp$ bbvideo.sh
MEncoder 2:1.0~rc2-0ubuntu19+medibuntu1 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x1f5370
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [MJPG]  320x240  24bpp  10.000 fps  1229.0 kbps (150.0 kbyte/s)
[V] filefmt:3  fourcc:0x47504A4D  size:320x240  fps:10.00  ftime:=0.1000
==========================================================================
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 16000 Hz, 1 ch, u8, 128.0 kbit/100.00% (ratio: 16000->16000)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
** MUXER_LAVF *****************************************************************
REMEMBER: MEncoder's libavformat muxing is presently broken and can generate
INCORRECT files in the presence of B frames. Moreover, due to bugs MPlayer
will play these INCORRECT files as if nothing were wrong!
*******************************************************************************
OK, exit
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [scale w=240 h=180]
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
[libfaac @ 0x88433f0]libfaac doesn't support this output format!
Couldn't open codec libfaac, br=224.

Exiting..[/COLOR][/FONT].

Now, I checked if I had libfaac.

Sure enough, I do: libfaac0 1.26.0.1-ubuntu2 and libfaac-dev 1.26.0.1-ubuntu2

---

### Post by tcpankon on 2009-10-01
please post the contents of your script:  bbvideo.sh

---

### Post by PerfectReign on 2009-10-01
I'll attach it here.

What does work for me is this:

[FONT=System][COLOR=Blue]mencoder -vf scale=240:-10 <input file> -o <output file> -of avi -ofps 15 -ovc lavc -oac mp3lame -lavcopts vcodec=mpeg4:vbitrate=230:acodec=mp3:abitrate=64 -delay +2[/COLOR][/FONT]

I've been filling up my 4GB memory card with cool videos of my kids to show to customers and co-workers.

Notice the -delay +2. That is to synch the sound and video. I change around a bit for different videos as needed.

---

