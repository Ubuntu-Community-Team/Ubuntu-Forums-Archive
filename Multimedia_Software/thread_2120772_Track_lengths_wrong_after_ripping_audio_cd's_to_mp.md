---
title: "Track lengths wrong after ripping audio cd's to mp3"
date: 2013-02-27
forum: Multimedia Software
---

### Post by schallertg on 2013-02-27
When ripping audio cd's to mp3 the track lengths are ridiculously long.  I.e. a 4:55 track ends up being 25:10.  The track plays normally it's just the file has 20 minutes of empty silence at the end.  All cd's do it and I've tried the following apps with the same result:

Sound Juicer
Rhythmbox
Asunder CD ripper

Even installed k3b and that does it as well.  I searched these forums for similar problem and nothing came back in results.  Any ideas?

System
------------
12.04 64 bit
lame installed (Asunder needed it)

---

### Post by Merrattic on 2013-02-27
It is probably the underlying libraries and binaries being used to do the mp3 conversion. You can replicate this if you try to convert a sound file to mp3 using avconv directly off the cli (the ubuntu replacement for ffmpeg).

If you compile "real" ffmpeg, the problem will go away.

Not sure if you have the same problem, but this was the case for me.

---

### Post by schallertg on 2013-02-27
Thanks for the reply.... I was googling and found (via the Audacity forums) that it had to do with variable bit rate so I just tried Asunder again and turned off VBR in the Advanced settings and the track length was correct for the one I tested.  I think that must be it but I have no idea if Sound Juicer has advanced settings.  Will just use Asunder as default cd ripper.  Thank you, will look into your suggestion as well.  :)

---

