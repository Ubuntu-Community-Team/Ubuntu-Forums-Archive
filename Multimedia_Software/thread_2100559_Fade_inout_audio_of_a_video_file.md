---
title: "Fade in/out audio of a video file"
date: 2013-01-02
forum: Multimedia Software
---

### Post by DrPL on 2013-01-02
Hello,
I have a couple of video files that I am trying to fade-in at the beginning and fade out at the end. I have used Avidemux and managed to get the images to do this but the audio won't. Someone suggested using OpenShot but it crashes on my computer.

Can anyone suggest an application, or even a command line tool that will apply a fade-in/out over a set time period for the audio element of a video file?

Many thanks

Paul

---

### Post by neu2buntu on 2013-01-02
Pitivi is capable of doing this as the video and audio are seperated, so you can infact have different fade in/out lengths for both video and audio ( i have problems rendering in ubuntu 12.04 tho, think it is a library problem ) .. if you wanted to you could probably strip the audio out into a seperate file using ffmpeg, edit the fades with audacity and join the file back with ffmpeg, but someone with more knowledge using ffmpeg would need to help ;)

---

### Post by DrPL on 2013-01-02
Hi,
I've downloaded PiTiVi but am having trouble getting it to recognise my clips.
I saved them using Avidemux using the x264 video and AAC codec as *.mp4
files, and PiTiVi says it can recognise mpeg-4 formats but when I navigate to the correct folder, I can't see my clips.

Best wishes

Paul

---

### Post by neu2buntu on 2013-01-02
make sure you are using the "import files" option and not the "open" option, which opens actual saved pitivi projects that you have saved ;)

---

### Post by DrPL on 2013-01-02
I feel like a kob moment coming on (kob ="kick own backside", a common statement in our office).

PiTiVi works beautifully...but compared to Avidemux, the file outputs are double in size. Must be the codecs I chose...

---

### Post by neu2buntu on 2013-01-02
haha i get those "kob" moments on a regular basis too ;) good that pitivi did your job, yeah the whole audio and video codec thing is way over my head. remember to mark the post as solved as to help others that may have this problem...Happy New year ;)

---

