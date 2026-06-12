---
title: "convert .mpg to .mov"
date: 2008-05-27
forum: Multimedia Software
---

### Post by rapattack1 on 2008-05-27
Hi I know that this question has been asked a lot but I don't seem to be getting anywhere. I want to convert a .mpg to .mov and I have read so many wiki's and other sites. I tried doing it via mencoder and ffmpeg(winff). Mencoder gave me an output that was faster than the input file both with sound and video. FFmpeg gave me something that looked like a txt file. So basicly I realise I should put in some more info to get a better result. I have a pda device and I would like to put the file on there. It does say that it plays mpeg files but so far it doesn't. I changed the extension from .mpg to .mpeg to see and no go. The pda reads it as 0.00 kb's. The pda is a Sony Clie nx70v which is old but gee it is a nice little machine.

---

### Post by FakeOutdoorsman on 2008-05-27
These PDAs can be picky with the video formats.  The best thing to do is create a video from the PDA and then use ffmpeg to see its specs:
```
ffmpeg -i videofrompda.mpg
```
Then you can see the size, bitrate, codec, container, etc.  If you post it here I can come up with a ffmpeg command for it.

---

### Post by rapattack1 on 2008-05-27
That makes a lot of sense. This is what I got:
carla@carla-desktop:~/Desktop$ ffmpeg -i videofrompda.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
videofrompda.mpg: I/O error occured
Usually that means that input file is truncated and/or corrupted.

---

### Post by FakeOutdoorsman on 2008-05-28
This error means there is something horribly wrong with the input file, or perhaps the path to the file is incorrect.  Can you view or play the PDA video in Ubuntu?  If you want to upload the file I can check it out with the latest version of ffmpeg.

---

### Post by rapattack1 on 2008-05-29
Oops I copied that line exactly as you typed it. The file is not videofrompda.mpg....silly me.

This is what is happening:
carla@carla-desktop:~/Desktop$ ffmpeg -i perfectmatch.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, mpeg, from 'perfectmatch.mpg':
  Duration: 00:01:30.4, start: 0.224400, bitrate: 2310 kb/s
  Stream #0.0[0x1c0]: Audio: mp2, 44100 Hz, stereo, 224 kb/s
  Stream #0.1[0x1e0]: Video: mpeg2video, yuv420p, 320x240, 6000 kb/s, 25.00 fps(r)
Must supply at least one output file

carla@carla-desktop:~/Desktop$ ffmpeg -i MOV00002.MOV
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 30000.00 (30000/1) -> 25.00 (25/1)
Input #0, m4v, from 'MOV00002.MOV':
  Duration: N/A, bitrate: N/A
  Stream #0.0: Video: mpeg4, yuv420p, 160x112, 25.00 fps(r)
Must supply at least one output file
carla@carla-desktop:~/Desktop$ 

I had to files to experiment on so they are both above. I am not able to upload as they are too large. I have a very small internet usage.

---

### Post by FakeOutdoorsman on 2008-05-29
ffmpeg from the Ubuntu repository has not been compiled to support restricted formats (mp3, aac, etc), so I recommend you uninstsall it, add the [Medibuntu repository]("http://medibuntu.org"), and install ffmpeg from the new repository.  If you're feeling adventurous, you could instead compile the newest version yourself: [HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095").

I believe ffmpeg is having trouble getting information from the MOV file because it probably contains a restricted format, so the Medibuntu ffmpeg should fix that.

Now that we know what the PDA likes, you can try to convert to that format:
```
ffmpeg -i MOV00002.MOV -acodec mp2 -ar 44100 -ac 2 -ab 128k -vcodec mpeg2video -s 320x240 -vb 800k -r pal outputvideo.mpg
```
I didn't test this command, but it should work.

---

### Post by rapattack1 on 2008-06-01
I tried to install the medibuntu stuff but somehow I stuffed up. Errors are everywhere. Everything I do and it has affected Skype. i did see the warning in that link about that skype but I don't know where I went wrong. How do i go back to the beginning?

---

### Post by FakeOutdoorsman on 2008-06-02
What are some of the errors you are getting?  This command should list all packages associated with Medibuntu:
```
dpkg -l medibuntu
```
What packages does that command list?

---

### Post by rapattack1 on 2008-06-02
carla@carla-desktop:~$ dpkg -l medibuntu
No packages found matching medibuntu.

Um I can't remember now. All I know is that the update manager thingy wants to get skype-common(medibuntu) and it doesn't get it even after I press install. Ah ok I tried again and it gave me this :
E: /var/cache/apt/archives/skype-common_2.0.0.68+repack-0medibuntu3_all.deb: trying to overwrite `/usr/share/skype/avatars/Empire Skype.png', which is also in package skype

There is also a whole list of other stuff it wants (lib.....) but those items are unchecked including skype.

---

