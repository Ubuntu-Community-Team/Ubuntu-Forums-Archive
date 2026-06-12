---
title: "Logitech 9000 pro - video / audio recording."
date: 2011-01-11
forum: Multimedia Software
---

### Post by Silvernail on 2011-01-11
I have a Logitech webcam that I want to use to video the questions from the audience during a demonstration.  Another video camera will be focused on the main event.

I am using this script to record both video/audio.

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


mencoder tv:// -tv driver=v4l2:norm=NTSC-M:audiorate=48000:immediatemode=0:device=/dev/video0:forceaudio:adevice=/dev/dsp1 -o "$name".avi lavc -lavcopts vcodec=mjpeg:aspect=4/3 -aspect 4:3 -noautoexpand -oac lavc -ovc copy

echo "Recording. Ctrl-C or close window to stop"

```

The sound is weak. I have 'alsamixer' set as high as it will go.
I have the volume control on my keyboard set as high as it will go.
And I have the volume all the way up on my speekers.

Is there somewhere else that I can look that might be affecting the volume.  Other programs give me a  louder volume.

TIA
Dave

---

### Post by no2498 on 2011-01-12
do you not need to set the input volume
 an not the output ?

---

### Post by Silvernail on 2011-01-12
You are correct, it needs to be the input.
I was trying to imply that I have set everything I can find/know of, to 100%.

Reading the dozen or so threads on this subject on this board, talked about muted this and muted that.

---

### Post by no2498 on 2011-01-12
in alsamixer did you set the mic
thinking its on the far right
is like 2 or 3 of them

---

### Post by Silvernail on 2011-01-12
Since I made my original post, I have fiddled with some other stuff.
Alsamixer has  everything set to 100%.
I made some adjustments to 'PulseAudioControls' and now have a very good sound level. At least something I can tone down.
[SIZE="1"]Except for waist lines, it is easier to take away than to add on.[/SIZE]
[COLOR="Red"]A new problem has developed.[/COLOR]
I now have a very loud back ground noise that sounds like a motor running.
Any ideas where that might have come from.

---

### Post by Silvernail on 2011-01-14
I am going to mark this thread abandoned because there are too many apps to control the sound and my problem seem to have gone away. Also a new problem has arisen. I will start a new thread.

---

### Post by Silvernail on 2011-01-17
Further search and read has led me to the reason for the low FPS on the webcam.  Everything states that the UVC is capible of 30 fps. What it doesn't tell you is that the fps speed is determined by the exposure.

The less light the longer it takes the camera to correct and compress the image.  The solution is to turn off automatic exposure. That can drastically affect image quality, but it does speed up fps.

---

