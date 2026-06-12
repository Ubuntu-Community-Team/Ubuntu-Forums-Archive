---
title: "avidemux , no sound"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by joriad on 2007-06-11
I have been trying to convert avi files into mpeg files so that I can put them onto a dvd. I was using devede at first but noticed some quality problems in the end file that was created (distortion). I have tried avidemux and have been able to convert the video but I cannot seem to get any audio. Is there a way that i can get the audio working with this program, or is there yet another program I can use to convert avi files to something that can be used for dvd players. I am looking for something that will result in excellent quality in both the video and audio segments of the file.

---

### Post by joriad on 2007-06-13
Anyone have any ideas?

---

### Post by Gwasanaethau on 2007-06-13
Hi there,

In the terminal, you can use a command like:
```
ffmpeg -i input.avi -target pal-dvd dvd.mpg
```
to convert the input video into one fit for a DVD. You may need to change the bit that says 'pal' into 'ntsc' if this is appropriate to your region (e.g. North America, etc.)

EDIT: If you get something that like 'command not recognised' or equivalent, you will probably need to install 'ffmpeg' from the repositories first. You can do this by using the command:
```
sudo apt-get install ffmpeg
```

---

### Post by joriad on 2007-06-13
Thanks, that worked great.

---

### Post by Gwasanaethau on 2007-06-13
> **joriad said:**
> Thanks, that worked great.

You're very welcome! ;) All the best with it now!

---

### Post by niceguy123 on 2008-01-17
> **joriad said:**
> I have been trying to convert avi files into mpeg files so that I can put them onto a dvd. I was using devede at first but noticed some quality problems in the end file that was created (distortion). I have tried avidemux and have been able to convert the video but I cannot seem to get any audio. Is there a way that i can get the audio working with this program, 


Have you or can someone else tell me how to resolve the no sound problem.

---

### Post by GeBo on 2008-01-28
From the avidemux.org website:

> MPEG files

If you use MPEG A+V (PS) as the output format, you will end up with a VCD, SVCD or DVD stream. Of course the audio must also be suitable for SVCD/VCD/DVD use. Avidemux is now using libmplex for maximum compliance.

If you use MPEG video as the output format, only the raw video elementary stream will be saved. That means there will be no audio and that it is not suitable for VCD/SVCD/DVD authoring. You have to save the audio only (using Audio->Save) and use mplex or tcmplex to rebuild an MPEG PS stream. 

Maybe you've chosen the wrong format?

---

### Post by benrboone on 2008-04-04
thanks I was using the wrong sound format

---

