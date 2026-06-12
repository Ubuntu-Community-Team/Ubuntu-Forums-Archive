---
title: "I need 1680x1050 res"
date: 2007-10-14
forum: Multimedia &amp; Video
---

### Post by s3a on 2007-10-14
I installed envy and got my drivers, now ubuntu doesn't have the 1680x1050 res listed as an option. How do I change this? I remember someone guiding me through this out of the OS on my laptop but I didn't retain much and am wondering if it's also possible to do it through the Ubuntu OS. I can't wait to see 1680x1050 again! (I say again because that's what I used when I had windows installed)

Thanks in advance!

---

### Post by arkara on 2007-10-14
you can manually add it to the xorg.conf but i am not sure on how to do this make some googling and good luck

---

### Post by ryanVickers on 2007-10-14
yeah, in /etc/X11/xorg.conf, theres a section on resolutions - can't miss it - just add yours using the system already there...  Remember to put it in either all the categories, or the one for the colour quality you are using!!!

---

### Post by s3a on 2007-10-14
What exactly is xorg.conf?

---

### Post by ryanVickers on 2007-10-14
it's a configuration file that tells the X window system (_*everything*_ graphical in Linux) how to work/run/stores settings, like say, available resolutions ;)

---

### Post by s3a on 2007-10-14
How do I get there? Is it on boot?

---

### Post by ryanVickers on 2007-10-14
> **ryanVickers said:**
> yeah, in /etc/X11/xorg.conf, theres a section...
:p

---

