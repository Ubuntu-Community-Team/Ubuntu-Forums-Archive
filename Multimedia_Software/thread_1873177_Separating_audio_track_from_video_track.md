---
title: "Separating audio track from video track"
date: 2011-10-31
forum: Multimedia Software
---

### Post by Pat201 on 2011-10-31
I took some video with my camera and want to save only the audio track as an MP3 or whatever.  I'm using OpenShot, but the only thing I've been able to come up with is turning off the video channel but I can still only save it as basically a video with no video, just audio.  I want to separate the two and JUST save the audio.  Any ideas?  Thanks.

Pat

---

### Post by andrew.46 on 2011-11-01
> **Pat201 said:**
> I took some video with my camera and want to save only the audio track as an MP3 or whatever.

Are you happy with the commandline? If so FFmpeg would be a great tool for the job. Some details here on installing a decent copy of FFmpeg:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg 
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then if you could post the results of:

```
ffmpeg -i *my_movie_file*
```

where 'my_movie_file' is the actual name of your file it would be a simple matter to demonstrate the required syntax...

---

### Post by leunam12 on 2011-11-01
after installing ffmpeg, install winff which is a graphical user interface for ffmpeg. It works fine for me. 

I wonder if the RealPlayer converter would run in ubuntu. hmm... worth a try.

---

### Post by aeiah on 2011-11-01
id use avidemux, but i guess if winff has a preset for it then that'll work fine. if you're going to be doing it regularly then an ffmpeg command would be more convenient of course. both winff and avidemux use ffmpeg iirc

---

### Post by Pat201 on 2011-11-01
I don't know anything about the Linux command line.  I was a DOS fiend and was more comfortable moving around under Windows at the command line than with the desktop, but alas..... I'm a Linux newb. :)  I found a link with how to do it with Mplayer, but when I did it, it said Mplayer was not installed although I have Movie Player installed.  Is that a different program?  Is Mplayer command line and MP graphical? I'll give it a shot and see what I come up with and let y'all know.  Thanks guys!

---

### Post by enkay009 on 2011-11-01
> **Pat201 said:**
> it said Mplayer was not installed although I have Movie Player installed.  Is that a different program?  Is Mplayer command line and MP graphical?

That's right. mplayer and movie player are two different beasts. There are flavors of mplayer with a graphical interface that allows you to queue up files, change settings on the fly, etc. For example gnome-mplayer, gmplayer, and smplayer.

However to dump audio, you don't need the gui flavors of mplayer.

---

