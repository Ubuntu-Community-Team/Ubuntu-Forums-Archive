---
title: "Security using Motion app"
date: 2010-12-11
forum: Multimedia Software
---

### Post by mark2741 on 2010-12-11
I recently switched back to Ubuntu after a few years away from it (due to hardware conflicts with a PC I had purchased). Yesterday, a package from amazon.com was allegedly delivered to my doorstep by UPS. I don't believe it was delivered (I was home at the time, no doorbell ring), but UPS swears it was. So I had the idea to setup a simple webcam-based security system (temporarily). My thinking is I'll rig this thing up, then put a big, juicy-looking (but empty) amazon.com labeled box out front of my house and hope to catch the culprit on the webcam : )

I tried following the instructions here:

[http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/](http://www.chriswpage.com/2009/05/setup-an-advanced-webcam-security-system-with-ubuntu-8-04-and-motion/)

But no luck. My webcam is detected as /dev/video1 and I set the motion.conf accordingly. When I run Motion, either through terminal or daemon, it starts up the webcam (as indicated by the green led on the webcam) but no pics get saved.

Also, when I try to kill the process via the terminal by clicking CTRL-C it doesn't work. I have to close the terminal window.

Also, the output is not viewable via localhost:8081 as stated in the tutorial.

I'm using 10.10 64-bit. Any ideas?

---

### Post by mark2741 on 2010-12-11
Success! Turns out the problem was I had an old Hauppage WinTV card in my PC. I knew that, and theoretically Motion (or any other app) shouldn't have a problem with it because you can select the /etc/videoX device you want it to use. But the PCI WinTV card was causing Motion, and it turned out all other webcam capture apps, to not work with my camera. I just opened the PC case, pulled out the WinTV card, rebooted, and now am capturing images via my webcam! Still have some configuring to do to get Motion working exactly as I want but I think I'm close.

---

