---
title: "i don't &quot;get&quot; jackd"
date: 2008-10-29
forum: Multimedia Software
---

### Post by bolex100 on 2008-10-29
I installed rosegarden but it needed to run Jack Server first. Ok did that, and now it needs Sox or Sndfile-resample ... which i don't know how to do.

But before I go on, there is something I want to understand. Having run Jack, all the other sound is dead.  Is that something that I'm going to have to live with (Rosegarden OR everything else) or can i wire it all through Jack.  The trouble is, I dont know what I should be connecting to what.  At the moment I'm on ALSA or autodetect.  Jack isn't an option.  So how does it all work?

---

### Post by markbuntu on 2008-10-29
Jack is an entirely separate thing. It was made for one thing and one thing only, to facilitate professional quality recording in linux. As such, it directly uses the hardware drivers to reduce latency and will shut out all other applications that seek to use the hardware. But, and there are always buts, there are ways around this which basically consists of hooking a sound server like alsa or pulseaudio into jack.

If you go here, you can find information and links to how this all works and how you can get your other applications working when you are using jack among (many) other things. The guide is very very long but covers just about everything you need to know about sound in ubuntu/linux if you read it and follow the links. I call it the 10,000 page guide.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

