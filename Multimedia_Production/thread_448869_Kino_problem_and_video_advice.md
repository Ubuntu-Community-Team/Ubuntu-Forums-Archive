---
title: "Kino problem and video advice?"
date: 2007-05-19
forum: Multimedia Production
---

### Post by gpilkay on 2007-05-19
Hello!  I'm VERY new to both Linux and video editing.  Pathetic as this sound,s what I want to do is take random scenes from some DVD's I have, mix them with an MP3, and make an anime music video.

Now that I've alienated myself from everyone, I was wondering what I need to do this?  I've downloaded Audacity, Kino, Avidemux, and pitivi, which may be WAY too much overkill.  Should I cut some stuff?

And when I start Kino, I get this at the bottom:
WARNING: dv1394 kernel module not loaded or failure to read/write /dev/dv1394/0

I did search under synaptic for it but got nothing.

I'm running Ubuntu 7.04 for college, so I don't want to change to Ubuntu Studio, at least not till I finish Grad School and have more play-time.

Thanks!

---

### Post by Quicky on 2007-05-20
I can't be much help with most of this but I can tell you that the “dv1394 kernel module not loaded or failure to read/write /dev/dv1394/0” warning is because you do not have a camcorder switched on and plugged into a firewire port on your PC. Kino is primarily used to capture DV from camcorders and this warning will appear unless that is what you're doing. I don't believe that Kino can be used to rip scenes from DVDs but I'm happy to be corrected.

If you need to capture from a camcorder I recommend this thread [http://ubuntuforums.org/showthread.php?t=56468&highlight=raw1394]("http://ubuntuforums.org/showthread.php?t=56468&highlight=raw1394") although it may seem a little daunting for a new user.

---

### Post by cgbier on 2007-05-20
You'll need a DVD ripper for that case (haven't tried it yet, so it is just a guess) ..... However, the use might be illegal.

If your camera has A/V through you might be able to connect your DVD player to the camera and capture the DVD with Kino.

For editing, I wouldn't use PiTVi. Cinelerra is much better.... however video editing under LINUX is stillo in its infancy.

---

