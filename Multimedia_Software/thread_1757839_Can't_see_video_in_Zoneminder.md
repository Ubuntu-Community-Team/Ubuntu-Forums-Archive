---
title: "Can't see video in Zoneminder"
date: 2011-05-13
forum: Multimedia Software
---

### Post by Maheriano on 2011-05-13
I just installed/configured Apache and also installed/configured Zoneminder to the best of my knowledge. I know Apache is running because I can go to [http://localhost](http://localhost) and see the simple webpage I made. Zoneminder starts fine and I added a monitor (camera) but when I click Monitor-1 to try and view the camera, it gives me just a black box where I should see the video. I think I'm very close, what do I need to do? I confirmed that my webcam is attached to /dev/video0 which is what I have it set to in the Zoneminder options.

---

### Post by deadtom on 2011-06-04
I'm having this exact problem. Did you ever get it resolved?

---

### Post by no2498 on 2011-06-04
[http://www.zoneminder.com/forums/viewtopic.php?p=63801](http://www.zoneminder.com/forums/viewtopic.php?p=63801)


[http://www.zoneminder.com/wiki/index.php/Documentation](http://www.zoneminder.com/wiki/index.php/Documentation)


hope 1 of them helps

---

### Post by deadtom on 2011-06-04
No but thanks anyway.

---

### Post by no2498 on 2011-06-05
does your cam work in cheese
or try wxcam
[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

### Post by Maheriano on 2011-06-06
Yes I did get it fixed, sorry.
I ran a command to look at dev0 and output all the specifications of the camera hooked up to dev0 (I can't remember the command, but it's a common one, someone here should know it).
From that I saw that the colour palette used by the camera wasn't RGB, it was something weird like YVYF or something like that. Once I went into Zoneminder and changed the camera properties to that colour palette, it worked.

---

