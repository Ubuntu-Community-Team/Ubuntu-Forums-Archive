---
title: "Converting mp3 to video mp4 for YouTube?"
date: 2010-12-22
forum: Multimedia Software
---

### Post by cybrsaylr on 2010-12-22
I have uploaded video files like mp4 to YouTube but how do you convert an mp3 file to a video file such as mp4 that YouTube will accept for upload?

Never did this before.

---

### Post by ron999 on 2010-12-22
> **cybrsaylr said:**
> ... but how do you convert an mp3 file to a video file such as mp4 that YouTube will accept for upload?


Look here....[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1649844]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1649844")

---

### Post by cybrsaylr on 2010-12-22
Ok I installed ffmpeg but can't find or open it.

So I don't know what to do next.

---

### Post by ron999 on 2010-12-22
> **cybrsaylr said:**
> Ok I installed ffmpeg but can't find or open it.

So I don't know what to do next.

ffmpeg runs from the command line.

You need the files **picture.jpg** and **song.mp3** in your home/user folder then copy and paste the command into the terminal.

---

### Post by cybrsaylr on 2010-12-22
> **ron999 said:**
> 

You need the files **picture.jpg** and **song.mp3** in your home/user folder then copy and paste the command into the terminal.

OK I put the pic jpg and song mp3 into home folder.
Then pasted your command in terminal:
> ffmpeg -loop_input -i picture.jpg -i song.mp3 -shortest -b 1000k -acodec copy video.mp4

But it doesn't do anything and I get this message,

> FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
[image2 @ 0xe1a260]Could not find codec parameters (Video: mjpeg)
picture.jpg: could not find codec parameters


What am I doing wrong?
As I said I never did this before.

---

### Post by ron999 on 2010-12-22
Hi
Maybe you need to install the extra libraries.
Read the explanation and then try option B here:-
[http://ubuntuforums.org/showthread.php?t=1117283]("http://ubuntuforums.org/showthread.php?t=1117283")

---

### Post by cybrsaylr on 2010-12-22
Hi,
Did Option B and got this Terminal output:
> tt@tt-desktop:~$ ffmpeg -loop_input -i picture.jpg -i song.mp3 -shortest -b 1000k -acodec copy video.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
[image2 @ 0x1cefef0]Could not find codec parameters (Video: mjpeg)
picture.jpg: could not find codec parameters


I then went ahead and did Option C.
Ran it and got this output:
> tt@tt-desktop:~$ ffmpeg -loop_input -i picture.jpg -i song.mp3 -shortest -b 1000k -acodec copy video.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
[image2 @ 0x211def0]Could not find codec parameters (Video: mjpeg)
picture.jpg: could not find codec parameters


I am stumped.

---

### Post by ron999 on 2010-12-22
> **cybrsaylr said:**
> 
I am stumped.

I'm running out of ideas too.
Maybe there's something wrong with that jpg, try using a different picture.

---

### Post by cybrsaylr on 2010-12-22
Tried a different pix and get this:
> tt@tt-desktop:~$ ffmpeg -loop_input -i picture.jpg -i song.mp3 -shortest -b 1000k -acodec copy video.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
[image2 @ 0x211def0]Could not find codec parameters (Video: mjpeg)
picture.jpg: could not find codec parameters

Does it matter where the jpg and mp3 files are in home folder?
I just dropped them into 'home folder' with the other default folders and folders I created.

---

### Post by ron999 on 2010-12-22
No, it doesn't matter where they are inside the home folder.
ffmpeg has found the jpg picture(s) OK - but it's having trouble handling them.:confused:

Try using a **png** picture instead of a jpg. And change the command.
```
ffmpeg -loop_input -i picture.png -i song.mp3 -shortest -b 1000k -acodec copy video.mp4 

```

---

### Post by cybrsaylr on 2010-12-22
Did that. Changed pic to png and get this:
> tt@tt-desktop:~$ ffmpeg -loop_input -i picture.png -i song.mp3 -shortest -b 1000k -acodec copy video.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
[image2 @ 0xda4ef0]Could not find codec parameters (Video: png)
picture.png: could not find codec parameters


---

### Post by ron999 on 2010-12-22
No more ideas.
:(

---

### Post by cybrsaylr on 2010-12-22
Just tried a third pic with the same results as above.

Well thanks for the help anyways ron999.

---

### Post by FakeOutdoorsman on 2010-12-22
Can you provide a sample of the image? jpg or png would be fine.

---

### Post by cybrsaylr on 2010-12-22
Here's the jpg:
[IMG]http://i.imgur.com/6F6oW.jpg?1023[/IMG]

---

### Post by FakeOutdoorsman on 2010-12-22
I see what's going on. When your input file is an image, and if FFmpeg can't find the input file it will give you that message. Not a very helpful message in my opinion.  You need to give the correct name and location of the file to FFmpeg. For example, if your image is saved onto your desktop, you can do:
```
ffmpeg -i ~/Desktop/6F6oW.jpg ...
```

---

### Post by cybrsaylr on 2010-12-22
What code should if use if both jpg and mp3 are on desktop?

---

### Post by ron999 on 2010-12-22
Hi
I'll jump back in here now FakeOutdoorsman has solved it.:D
```
ffmpeg -loop_input -i ~/Desktop/picture.jpg -i ~/Desktop/song.mp3 -shortest -b 1000k -acodec copy video.mp4 

```

---

### Post by FakeOutdoorsman on 2010-12-22
I don't know the name of your files, so I'll just use *input.jpg* and *input.mp3*. When you open Terminal it uses your home directory as your current directory. You can either navigate to your desktop and then issue the FFmpeg command:
```
cd ~/Desktop
ffmpeg -loop_input -i input.jpg -i input.mp3 -qscale 3 -acodec copy -shortest output.mkv
```
...or you can give the full path to the input files:
```
ffmpeg -loop_input -i ~/Desktop/input.jpg -i ~/Desktop/input.mp3 -qscale 3 -acodec copy -shortest output.mkv
```
Notice the **~**. It's a shortcut for your home directory, for example: **/home/cybrsaylr**.

> **ron999 said:**
> Hi
I'll jump back in here now FakeOutdoorsman has solved it.:D
```
ffmpeg -loop_input -i ~/Desktop/picture.jpg -i ~/Desktop/song.mp3 -shortest -b 1000k -acodec copy video.mp4 

```
**Update:** I'm slow.

---

### Post by ron999 on 2010-12-22
> **FakeOutdoorsman said:**
> 

**Update:** I'm slow.

But you're the brains behind the operation.:D

---

### Post by cybrsaylr on 2010-12-22
OK I put it in exactly as posted in terminal and got this output:
> tt@tt-desktop:~$ ffmpeg -loop_input -i ~/Desktop/picture.jpg -i ~/Desktop/song.mp3 -shortest -b 1000k -acodec copy video.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
[image2 @ 0x183eef0]Could not find codec parameters (Video: mjpeg)
/home/tt/Desktop/picture.jpg: could not find codec parameters


Since I am no expert at command line I suspect I am doing something wrong.

---

### Post by ron999 on 2010-12-22
> **cybrsaylr said:**
> 
Since I am no expert at command line I suspect I am doing something wrong.
Try using FakeOutdoorsman's two suggestions in post #19

---

### Post by cybrsaylr on 2010-12-22
When I insert the name of the pic file and name of the song file on desktop into that command this is the output:
> tt@tt-desktop:~$ ffmpeg -loop_input -i ~/Desktop/Leila Maria - front.jpg -i ~/Desktop/13 A Little Tear (razao de viver).mp3 -shortest -b 1000k -acodec copy video.mp4
bash: syntax error near unexpected token `('


---

### Post by ron999 on 2010-12-22
Hi
It's because the filenames are broken into separate words:- Leila Maria - front.jpg
Instead of all_one_word like this:- Leila_Maria_front.jpg

To overcome this, put the broken filenames in quotes.
Like this:-
```
ffmpeg -loop_input -i "~/Desktop/Leila Maria - front.jpg" -i "~/Desktop/13 A Little Tear (razao de viver).mp3" -shortest -b 1000k -acodec copy video.mp4
```

---

### Post by cybrsaylr on 2010-12-22
> **ron999 said:**
> Hi
It's because the filenames are broken into separate words:- Leila Maria - front.jpg
Instead of all_one_word like this:- Leila_Maria_front.jpg

Hi again,
When i put it in quotes i get the same output as before.

So I tried making it one_word_as_you_suggested_ and and renaming the files to shorten them and now got this:
> tt@tt-desktop:~$ ffmpeg -loop_input -i ~/Desktop/Leila_Maria.jpg -i ~/Desktop/A_Little_Tear.mp3 -shortest -b 1000k -acodec copy video.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
Input #0, image2, from '/home/tt/Desktop/Leila_Maria.jpg':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj420p, 400x400 [PAR 1:1 DAR 1:1], 25 tbr, 25 tbn, 25 tbc
/home/tt/Desktop/A_Little_Tear.mp3: no such file or directory


As I said I'm no command line guy but it looks like it responded different this last attempt.

---

### Post by ron999 on 2010-12-23
> tt@tt-desktop:~$ ffmpeg -loop_input -i ~/Desktop/Leila_Maria.jpg -i ~/Desktop/A_Little_Tear.mp3 -shortest -b 1000k -acodec copy video.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
libavutil 49.15. 0 / 49.15. 0
libavcodec 52.20. 0 / 52.20. 0
libavformat 52.31. 0 / 52.31. 0
libavdevice 52. 1. 0 / 52. 1. 0
libavfilter 0. 4. 0 / 0. 4. 0
libswscale 0. 7. 1 / 0. 7. 1
libpostproc 51. 2. 0 / 51. 2. 0
built on Apr 23 2010 15:38:06, gcc: 4.4.1
Input #0, image2, from '/home/tt/Desktop/Leila_Maria.jpg':
Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
Stream #0.0: Video: mjpeg, yuvj420p, 400x400 [PAR 1:1 DAR 1:1], 25 tbr, 25 tbn, 25 tbc
[COLOR="Red"]/home/tt/Desktop/A_Little_Tear.mp3: no such file[/COLOR] or directory 
....

---

### Post by cybrsaylr on 2010-12-23
Hi,
Well I finally got somewhere.....sort of....

I converted that mp3 to an ogg file with Sound Converter.
I also tried converting to flac and wav but those two would not work with FFmpeg. Only ogg converted with FFmpeg.

Then put that command in terminal as shown below and it worked!
Here is the output:
> tt@tt-desktop:~$ ffmpeg -loop_input -i ~/Desktop/Leila_Maria.jpg -i ~/Desktop/_A_Little_Tear.ogg -shortest -b 1000k -acodec copy video.mp4


FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
Input #0, image2, from '/home/tt/Desktop/Leila_Maria.jpg':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj420p, 400x400 [PAR 1:1 DAR 1:1], 25 tbr, 25 tbn, 25 tbc
Input #1, ogg, from '/home/tt/Desktop/_A_Little_Tear.ogg':
  Duration: 00:04:03.59, start: 0.000000, bitrate: 176 kb/s
    Stream #1.0: Audio: vorbis, 44100 Hz, stereo, s16, 192 kb/s
File 'video.mp4' already exists. Overwrite ? [y/N] y
Output #0, mp4, to 'video.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 400x400 [PAR 1:1 DAR 1:1], q=2-31, 1000 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: vorbis, 44100 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #1.0 -> #0.1
Press [q] to stop encoding
frame= 6090 fps=455 q=2.0 Lsize=   18596kB time=243.58 bitrate= 625.4kbits/s    
video:13218kB audio:5137kB global headers:0kB muxing overhead 1.314249%


The only problem is it will not play audio.
VLC shows the jpg but says:
> No suitable decoder module:
VLC does not support the audio or video format "mp4a". Unfortunately there is no way for you to fix this.

Movie Player opens and shows the jpg but that mp4 but won't play the audio.
Here's a screenshot:
[IMG]http://i.imgur.com/JUPRj.png?4902[/IMG]


Any ideas on what to do?

---

### Post by ron999 on 2010-12-23
> **cybrsaylr said:**
> 
Any ideas on what to do?

Figure out why ffmpeg says that the mp3 file doesn't exist.

Is the file name
**A_Little_Tear.mp3**
Or is it
**_A_Little_Tear.mp3**


If you're prone to typos then rename the mp3 file **song.mp3**

---

### Post by cybrsaylr on 2010-12-23
> **ron999 said:**
> Figure out why ffmpeg says that the mp3 file doesn't exist.

Is the file name
**A_Little_Tear.mp3**
Or is it
**_A_Little_Tear.mp3**


If you're prone to typos then rename the mp3 file **song.mp3**

Those 3 options don't work and give this same output:
> tt@tt-desktop:~$ ffmpeg -loop_input -i picture.png -i song.mp3 -shortest -b 1000k -acodec copy video.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
[image2 @ 0xb84ef0]Could not find codec parameters (Video: png)
picture.png: could not find codec parameters


This ogg command is the only one that works but there is no audio:
> ffmpeg -loop_input -i ~/Desktop/Leila_Maria.jpg -i ~/Desktop/A_Little_Tear.ogg -shortest -b 1000k -acodec copy video.mp4

---

### Post by ron999 on 2010-12-23
right-click 'copy' the mp3 file from your desktop and 'paste' it here.
Like this:-
```
/home/ron/Desktop/song.mp3
```

---

### Post by cybrsaylr on 2010-12-23
OK, here is what I got:

> /home/tt/Desktop/ _A_Little_Tear.mp3

---

### Post by ron999 on 2010-12-23
> **cybrsaylr said:**
> OK, here is what I got:
Quote:
/home/tt/Desktop/ _A_Little_Tear.mp3

OK
So your file name is 
**/home/tt/Desktop/ _A_Little_Tear.mp3**
 
_**That's got a space and an underscore in front of it.**_
That's why ffmpeg can't find the file.

So rename it without the space and the first underscore.
Like this:-
**A_Little_Tear.mp3**

It's got to be exactly right.

Then use the command again:-
```
ffmpeg -loop_input -i ~/Desktop/Leila_Maria.jpg -i ~/Desktop/A_Little_Tear.mp3 -shortest -b 1000k -acodec copy video.mp4

```

---

### Post by cybrsaylr on 2010-12-23
EUREKA!!!!!

It finally worked! 
That's got a _space_ and an underscore in front of it.
That extra **space** was the problem.

As stated earlier, I am weak on command line. Usually just get the needed code and copy/paste into Terminal and it works. This ffmepg app is the first time using solely CL. 

Thanks for all the help ron999.

Just uploaded it to YouTube using ffmpeg for the first time for conversion.
It went through OK. 

It's a nice tune.
FWIW here's a link:
[http://www.youtube.com/watch?v=BsHhDdXM7_Y](http://www.youtube.com/watch?v=BsHhDdXM7_Y)

---

### Post by ron999 on 2010-12-23
Glad it's sorted out.:D
ffmpeg's much more fun than Windows Movie Maker.;)

---

### Post by cybrsaylr on 2010-12-24
Never used Windows Movie Maker.

Used FFmpeg a couple more times and discovered less typo mistakes are made by renaming and shortening the jpg and mp3 files down to one word. Such as: Leila.jpg and tear.mp3 then inserting that into the code instead of trying to type or copy/paste the whole file name with all the proper underscoring and such.

---

