---
title: "Avidemux: converting from .avi to .mp4"
date: 2009-10-18
forum: Multimedia Software
---

### Post by hooless on 2009-10-18
Hey all, I have been having troubles trying to convert a certain avi file on my computer to the format used by the iPod so I can put it on there. ive searched quite a bit, but none seem to be very helpful. anyways, how exactly do I use avidemux to convert from avi to mp4 (i think thats the right file.)?

ps, the 'auto' thing on the menu bar keeps saying 'Cannot select the MPEG-4 SP codec.' so that would help me a lot to know what that means... thanks all!

---

### Post by duanedesign on 2009-10-18
If you dont get Avidemux working, here are some alternative methods.

**Winff**
In the Terminal run:

```
sudo apt-get install ffmpeg winff
```

> WinFF is probably the most user-friendly tool for converting videos and extracting audio from videos in GNU/Linux. Avidemux is a popular and useful video editing application, which makes it quite simple to cut and crop videos to your liking, and much more.

Tip: To make a video for a mobile phone in WinFF, select 3g2 as the type of video you want to make, but change the extension from ".3g2" to ".mp4" when the video is complete. To increase the audio quality of the video, click on "Options" within WinFF, and in the option labelled "Audio Bitrate", type "96000" (default is 64000, which is 64kbps). However, your phone may not play it properly with the audio at 96kbps, depends really. Test it yourself.

**Just plain FFMPEG**
[Enable Medibuntu repository. ]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")
In a Terminal run:
```
sudo apt-get install ffmpeg
```
Download this script and save it to /tmp
[pypodconv]("http://web.mit.edu/~jdong/www/pypodconv/pypodconv")

In a Terminal run these three (3) commands one at a time.
```
sudo apt-get install gpac

sudo mv /tmp/pypodconv /usr/local/bin/pypodconv

sudo chmod +x /usr/local/bin/pypodconv
```

Then the command to convert the video would be:
```
pypodconv -i INPUT_FILE -o OUTPUT_FILE
```

This by defaults to a 200kbit/s 320xNNN 2-pass H.264 video, for iPod viewing. If you want to make 500kbit high-definition encodes:

```
pypodconv -i INPUT_FILE -o OUTPUT_FILE --hd -b 500
```

---

### Post by duanedesign on 2009-10-18
You might also try the Unix-like channel on the [Avidemux Forums]("http://avidemux.org/admForum/viewforum.php?id=20").

Good Luck :)

---

### Post by FakeOutdoorsman on 2009-10-18
> **duanedesign said:**
> ...
**Just plain FFMPEG**
[Enable Medibuntu repository. ]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f")
In a Terminal run:
```
sudo apt-get install ffmpeg
```
...

Medibuntu only offers FFmpeg for Ubuntu Hardy Heron.  Newer versions of Ubuntu have other options:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

If you're going to encode often, then I recommend compiling your own FFmpeg.  Development of FFmpeg is incredibly active and by compiling it yourself you can take advantage of bug fixes and new features such as the iPod preset for the H.264 encoder (libx264).  Easy to follow instructions to compile are linked to in the URL above.  Here's an example command using a recent FFmpeg:

```
ffmpeg -i input.avi -acodec libfaac -ac 2 -ab 128k -vcodec libx264 -vpre hq -vpre ipod640 -s 640x480 -crf 26 -threads 0 output.mp4
```

---

### Post by 1/0 on 2009-12-12
Any solution to this? I'm running Karmic and I have the exact same problem...

---

### Post by beowulf62381 on 2009-12-15
Posted by Whaevr on [avidemux fourms]("http://avidemux.org/admForum/viewtopic.php?id=6931")

"This is an issue with the gtk interface, use the qt interface and it'll work fine."

---

### Post by WadeH2o on 2010-04-06
> **beowulf62381 said:**
> Posted by Whaevr on [avidemux fourms]("http://avidemux.org/admForum/viewtopic.php?id=6931")

"This is an issue with the gtk interface, use the qt interface and it'll work fine."

NICE! Thank you!:popcorn:

---

### Post by floorripper on 2012-10-05
Hello I have found out that Avidemux GTK+ does not work with the I pod,

I have used this instead:

```
apt install avidemux-qt
```

and this guide:
[http://www.linuxondesktop.in/2008/05/converting-and-transferring-audiovideo.html](http://www.linuxondesktop.in/2008/05/converting-and-transferring-audiovideo.html)

---

