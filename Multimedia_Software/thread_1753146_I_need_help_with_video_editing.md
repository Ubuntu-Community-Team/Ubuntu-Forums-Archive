---
title: "I need help with video editing"
date: 2011-05-08
forum: Multimedia Software
---

### Post by ChaosChris2009 on 2011-05-08
[CENTER]I'm looking for a video editor that will allow me to easily apply album covers to songs.

So I want the album cover picture to show while the whole song is playing the video ends.

Something like this

```
http://youtu.be/866Iur9kpkc
```

These are the video editors I have: Kdenlive, OpenShot, and Pitivi Video Editor. I'm on Natty.

I'd really appreciate help.[/CENTER]

---

### Post by ron999 on 2011-05-08
Hi
You don't need to use a video editor for this.
**FFmpeg** will do the job. It's easier.:)

You need your album cover **picture.jpg** file.
And your **song.mp3** file.

Then use a command like this:-
```
ffmpeg -loop_input -i picture.jpg -i song.mp3 -shortest -b 1000k -acodec copy movie.mp4
```

---

### Post by ChaosChris2009 on 2011-05-08
> **ron999 said:**
> Hi
You don't need to use a video editor for this.
**FFmpeg** will do the job. It's easier.:)

You need your album cover **picture.jpg** file.
And your **song.mp3** file.

Then use a command like this:-
```
ffmpeg -loop_input -i picture.jpg -i song.mp3 -shortest -b 1000k -acodec copy movie.mp4
```

Do I need the latest version of FFmpeg?

Cause the one I'm getting from Software Center is 4:0.6.2

And is it possible to have it output as .avi?

---

### Post by ChaosChris2009 on 2011-05-08
Any other solutions besides FFmpeg?

---

### Post by FakeOutdoorsman on 2011-05-09
> **ChaosChris2009 said:**
> Do I need the latest version of FFmpeg?
No, but you may need to enable some additional encoders depending on what output format you want. See:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

> **ChaosChris2009 said:**
> And is it possible to have it output as .avi?
Yes, but why do you want avi? It's an outdated container format and doesn't have many advantages over more modern formats.

> **ChaosChris2009 said:**
> Any other solutions besides FFmpeg?
FFmpeg isn't the only solution, but it's probably the best.

---

