---
title: "Unable to open mixer /dev/mixer"
date: 2010-10-13
forum: Multimedia Software
---

### Post by SoulMazer on 2010-10-13
Hi, I've written a media player using Python and tkSnack that I haven't used in a while, so I just tried to run it, but it fails to produce audio. The program has worked before numerous times, but it does not now.

I simply get an error in its terminal saying "Unable to open mixer /dev/mixer". Restarting my computer to free the sound device had no effect. Does this have to do with permissions or what?

By the way, I just upgraded to 10.10 this morning, so that may possibly be a culprit. However, all other sounds on my computer work just fine.

Thanks in advance.

EDIT: Well it seems I have solved my own problem. I've searched the internet for the past hour or two, and have found a plethora of ideas, none of which seemed to work. Some involved created symbolic links, some involved creating special groups and other stuff...but the one that worked was probably the simplest. For some reason, I had to remove the package libsnack2 and install **libsnack2-alsa**. I'm not quite sure why that is, but it worked.

---

### Post by aasdfasdfg on 2010-11-06
Thanks, your post helped me out a lot. In my case, it was another Tcl/Tk application that was having sound issues. Whenever I ran the program "scid", I would receive the same error message during startup. After switching to libsnack2-alsa, the problem is gone. Note: this error happened the first time I ran scid after upgrading to 10.10

---

### Post by Yellow Pasque on 2010-11-06
Probably because /dev/mixer is the legacy OSS device and the kernel in 10.10 removed OSS support.

---

### Post by ubudog on 2011-03-27
Thank you for actually telling us what you did to fix it!  It works.

---

