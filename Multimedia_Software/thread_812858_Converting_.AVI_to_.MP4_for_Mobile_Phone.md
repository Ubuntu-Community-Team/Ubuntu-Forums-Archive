---
title: "Converting .AVI to .MP4 for Mobile Phone"
date: 2008-05-30
forum: Multimedia Software
---

### Post by uheaven on 2008-05-30
Hey there, i want to convert some episodes of Hannah Montana from .AVIs to .MP4s for my mobile which uses 176x144 MP4s.. Any quik and easy ways to do this... A bit advanced also accepted.. I need to have this doen by tonight so i can show the episodes to my frnds

---

### Post by FakeOutdoorsman on 2008-05-30
You can try ffmpeg if you like command-line.  [WinFF]("http://www.winff.org/") is a good ffmpeg GUI.  There is also [Fuoco Tools]("http://ubuntuforums.org/showthread.php?t=652843").

The version of ffmpeg in the Ubuntu repositories has not been compiled with support for restricted formats (mp3, aac, etc), so you may want to use the [Medibuntu]("http://medibuntu.org") repository to get a version that has been compiled to support restricted formats.

Here is a basic ffmpeg command (change bitrate to whatever you want):
```
ffmpeg -i inputvideo.avi -b 500k -s 176x144 outputvideo.mp4
```

Another with more quality parameters and two-passes:
```
ffmpeg -y -i inputvideo.avi -b 500k -s 176x144 -mbd rd -flags +4mv+trell+aic -cmp 2 -subcmp 2 -g 300 -f mp4 -pass 1 /dev/null && ffmpeg -i inputvideo.avi -b 500k -s 176x144 -mbd rd -flags +4mv+trell+aic -cmp 2 -subcmp 2 -g 300 -f mp4 -pass 2 outputvideo.mp4
```

---

### Post by xjgnsdof on 2008-05-30
I use podencoder, which you can install through Synaptic or from the command line, as follows:

```
sudo apt-get install podencoder
```

To convert the video, from the command line, navigate to the directory containing the video and run podencoder as follows (replacing input.avi and output.mp4 as appropriate):

```
podencoder input.avi output.mp4
```

---

### Post by fickenbaisage on 2008-05-30
If you are a new linux user you may want to try a program with graphical interface as opposed to using the command line (which can get extremely tedious when it comes to converting multiple video files).

WinFF is a good program to use. Use the following guide to install:

[http://tombuntu.com/index.php/2008/05/22/easily-convert-videos-with-winff-and-ffmpeg/](http://tombuntu.com/index.php/2008/05/22/easily-convert-videos-with-winff-and-ffmpeg/)

---

### Post by FakeOutdoorsman on 2008-05-30
> **fickenbaisage said:**
> If you are a new linux user you may want to try a program with graphical interface as opposed to using the command line (which can get extremely tedious when it comes to converting multiple video files)
...

I disagree.  The command-line does not have to be tedious.  Multiple files can be easily encoded with a single batch-type command:
```
find ~/ -name "*.avi" -type f -exec ffmpeg -i {} -b 500k -s 176x144 outputvideo.mp4 \;
```

---

### Post by JEDIDIAH on 2008-05-30
> **fickenbaisage said:**
> If you are a new linux user you may want to try a program with graphical interface as opposed to using the command line (which can get extremely tedious when it comes to converting multiple video files).

WinFF is a good program to use. Use the following guide to install:

[http://tombuntu.com/index.php/2008/05/22/easily-convert-videos-with-winff-and-ffmpeg/](http://tombuntu.com/index.php/2008/05/22/easily-convert-videos-with-winff-and-ffmpeg/)

pppffft... This is what scripts and aliases are for.

There's really no need to subject yourself to the commandline arguments
for any given tool more than once. With some of these codecs, they are
just plain complicated regardless of what UI you're using. There are a
lot of obscure sounding options to keep track of.

The trick to getting video to work with any particular device is figuring
out what the compatable options are. If you luck out, then defaults might
be good enough.

Archos does well with default divx and x264 options.

---

### Post by S3loth on 2008-05-30
> **FakeOutdoorsman said:**
> You can try ffmpeg if you like command-line.  [WinFF]("http://www.winff.org/") is a good ffmpeg GUI.  There is also [Fuoco Tools]("http://ubuntuforums.org/showthread.php?t=652843").

The version of ffmpeg in the Ubuntu repositories has not been compiled with support for restricted formats (mp3, aac, etc), so you may want to use the [Medibuntu]("http://medibuntu.org") repository to get a version that has been compiled to support restricted formats.

Here is a basic ffmpeg command (change bitrate to whatever you want):
```
ffmpeg -i inputvideo.avi -b 500k -s 176x144 outputvideo.mp4
```

Another with more quality parameters and two-passes:
```
ffmpeg -y -i inputvideo.avi -b 500k -s 176x144 -mbd rd -flags +4mv+trell+aic -cmp 2 -subcmp 2 -g 300 -f mp4 -pass 1 /dev/null && ffmpeg -i inputvideo.avi -b 500k -s 176x144 -mbd rd -flags +4mv+trell+aic -cmp 2 -subcmp 2 -g 300 -f mp4 -pass 2 outputvideo.mp4
```

When I do that the video comes out fine, but there is no audio. (btw I am using mpg not avi)

---

### Post by S3loth on 2008-05-30
Woah, hold on. I'm having multiple audio problems, seems to be a problem with my computer, not the audio.

---

