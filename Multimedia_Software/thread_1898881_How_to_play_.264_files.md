---
title: "How to play .264 files"
date: 2011-12-22
forum: Multimedia Software
---

### Post by PaulM1985 on 2011-12-22
Hi

My friend has been sent some video files from a security camera but is unable to play them.  The disk contained 3 *.264 files and 1 *.md5.  He has tried opening the .264 files in VLC and they haven't worked and also tried changing the file extension to .avi and .mp4, but neither of these have worked.

Does anyone know what these files are and how these could be opened?

Thanks in advance

Paul

---

### Post by ron999 on 2011-12-22
> **PaulM1985 said:**
> ... The disk contained 3 *.264 files...

Does anyone know what these files are and how these could be opened?


Hi
To play those .264 files....
Put them in mkv containers using mkvmerge-gui (mkvtoolnix-gui).


Or put them in mp4 containers.
Use MP4Box (part of gpac package) like this:-
```
MP4Box -add filename.264 filename.mp4
```

Or use FFmpeg like this:-
```
ffmpeg -i filename.264 -vcodec copy filename.mp4
```

---

### Post by andrew.46 on 2011-12-22
A modern enough version of MPlayer will usually be able to play raw h.264 streams but it usually helps to feed it with a few extra parameters such as fps, selected demuxer etc.

---

### Post by PaulM1985 on 2011-12-30
> **ron999 said:**
> Hi
To play those .264 files....
Put them in mkv containers using mkvmerge-gui (mkvtoolnix-gui).


Or put them in mp4 containers.
Use MP4Box (part of gpac package) like this:-
```
MP4Box -add filename.264 filename.mp4
```

Or use FFmpeg like this:-
```
ffmpeg -i filename.264 -vcodec copy filename.mp4
```

Thanks for the suggestions, but neither seemed to work.
```
MP4Box -add filename.264 filename.mp4
```
Gave:
```

Cannot find H264 start code
Error importing ch00000000000003-111112-180000-180000-01p003000000.264: BitStream Not Compliant

```

and
```
ffmpeg -i filename.264 -vcodec copy filename.mp4
```
gave:
```

FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Sep 16 2011 17:08:44, gcc: 4.4.3
[mp3 @ 0xf06480]Could not find codec parameters (Audio: mp1, 0 channels, s16)
ch00000000000003-111112-180000-180000-01p003000000.264: could not find codec parameters

```

My other files get "unknown format" errors.

Any other suggestions?  There is a file that came with these video files called ".checksum.md5".  Would this be important in any way?

Paul

---

### Post by rubylaser on 2011-12-30
You could give it a shot with mkvmerge...
```
sudo apt-get install mkvtoolnix
```
```
mkvmerge -o ~/output_file.mkv --default-duration 0:23.976fps input_video.h264
```

With raw h264 video, you need to tell mkvmerge the framerate or it defaults to 25 fps.  Your security camera footage is probably 30 fps, so adjust the above accordingly.  The checksum md5, is so you can validate that the file you have is what it should be.  It is not necessary for proper playback.  You can view the file like this if you're interested.

[CODE}md5sum .checksum.md5[/CODE]

---

### Post by PaulM1985 on 2011-12-31
Nope that didn't work either:
```

paul@paul-desktop:~/Desktop/CCTV for Paul$ mkvmerge -o ~/output.mkv --default-duration 0:23.976fps ch00000000000003-111112-180000-180000-01p003000000.264 
mkvmerge v3.0.0 ('Hang up your Hang-Ups') built on Dec 29 2009 00:21:20
'ch00000000000003-111112-180000-180000-01p003000000.264': Using the AVC/h.264 ES demultiplexer.
'ch00000000000003-111112-180000-180000-01p003000000.264' track 0: Using the MPEG-4 part 10 ES video output module.
The file '/home/paul/output.mkv' has been opened for writing.
Error: 'ch00000000000003-111112-180000-180000-01p003000000.264' track 0: mkvmerge encountered broken or unparsable data in this AVC/h.264 video track. Either your file is damaged (which mkvmerge cannot cope with yet) or this is a bug in mkvmerge itself. The error message was:
end-of-file

```
Any other ideas?
Paul

---

### Post by PaulM1985 on 2011-12-31
When I do:
```
file [filename].264
```
I get:
```
[filename].264 data
```
as a response.  Does this mean that the file might not actually be a video file and might have some special encryption?

Paul

---

### Post by stuartcnz on 2012-01-01
Have you got the codecs to play h264 files? 

You probably need libx264. then I would be inclined to use KDEnlive to convert the file to something that your system is already comfortable with, which will depend on what codecs you already have installed.

Make sure you have a backup copy of the original file before you start messing with it though.

---

### Post by PaulM1985 on 2012-01-01
Yep, I already have that installed.

Paul

---

### Post by syerges on 2012-01-01
[https://launchpad.net/~sunab/+archive/sunab2]("https://launchpad.net/%7Esunab/+archive/sunab2")

---

### Post by syerges on 2012-01-01
You can build a new version of ffmpeg and ffmpeg-extra using ubuntu sources.
You need to somewhat know what you are doing, but this webpage is useful and can be adapted for your needs.
[http://ubuntuforums.org/showthread.php?t=1071262](http://ubuntuforums.org/showthread.php?t=1071262)
 You would need to build both the ffmpeg and ffmpeg-extra packages.
 [http://packages.ubuntu.com/source/karmic/ffmpeg](http://packages.ubuntu.com/source/karmic/ffmpeg)
and
[http://packages.ubuntu.com/source/karmic/ffmpeg-extra](http://packages.ubuntu.com/source/karmic/ffmpeg-extra)
 You would not need to edit any debian/ files just install the .diff  patch and build with these commands for both ffmpeg and then  ffmpeg-extra
 Commands:
export DEBEMAIL="Your Name"
 debchange --nmu "Rebuild enabling --enable-nonfree --enable-externalcodecs"
 DEB_BUILD_OPTIONS="--enable-externalcodecs --enable-nonfree" debuild -rfakeroot -uc -us -b
 Install the local packages and re-run the kdenlive config wizard to pick up the changes.

---

