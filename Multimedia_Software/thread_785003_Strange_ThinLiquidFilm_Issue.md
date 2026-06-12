---
title: "Strange ThinLiquidFilm Issue"
date: 2008-05-07
forum: Multimedia Software
---

### Post by IncredibleBulk on 2008-05-07
I was previously using ffmpeg + thinliquidfilm to convert video files for my Ipod. I've tried to install it again on my new Hardy set-up but it keeps falling over on me. I've been able to configure ffmpeg with x264 and xvid enabled, and thinliquidfilm can see this. But when I try to import a video to convert, I get this warning

FFmpeg version SVN-r13071, Copyright (c) 2000-2008 Fabrice Bellard, et al.
configuration: --enable-gpl --enable-libvorbis --enable-libtheora --enable-liba52 --enable-libdc1394 --enable-libgsm --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-libxvid --enable-pthreads --enable-libx264
libavutil version: 49.6.0
libavcodec version: 51.56.0
libavformat version: 52.13.0
libavdevice version: 52.0.0
built on May 7 2008 13:54:41, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, avi, from '/media/400-1/futurama.benders.big.score.anivcd.avi':
Duration: 01:28:50.19, start: 0.000000, bitrate: 1097 kb/s
Stream #0.0: Video: mpeg4, yuv420p, 640x352 [PAR 1:1 DAR 20:11], 23.98 tb(r)
Stream #0.1: Audio: mp3, 48000 Hz, stereo, 32 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s

Never seen those warning messages before and haven't been able to find a solution as to how to fix it. Just seems bizarre that I followed EXACTLY the same steps as previously but this error never occured before

---

### Post by Leechpool on 2009-02-26
IncredibleBulk, Did you ever sort this out - I'm getting exactly the same issue?
Does anyone know what's going on?
Cheers
:p

---

### Post by FakeOutdoorsman on 2009-02-26
You will need to patch TLF for it to be compatible with newer FFmpeg.
```

wget http://www.thinliquidfilm.org/tlf-1.00.tar.bz2
tar xjvf tlf-1.00.tar.bz2
cd thinliquidfilm
wget http://aur.archlinux.org/packages/thinliquidfilm/thinliquidfilm/0001-Fix-syntax-of-ffmpeg-interactions.patch
wget http://aur.archlinux.org/packages/thinliquidfilm/thinliquidfilm/0002-Fix-regular-expression-matching-of-ffmpeg-output.patch
wget http://aur.archlinux.org/packages/thinliquidfilm/thinliquidfilm/0003-Fix-change-of-motion-estimation-command-line-param.patch
patch -p1 < 0001-Fix-syntax-of-ffmpeg-interactions.patch
patch -p1 < 0002-Fix-regular-expression-matching-of-ffmpeg-output.patch
patch -p1 < 0003-Fix-change-of-motion-estimation-command-line-param.patch
sudo ./install.py
```
Patches courtesy of imrehg, [thinliquidfilm](http://aur.archlinux.org/packages.php?ID=13124) package maintainer on Arch Linux.  If you want to install the most recent FFmpeg:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Leechpool on 2009-03-02
FakeOutdoorsman, thanks for your post. I followed your instructions and all seems to go well (I can sucessfully select a video to transcode) but when I hit transcode the program gives errors. Its looks like its still the FFMPEG issue. Can you make any more suggestions. The shell output is:

```
bert@bert-desktop:~$ sudo thinliquidfilm/
sudo: thinliquidfilm/: command not found
bert@bert-desktop:~$ sudo thinliquidfilm
[]
ffmpeg supports xvid
ffmpeg supports x264
tab changed
changed to "encode"
/home/bert/.thinliquidfilm/latest
1.0
Version Check:  Update message already shown
Version Check:  This is the latest version
tab changed
changed to "encode"
/home/bert/thinliquidfilm/video/Yes/Moulin Rouge.avi
Values:
['mpeg2video', 175675, '0.9444', '2213', 7027000, '544x576']
['/home/bert/thinliquidfilm/video/Yes/Moulin Rouge.avi']
[['1', ['320x338', '640x678'], 0, 'h264', '160', '/home/bert']]
A file has been selected
0 is selected
0
1
update thinks these are selected:
[0]
[['1', ['320x338', '640x678'], 0, 'h264', '160', '/home/bert']]
A file has been selected
0 is selected
0
1
update thinks these are selected:
[0]
[['1', ['320x338', '640x678'], 0, 'h264', '160', '/home/bert']]
main.setDestination(): Not implemented yet
update thinks these are selected:
[0]
[['1', ['320x338', '640x678'], 0, 'h264', '160', '/home/bert/thinliquidfilm/video/Yes/']]
self.encodeSettings:
[['1', ['320x338', '640x678'], 0, 'h264', '160', '/home/bert/thinliquidfilm/video/Yes/']]
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from '/home/bert/thinliquidfilm/video/Yes/Moulin Rouge.avi':
  Duration: 01:57:07.0, start: 0.000000, bitrate: 2213 kb/s
    Stream #0.0: Video: mpeg2video, yuv420p, 544x576 [PAR 32:17 DAR 16:9], 10000 kb/s, 25.00 tb(r)
    Stream #0.1: Audio: mp2, 48000 Hz, stereo, 192 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'h264'

no match

no match

no match

no match

no match

no match

no match

no match
^CTraceback (most recent call last):
  File "/usr/local/thinliquidfilm/main.py", line 2736, in encode
    time.sleep(1)
KeyboardInterrupt



```

Thanks for trying to help.
Cheers
:P

---

### Post by FakeOutdoorsman on 2009-03-02
I've never used thinliquid film, but those patches should have corrected the syntax, however it still looks like TLF is using the old syntax (h264 instead of libx264).  The developer of TLF hasn't updated it to reflect the changes in FFmpeg.  What are you trying to encode to?  I could give you a command to use FFmpeg itself instead of this possibly abandoned software.

---

### Post by Leechpool on 2009-03-02
I'm trying to encode video recorded on my Topfield PVR for playing on my ipod. Thinliquidfilm used to do a great job without having to think about it and the h.264 codec gave great performance for small file sizes.

I've tried the command line but get the following error:

```
bert@bert-desktop:~$ cd videotemp/converted/
bert@bert-desktop:~/videotemp/converted$ ls
test.mpg
bert@bert-desktop:~/videotemp/converted$ ffmpeg -i test.mpg -acodec libfaac -ab 128k -s qvga -vcodec libx264 -vpre hq -vpre ipod320 -b 750k -bt 100k -title TEST_Title -threads 0 OUTPUT.mp4
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, mpeg, from 'test.mpg':
  Duration: 00:01:09.0, start: 0.264656, bitrate: 5280 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576 [PAR 16:15 DAR 4:3], 4500 kb/s, 25.00 tb(r)
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, 224 kb/s
ffmpeg: unrecognized option '-vpre'
bert@bert-desktop:~/videotemp/converted$ 


```

Many of the examples I find on the net have this -vpre setting but my ffmpeg doesn't seem to recognise it?

Cheers
:P

---

### Post by FakeOutdoorsman on 2009-03-02
FFmpeg from the repository is very old and doesn't support the libx264 presets, but you can compile it yourself easily:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by Leechpool on 2009-03-04
FakeOutdoorsman.
Thanks for trying to help. I tried various ways to encode and was all set to install a more up to date ffmpeg etc as per your other thread when I found that the instructions in the ubuntu howto encode video for ipod worked using the default ubtuntu ffmpeg with libx264 enabled (as I guess you'd expect)

[HTML]https://help.ubuntu.com/community/iPodVideoEncoding[/HTML]

The code from there I used was :

```
ffmpeg -y -i input_file.avi -an -v 1 -threads auto -vcodec libx264 -b 500k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 640x480 -f mp4 -pass 1 /dev/null

ffmpeg -y -i input_file.avi -v 1 -threads auto -vcodec libx264 -b 500k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 640x480 -acodec libfaac -ab 96 -ar 48000 -ac 2 -f mp4 -pass 2 output_file.mp4
```

Armed with the knowledge my default ubuntu ffmpeg etc was capable of creating libx264 video for my ipod I decided to look at the python code in thinliquid film and try to work out why it wasn't working. This was a very big ask for me (i'm not familiar with programming in any language let alone python). Anyway I was changing the script slightly to print out variable contents at various points so I could try to follow it and as I started to understand what was going on it started working. I didn't change anything and in fact replaced the python program with the original I had backed up and it carried on working. I even shutdown and restarted but it carried on working.

So just to say that I must have done something very strange and the patched you pointed me to to correct thinliquidfilm did work (in the end).

Thanks again for your help.

Cheers
:D

---

### Post by motin on 2009-03-08
> **Leechpool said:**
> FakeOutdoorsman, thanks for your post. I followed your instructions and all seems to go well (I can sucessfully select a video to transcode) but when I hit transcode the program gives errors. Its looks like its still the FFMPEG issue. Can you make any more suggestions. The shell output is:

```
bert@bert-desktop:~$ sudo thinliquidfilm/
sudo: thinliquidfilm/: command not found
bert@bert-desktop:~$ sudo thinliquidfilm
[]
ffmpeg supports xvid
ffmpeg supports x264
tab changed
changed to "encode"
/home/bert/.thinliquidfilm/latest
1.0
Version Check:  Update message already shown
Version Check:  This is the latest version
tab changed
changed to "encode"
/home/bert/thinliquidfilm/video/Yes/Moulin Rouge.avi
Values:
['mpeg2video', 175675, '0.9444', '2213', 7027000, '544x576']
['/home/bert/thinliquidfilm/video/Yes/Moulin Rouge.avi']
[['1', ['320x338', '640x678'], 0, 'h264', '160', '/home/bert']]
A file has been selected
0 is selected
0
1
update thinks these are selected:
[0]
[['1', ['320x338', '640x678'], 0, 'h264', '160', '/home/bert']]
A file has been selected
0 is selected
0
1
update thinks these are selected:
[0]
[['1', ['320x338', '640x678'], 0, 'h264', '160', '/home/bert']]
main.setDestination(): Not implemented yet
update thinks these are selected:
[0]
[['1', ['320x338', '640x678'], 0, 'h264', '160', '/home/bert/thinliquidfilm/video/Yes/']]
self.encodeSettings:
[['1', ['320x338', '640x678'], 0, 'h264', '160', '/home/bert/thinliquidfilm/video/Yes/']]
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Oct  3 2008 22:40:31, gcc: 4.3.2
Input #0, avi, from '/home/bert/thinliquidfilm/video/Yes/Moulin Rouge.avi':
  Duration: 01:57:07.0, start: 0.000000, bitrate: 2213 kb/s
    Stream #0.0: Video: mpeg2video, yuv420p, 544x576 [PAR 32:17 DAR 16:9], 10000 kb/s, 25.00 tb(r)
    Stream #0.1: Audio: mp2, 48000 Hz, stereo, 192 kb/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'h264'

no match

no match

no match

no match

no match

no match

no match

no match
^CTraceback (most recent call last):
  File "/usr/local/thinliquidfilm/main.py", line 2736, in encode
    time.sleep(1)
KeyboardInterrupt



```

Thanks for trying to help.
Cheers
:P

Yeah I get the exact same with the latest ffmpeg and those patches. Without more contributed hacking to get tlf compatible with the current ffmpeg I don't see how we will be able to use it. Revert back to an older ffmpeg meanwhile - or try another gui. 

I don't know what you are trying to convert, but I recommend mvPod - a GUI for mencoder. You may need an updated version of the gpac package in order for it to work, but otherwise than that it's a great and easy to use GUI. 

I however am dependent on features onyl available in the latest ffmpeg and not in mencoder so I'll go on try to find a suitable gui. My father has to be able to use it to convert our family camcorder AVCHD MTS files...

Cheers!

---

