---
title: "a question about ffmpeg and desktop video and sound capture"
date: 2010-09-27
forum: Multimedia Software
---

### Post by shantiq on 2010-09-27
ok trying to get a good video and sound desktop capture with this


```
ffmpeg -f alsa -ac 2  -ab 128k  -i hw:0,0 -f x11grab -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -r 30 -qscale 1  -i :0.0   -f avi ./Desktop/mydesktop.avi
```


and perfect image/video capture but the sound does not play back


any ideas why not?    got some of the ideas from [here]("http://www.math-linux.com/spip.php?article97")

i am using an alpha lexicon box for my sound system-wide on my machine

---

### Post by ron999 on 2010-09-27
Hi
The tutorial that you used only describes how to capture video.
There's a better tutorial here:-[http://ubuntuforums.org/showthread.php?t=1392026]("http://ubuntuforums.org/showthread.php?t=1392026")
It captures raw video and pcm audio which is very easy to convert afterwards.
It works OK for me.
You'll probably get support there if you need help.

---

### Post by shantiq on 2010-09-28
> **ron999 said:**
> Hi
The tutorial that you used only describes how to capture video.
There's a better tutorial here:-[http://ubuntuforums.org/showthread.php?t=1392026]("http://ubuntuforums.org/showthread.php?t=1392026")
It captures raw video and pcm audio which is very easy to convert afterwards.
It works OK for me.
You'll probably get support there if you need help.


cheers Ron will check that


it really works it is a great guide/tip

i modified it slightly so it leaves the recorded video file on desktop



```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 ./Desktop/mydesktop.mkv
```

---

### Post by shantiq on 2010-09-29
and for a good webcam plus voice grab



with help [from Verb]("http://ubuntuforums.org/showpost.php?p=9904875&postcount=85")


i use this which really roks too


```
ffmpeg -f alsa -ac 2 -i pulse  -f video4linux2 -i /dev/video0 -acodec pcm_s16le  -vpre lossless_ultrafast -threads 0 -s 320x240   -r 30    ./Desktop/mywebcam.avi
```AND just record your voice with a microphone to a wave file


```
ffmpeg -f alsa -ac 2 -i pulse   -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0  -y  ./Desktop/myVOICE.wav
```

---

### Post by shantiq on 2010-10-01
AND just record your voice with a microphone to an alac file


```
ffmpeg -f alsa -ac 2 -i pulse -acodec alac  -y ./Desktop/RecordingMYvoice.m4a
```



to flac


```
ffmpeg -f alsa -ac 2 -i pulse -acodec flac  -y ./Desktop/RecordingMYvoice.flac

```


to aac


```
ffmpeg -f alsa -ac 2 -i pulse -acodec aac -strict experimental -ab 399k  -y ./Desktop/RecordingMYvoice.aac
```

---

### Post by shantiq on 2010-11-10
---deleted---

---

### Post by shantiq on 2011-01-30
also if you wish for an **HD 1080p** grab of desktop + microphone recording


having made sure your system/nvidia settings are set on 1920x1080

ie    system/admin/nvdia X server settings  /resolution/pick 1920/apply   



run

```

ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 35 -s hd1080 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0   -y  ./Desktop/Mydesktop.mkv
```

---

### Post by shantiq on 2011-03-20
if you want to grab your desktop and desktop sound (music/video) instead 

use the same code line

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1280x1024 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0   -y ./Desktop/mydesktop.mkv
```


**but** to make sure your mike is not picked up instead you need to do this



> +  Q: How can I control PulseAudio input? (e.g. capture application audio instead of mic)
A: Install “pavucontrol“. Start recording with ffmpeg. Start pavucontrol. Go to the “Recording” tab and you’ll find ffmpeg listed there. Change audio capture from “Internal Audio Analog Stereo” to “Monitor of Internal Audio Analog Stereo“.
Now it should record system and application audio instead of microphone.


```
sudo apt-get install pavucontrol

```

from [verb]("http://ubuntuforums.org/showthread.php?t=1392026")

---

### Post by rulet on 2011-10-01
I used f.e. this command

```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 30 -s 1024x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 1.mkv
```

 But I've got audio delay in recorded video in about 2sec. What I have to put in this command that audio delay disappeared?

---

