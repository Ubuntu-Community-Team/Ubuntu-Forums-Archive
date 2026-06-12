---
title: "Video and Graphics problems"
date: 2007-09-30
forum: Multimedia &amp; Video
---

### Post by patmalcolm91 on 2007-09-30
I'm having problems with video and graphics in many of my applications. In totem, when i play an audio file, it takes around 10 seconds before the graphic starts going. In kdenlive, the video plays for a few seconds, then goes black. In all of the various 3D modeling programs i've tried, including Wings3D, QCad, Sketchup (in wine), and others, the graphics area is either black or horribly glitchy. Totem does handle video very nicely, and Even when rotating the desktop cube in beryl, it isn't glitchy at all. My screensaver also blinks black squares at the top (where the applets in the tray are), and sometimes in other places, although this is less of a problem. Also, various other applications that use graphics haven't worked properly

I'm on a Dell Inspiron 630m laptop that is a couple years old
My graphics card is: Mobile 915GM/GMS/910GML Express Graphics Controller

Any help would be greatly, greatly appreciated! I really want to do some video editing and 3D modeling, but it's practically impossible with the way things are now.

---

### Post by scrooge_74 on 2007-10-01
There are a couple of threads on drivers for that card, but I cant find them right know, I also have an intel graphic chip and is working fine. It would seem that you need to change the driver that is been use

---

### Post by patmalcolm91 on 2007-10-01
I've tried searching for info on the card, but i didn't ever search for a driver (i feel stupid now). Thanks, I'll do a little more digging.

---

### Post by patmalcolm91 on 2007-10-03
i tried the intel driver (instead of the i810 driver that i had), but i wasn't able to log in, so i had to reinstall the i810 driver via the command line. Is there any driver that won't cause problems for this card? possibly even a proprietary driver?

---

### Post by scrooge_74 on 2007-10-04
Intel open source drivers are supplied by Intel, it takes some configuring, but hang in there. I know there is a Howto I bookmarked, but sadly it is on a laptop which is at the shop getting repair. I won't have it for another day.

The drivers should be in the repos

xserver-xorg-video-i810 is the name of the package, if I am not mistaken there is a howto on how to use the i810 with a i910 card. Sorry I can't be more specific at this moment

---

### Post by patmalcolm91 on 2007-10-10
The i810 package is the one i have installed. I'll look around for the how-to your talking about, thanks for the help.

---

### Post by scrooge_74 on 2007-10-10
Not sure if this will help, I read those in the past, I only have one laptop using an Intel driver and it has been working fine, mostly it involved using the 915resolution package.

[https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Some extra reading

[http://www.intellinuxgraphics.org/user.html](http://www.intellinuxgraphics.org/user.html)

---

