---
title: "How To Add Video To iPod Classic"
date: 2013-06-30
forum: Multimedia Software
---

### Post by CrystalDreamer59 on 2013-06-30
I just got myself a 160GB iPod classic and I'm just curious how to get video onto it. I tried adding a m4v video file to banshee but when I tried syncing the video to my iPod in banshee I get an error message saying something like the file is not supported on the device and that it couldn't be converted. What should I try to do. By the way I'm using the latest version of Ubuntu, which is 13.04. I've tried gtkpod too but when I sync a movie it ends up in my music as an audio.

---

### Post by coldraven on 2013-06-30
Have a look at Arista Transcoder, it has pre-sets for iPods etc. and you can download or create more.
[http://www.transcoder.org/](http://www.transcoder.org/)

---

### Post by CrystalDreamer59 on 2013-06-30
I downloaded arista and converted an avi video to the preset for iPod classic, which turned out to be m4v. I then added the converted m4v file to banshee and synced it to my iPod classic and I still got the same error message.

---

### Post by coldraven on 2013-07-01
Sorry I cannot help any more because I don't have an iPod. Hopefully someone else will reply.
The only thing that I can think of is that 13.04 does not have ffmpeg, it uses avconv instead.

---

### Post by CrystalDreamer59 on 2013-07-01
I added ffmpeg and I still got the error message when I tried to add an m4v file to my ipod using banshee. If you don't use an iPod what mp3 player do you use to listen to music. Perhaps I should try something other then an iPod.

---

### Post by coldraven on 2013-07-03
> **CrystalDreamer59 said:**
>  If you don't use an iPod what mp3 player do you use to listen to music.
The only mp3 player I have is in my phone but I don't use it. (a basic Nokia C1-01)
 I never got into the habit of wandering around with headphones on, I prefer to hear my surroundings.
At home I listen to the radio, internet radio or CDs. Call me old fashioned :)
I'm surprised that no-one else has responded to your problem, this should bump you the top again!

---

### Post by FakeOutdoorsman on 2013-07-03
I don't have one of these devices, but you can try this:

```
ffmpeg -i input -vf "scale=320:trunc(ow/a/2)*2,format=yuv420p" -codec:v libx264 -preset fast -profile:v baseline -level 13 -crf 28 -codec:a aac -b:a 128k -strict experimental -metadata title="1984 Bonk-the-Weasel Idaho State Tournament" output.mp4
```

You can change "320" to "640" if you plan on connecting the iPod to an external device like a TV to view the video. Control encoding speed with "-preset" and quality with "-crf" as shown at the [FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide), and of course you can change the title or omit that.

This example probably uses more recent syntax for the so-called "ffmpeg" package in the repository, but you can easily use a [ffmpeg build](http://ffmpeg.org/download.html#LinuxBuilds) (just download, extract, and run [[instructions](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453)]) or follow a step-by-step [guide to compile ffmpeg](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide).

---

### Post by coldraven on 2013-07-03
> 1984 Bonk-the-Weasel Idaho State Tournament
Hey Fakeoutdoorsman, I think your copy/paste window was too short! LOL
Now that you have changed avatar what was that guy holding? A quadrophonic decoder?

---

### Post by FakeOutdoorsman on 2013-07-03
Now I remember is was actually called "Whac-a-Mole", not "Bonk-the-Weasel".

I believe it was a VCR.

---

