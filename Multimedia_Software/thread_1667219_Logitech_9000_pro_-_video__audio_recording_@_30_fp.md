---
title: "Logitech 9000 pro - video / audio recording @ 30 fps"
date: 2011-01-14
forum: Multimedia Software
---

### Post by Silvernail on 2011-01-14
Can I run this camera:
> Bus 001 Device 007: ID 046d:0809 Logitech, Inc
as something other than a UVC driven camera?

It appears that UVC in 640x480 format is only available at 15 fps. I need to record at  fps=30. So I can splice into existing video.

```
#!/bin/bash
##Turn on webcam and save video and audio output to file.

# check if there is no command line argument
if [ $# -eq 0 ]
then
echo "You forgot to name the output file!"
echo "Usage :: webcam-capture name of output file"
exit
fi

name=$1;


mencoder -tv fps=30:driver=v4l2:buffersize=256:norm=NTSC:input=0:volume=40:amode=1:quality=100:width=640:height=480:device=/dev/video0:adevice=/dev/dsp1:audiorate=44100:immediatemode=0:forceaudio tv:// -o "$name".avi -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=490:keyint=18 -ofps 30 -vf lavcdeint -oac mp3lame -lameopts cbr:br=96:mode=0 -noskip


echo "Recording. Ctrl-C or close window to stop"
```

Is there a driver other than 'v4l2' I can use that will give me 30 frames per second?

---

### Post by Silvernail on 2011-01-17
Further search and read has led me to the reason for the low FPS on the webcam.  Everything states that the UVC is capible of 30 fps. What it doesn't tell you is that the fps speed is determined by the exposure.

The less light the longer it takes the camera to correct and compress the image.  The solution is to turn off automatic exposure. That can drastically affect image quality, but it does speed up fps.

---

