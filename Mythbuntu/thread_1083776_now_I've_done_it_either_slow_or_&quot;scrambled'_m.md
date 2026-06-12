---
title: "now I've done it: either slow or &quot;scrambled' menu"
date: 2009-03-01
forum: Mythbuntu
---

### Post by Kheos on 2009-03-01
While messing around with my mythbuntu I guess I broke something: 
Once MythTV is started, it appears very scrambled or distorted. like there is something out of sync or something.
But when I deactivate the nVidia drivers my menu looks normal, albeit reaaaal slow.

I think I was following the "get the LCD on your Antec fusion case working" topic where I must have done something wrong.
Perhaps in the envyng part?

What info should I provide and what can I do to repait my HTPC again?

---

### Post by scary_jeff on 2009-03-02
Have you tried purging the applications you installed? (sudo apt-get remove --purge appname). This helped me out a couple of times.

You could check /var/log/mythfrontend.log, /var/log/Xorg.0.log, and /var/log/syslog for any relevant errors.

Have you tried a different version of the nVidia drivers? I know there's a recommended version, but it shouldn't hurt to try a different one, provided it supports your hardware.

You could try changing the paint engine in the frontend options under appearance to determine if it's a problem with whichever engine you are currently using (Qt or OpenGL).

If the Qt engine works, but not the OpenGL one, you could try changing some of the OpenGL settings in the nVidia control panel.

When you say the image is 'scrambled', can you give a better description? Is it a scanning problem, where the image is flying up/down/left/right, or flickering badly? Or perhaps a corruption issue where everything is static, but colours or alignment are messed up? Or maybe just a theme issue where everything is far too big and overlapping?

---

### Post by Kheos on 2009-03-03
mythfrontendlog says

2009-03-03 19:20:56.971 VideoOutputXv Error: GetRefreshRate(): X11 ModeLine query returned zeroes
2009-03-03 19:20:56.973 VideoOutputXv Error: GetRefreshRate(): X11 ModeLine query returned zeroes

xorg and syslog look normal

both of the engines give the same result

and it looks indeed like a corruption issue where everything is static, but colours or alignment are messed up

---

### Post by Kheos on 2009-03-07
bump

---

### Post by scary_jeff on 2009-03-07
Did you try purging the things you installed, and reversing the changes you made, in "get the LCD on your Antec fusion case working"?

Did you try different nVidia drivers?

If you are confident with the command line, you could try backing up and then deleting your Xorg.conf, this might re-setup everything to a working state. The downside is that it's possible that this might break things and leave you with just a command line to sort it out.

---

### Post by Kheos on 2009-03-17
> **scary_jeff said:**
> Did you try purging the things you installed, and reversing the changes you made, in "get the LCD on your Antec fusion case working"?

yup
> **scary_jeff said:**
> 
Did you try different nVidia drivers?
I have no idea how to change those.
> **scary_jeff said:**
> 
If you are confident with the command line, you could try backing up and then deleting your Xorg.conf, this might re-setup everything to a working state. The downside is that it's possible that this might break things and leave you with just a command line to sort it out.
can't I just rename it, reboot and if this does not solve it rename it again? Or am I being too optimistic now?

---

### Post by Kheos on 2009-03-28
bump

---

### Post by scary_jeff on 2009-03-28
Sorry, I don't have any more ideas. I don't even know how to change nVidia driver versions, only that it is possible to change them. There must be a guide somewhere.

---

### Post by Kheos on 2009-04-02
Ok, I've come to the point where I'm willing to start all over again. Can I install it over my current setup? Should I can clean my hard disk?

---

### Post by utar on 2009-04-02
> **Kheos said:**
> Ok, I've come to the point where I'm willing to start all over again. Can I install it over my current setup? Should I can clean my hard disk?

Assuming you are using the default one partition for the OS and one for recordings then you can just reinstall the OS and leave the recordings.  Note this will wipe everything on the OS partition.

Before you do a reinstall have you tried going into the package manager, searching for the latest nvidia driver then selecting reinstall?

---

