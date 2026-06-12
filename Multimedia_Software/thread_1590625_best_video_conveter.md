---
title: "best video conveter"
date: 2010-10-08
forum: Multimedia Software
---

### Post by gudurukarthik on 2010-10-08
hey can u pls suggest which is the best video coveter in ubuntu... basicall i like to convert all formates in to mp4 or iphone compatible

---

### Post by nothingspecial on 2010-10-08
The best video converter is ffmpeg but it is command line only.

There is a gui called winff

To do what you want to do though you will have to do this first

[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by hsoulen on 2010-10-08
> **gudurukarthik said:**
> hey can u pls suggest which is the best video coveter in ubuntu... basicall i like to convert all formates in to mp4 or iphone compatible

If you are specifically looking for mp4 and iPod/iPhone compatible profiles, there is no better than Handbrake.

I use the stebbins PPA: [https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots]("https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots")

Hank

---

### Post by mrebanza on 2010-10-08
I use Transmageddon . . . It's simple, lights weight and already in the ubuntu repos . . . and the logo is kick ***

:guitar: 

```
sudo apt-get install transmageddon
```

[IMG]http://thumbla.com.nyud.net/images/images/transmaged.jpg[/IMG]

---

### Post by hsoulen on 2010-10-08
> **mrebanza said:**
> I use Transmageddon . . . It's simple, lights weight and already in the ubuntu repos . . . and the logo is kick ***

Sweet. Never used Tranmageddon, looks awesome and will give it a try.

Reason I have stuck with Handbreak so long is the support for DVD structures, I usually use cli for transcoding video files but when it comes to ripping a DVD... Handbrake!

Hank

---

### Post by MichiganMan on 2010-10-10
Transmageddon is pretty nice, but it doesn't seem to support multi-core CPU encoding like Stebbins' Handbrake builds do.  For me that means the difference between five minutes with Handbrake on a 30 minute video and 22 minutes with Transmageddon.

---

### Post by inobe on 2010-10-10
if your not ripping anything winff will make use of ffmpeg.

it's a nice cross platform app [http://winff.org/html_new/](http://winff.org/html_new/)

---

### Post by MichiganMan on 2010-11-07
I will say that one significant thing Transmageddon has over Handbrake is that the authors of Handbrake have chosen to no longer support avi encoding and are quite obstinate about its obselescence as a standard, the abundance of media players chiefly supported only by avi notwithstanding.  So if I need to encode a file to play on my dvd player Transmageddon has it all over Handbrake.

---

### Post by andrew.46 on 2010-11-12
Hi MichiganMan,

> **MichiganMan said:**
> I will say that one significant thing Transmageddon has over Handbrake is that the authors of Handbrake have chosen to no longer support avi encoding and are quite obstinate about its obselescence as a standard, the abundance of media players chiefly supported only by avi notwithstanding.

It is interesting to read the [Handbrake developers' comments]("http://handbrake.fr/") on the avi issue:

> 
AVI: AVI is a rough beast. It is obsolete. It does not support modern container features like chapters, muxed-in subtitles, variable framerate video, or out of order frame display. Furthermore, HandBrake's AVI muxer is vanilla AVI 1.0 that doesn't even support large files. The code has not been actively maintained since 2005. Keeping it in the library while implementing new features means a very convoluted data pipeline, full of conditionals that make the code more difficult to read and maintain, and make output harder to predict. As such, it is now gone. It is not coming back, and good riddance.


Personally I agree with this completely, particularly if removing the code allows precious time to be spent developing code in different areas. I suspect that in time the avi container will go the way of the floppy disk, but in the meantime as you have found there are still some programs that support this old container...

Andrew

---

### Post by Amy_1990 on 2010-11-12
+1 for FFmpeg and winff.

---

### Post by BADGER.BRAD on 2010-11-12
Will any of these converters convert to Pal DVD ? So I get a full screen pic for UK use .

Many thanks all.

Brad

---

