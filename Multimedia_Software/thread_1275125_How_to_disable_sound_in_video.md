---
title: "How to disable sound in video?"
date: 2009-09-25
forum: Multimedia Software
---

### Post by Julita on 2009-09-25
Hello everyone! I have a video that needs to be muted. How is it possible to do it?

---

### Post by duanedesign on 2009-09-25
Are you talking about muting the sound while you are playing back the video. This can be accomplished with the volume applet in the Gnome Panel at the top of your screen.
Or are you meaning to take the sound out of the actual video file? For that you can use one of the video editors available for Ubuntu like PiTiVi.

---

### Post by Julita on 2009-09-25
I need to mute video permanently ;) I'll try PiTiVi! Thanks a bunch!

---

### Post by cgroza on 2009-09-25
Why mute video?

---

### Post by Julita on 2009-09-25
To make clips ;)

---

### Post by duanedesign on 2009-09-25
I just stumbled across another thread on this topic.

> Download Cinelerra.
When you import the video file into the editor, the audio tracks will be
separated out. You will be able to delete the audio tracks and render the video out to an .mpg file.

Open Movie Editor should also work.

This answer seemed to work well for individual who started the thread.

Good luck

---

### Post by FakeOutdoorsman on 2009-09-25
FFmpeg can simply copy and paste your video to another file with or without audio.  This can be done without re-encoding so it is very quick, and because it is a direct copy it preserves the quality of your video.  Here is an example of removing the audio out of a .mp4 file:
```
ffmpeg -i input.mp4 -vcodec copy -an output.mp4
```
The *-vcodec copy* option tells FFmpeg to copy the video stream.  The *-an* option tells FFmpeg to ignore the audio.

---

### Post by Julita on 2009-09-25
Thank you so much for your answers!!! I appreciate greatly your help!

---

### Post by sushant.d84 on 2011-03-25
):P


> **FakeOutdoorsman said:**
> FFmpeg can simply copy and paste your video to another file with or without audio.  This can be done without re-encoding so it is very quick, and because it is a direct copy it preserves the quality of your video.  Here is an example of removing the audio out of a .mp4 file:
```
ffmpeg -i input.mp4 -vcodec copy -an output.mp4
```The *-vcodec copy* option tells FFmpeg to copy the video stream.  The *-an* option tells FFmpeg to ignore the audio.



Thanks for this I used it and Solved my problem !

---

### Post by oxman on 2011-05-25
> **FakeOutdoorsman said:**
> etc

I just wanted to thank you for all of your ffmpeg advice FakeOutdoorsman. While sleuthing on the web for video/audio answers you consistently come up with elegant solutions. The above case scenario is an example. I searched high and low for a solution to a similar problem and bingo here you are again. You're an asset to the open source world.

Are there any good online resources to train the amateur ffmpeg user?

Stan

---

