---
title: "[SOLVED] pulse audio support for adobe flash latest version 10.0.12.36"
date: 2008-11-27
forum: Multimedia Software
---

### Post by spandanj on 2008-11-27
Adobe flash player 10 in ubuntu 8.04 does not show up as a stream in pulse's PAVUCONTROL. how can I make adobe flash player 10 to use pulse?


Currently, sometimes there is no sound in flash videos in firefox if I am also using banshee. So, I think there is a conflict there...

Finally, i don't get why this has to be complicated and confusing -- a simple a thing as "audio" in an operating system!!! There's alsa, then pulse.....urgh....Just make it work. I don't want to deal with so much configuration.

in summary, how do i get adobe flash 10 to use pulse audio.

---

### Post by spandanj on 2008-11-30
Still no audio in flash player 10 in firefox, if I have banshee running first.

any solution? In fact, are Ubuntu devs going to release any major update to consolidate alsa and pulse....so i don't have to deal with such conflicts...

---

### Post by markbuntu on 2008-11-30
Try this:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by spandanj on 2008-12-01
> **markbuntu said:**
> Try this:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

ok. I did what it said in your post. It worked!!!. Now flash 10 in firefox IS USING pulse as evidenced by a stream in pavucontrol:

ALSA plug-in [firefox]: ALSA playback.

THank you!!!


However, I have two questions:

1) the flash player in firefox has a very low volume even though it's (stream) volume is set too 100% in pavucontrol. While, simultaneously the banshee stream gives me a good volume at 100% in pavucontrol. I have set my sound card volume to max using the volume applet in gnome bar
2) WHY do I (...the user) have to take so just to set up audio properly????? It's annoying have to configure so many things in my fresh install. Sound is just one of them. Why can't the ubuntu devs just make it work??? I am on ubuntu 8.04. 


I hope this configuration will last a few months without breaking...although even as right now, its not perfect, because my overall volume in my headphones has reduced very much even after setting all volume settings to max and configuring the system as your post suggests.

---

