---
title: "LiVES in Gutsy 64"
date: 2007-12-18
forum: Multimedia Production
---

### Post by myonta on 2007-12-18
Well, I've been using Ubuntu for a few months now and this is my first post on the forums. Usually, anything I need to do/fix/figure out is already on here in detail.

So, I'm having terrible luck with video editing software. Pitivi doesn't have enough features, Kino doesn't like anything but raw DV, Cinelerra is plain confusing (and the audio isn't working anyway), etc.

LiVES seems to have a lot of potential and looks like right about the technical and features level I'm looking for. However, it wont work for me. It seems to be some error with JACK (of which I know little about). I tried JACK control, but I have no idea what I'm doing.

Here's the terminal readout when I attempt to run LiVES (ver. 0.9.8.6; a 64 package I found on getdeb.net):


```

LiVES 0.9.8.6
Copyright 2002-2007 Gabriel Finch (salsaman@xs4all.nl) and others.
LiVES comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details.

JACK tmpdir identified as [/dev/shm]
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns

JACK tmpdir identified as [/dev/shm]
JACK tmpdir identified as [/dev/shm]
JACK tmpdir identified as [/dev/shm]
JACK tmpdir identified as [/dev/shm]
JACK tmpdir identified as [/dev/shm]...
```*...ad infinitum*
Let me know.
Thanks,
~Jon

---

### Post by dad311 on 2007-12-18
Jon, I dont know much abount Lives, but Ive had success with Cinelerra on my AMD64.   

I used Kino and Cinelerra to edit lots home movies.  Cinelerra has a sharp learning curve, but works well.

Ive pasted some links below that might help you.  The first link is how to install Cinelerra, it very easy just enable some repositories and use apt-get.   The second link is a how-to that I found very helpful in learning Cinelerra.

[http://cvs.cinelerra.org/getting_cinelerra.php](http://cvs.cinelerra.org/getting_cinelerra.php)

[http://www.robfisher.net/video/cinelerra1.html](http://www.robfisher.net/video/cinelerra1.html)

---

### Post by eye208 on 2007-12-19
> **myonta said:**
> Pitivi doesn't have enough features, Kino doesn't like anything but raw DV, Cinelerra is plain confusing (and the audio isn't working anyway), etc.
You might want to check out Blender. Although it's best-known for being a 3D modelling/rendering app, it includes a fully featured video editor and compositing system. It integrates FFMPEG so you can import almost any video file type. It has lots of effects, and if these are not enough you can harness its powerful 3D engine. For example you can use videos as textures on 3D objects. Imagine video smoothly rotating and zooming in 3D space, customized intros and end credits (e.g. Star Wars style etc.), video on particles or fluids, lens flares etc.

---

### Post by salsaman on 2007-12-19
This means that some other application is using your soundcard and blocking it. You need to find out which application and stop it.

Alternately you can start LiVES with:

lives -aplayer sox -jackopts 0

however doing this will result in reduced audio functionality within LiVES.


- Salsaman.

---

### Post by myonta on 2007-12-20
Salsaman:
How about that. You set me on the right track.  RhythmBox was running in the background. I shut it off and *presto, LiVES is up and running.

dad311:
I'll take another crack at Cinelerra-thanks for the tutorial link.

eye208:
I didn't know that Blender could edit video, though I'm pretty sure Blender's learning curve is even steeper than Cinelerra. Either way, though, I'll check it out.

Thanks guys,
~Jon

---

