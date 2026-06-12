---
title: "Does libao actually use /etc/libao.conf ?"
date: 2010-07-20
forum: Multimedia Software
---

### Post by stobor on 2010-07-20
I'm trying to get pianobar to play music through my nforce2's iec958 interface, but libao seems to be ignoring anything I put in /etc/libao.conf or ~/.libao.  I get no sound or errors no matter what i put in these config files (even if I put default_driver=asdsf, it should give me an error, right?).

I tried it out with mpg321 as well, I can make the output work the way I want with the -o and -a arguments, but if I leave these off to choose the libao defaults, I get no sound.

Does anyone actually use these config files?  is there a known bug or workaround?  I could probably easily fix pianobar to pass the correct options directly to the library, but it seems strange that ao doesn't work as advertised.

libao2 in Karmic.  Everything up to date as of this post.

---

