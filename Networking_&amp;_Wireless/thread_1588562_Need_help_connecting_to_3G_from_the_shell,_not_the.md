---
title: "Need help connecting to 3G from the shell, not the GUI"
date: 2010-10-05
forum: Networking &amp; Wireless
---

### Post by TheFr00n on 2010-10-05
Hi all,

I live in the sticks, where the only available internet is 3G. I'm using Ubuntu 10.04 on an old Dell laptop, with a Vodacom 3G dongle. It works perfectly. I can connect and disconnect using the Networking GUI thingy in the top right corner of the Gnome desktop.

However, this laptop actually serves as a router for the house. I am experiencing a big problem.

The laptop no longer has a screen (part of why it's now a router). My original plan was to VNC into it and connect/disconnect the 3G as needed. But if I boot the laptop without a monitor, X freaks out and won't start. I can SSH into the laptop and attempt to manually run startX, but without a screen attached, it fails. Without the GUI, I can't connect the 3G.

Right now, I have to connect a monitor to the lappie every time I boot it. If I have to have a big CRT attached to this little laptop, it defeats the object of being a quiet little router that sits on a shelf.

First prize solution would be if there were a way to connect the 3G from the shell, without having to use the GUI app. Does anyone have any idea how I can launch the 3G connection from the commandline?

---

### Post by robert_pectol on 2010-10-05
I've used the ***wvdial*** utility to do exactly what you are talking about.  A couple of Google searches for ***wvdial*** should get you up and running in no time.  Good luck.

---

### Post by TheFr00n on 2010-10-05
Sweet! Thanks for that. It's working like a charm.

I found this thread particularly helpful:
[http://ubuntuforums.org/archive/index.php/t-633981.html](http://ubuntuforums.org/archive/index.php/t-633981.html)

EDIT: wait wait wait. Something isn't right.

This is very bizarre.

If I SSH into the linux box and **sudo wvdial**, I get a bunch of errors. I suspected that it was something to do with permissions, so I ran **startx**, even though it crashed without a monitor attached. But having run X, **sudo wvdial** now works.

I can't think why that would be. I'm still pleased because I can launch the 3G without a monitor, but I think it's weird that I have to crash X server first. Any ideas?

---

### Post by alexfish on 2010-10-05
can you also have a look at (also check out post #26)

        [LEFT]&#65279;[How To : Mobile Broadband Connections [ Ubuntu 10.04 : 9.10 : 9.04 ]]("http://ubuntuforums.org/showthread.php?t=1466490")[/LEFT]
        [LEFT]also checkout[/LEFT]
                        [LEFT][http://ubuntuforums.org/showthread.php?t=1583103](http://ubuntuforums.org/showthread.php?t=1583103)

[/LEFT]
        [LEFT]alexfish

[/LEFT]

---

