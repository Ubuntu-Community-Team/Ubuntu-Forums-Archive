---
title: "Resolution went away..."
date: 2006-01-13
forum: Multimedia &amp; Video
---

### Post by zzigahertz on 2006-01-13
My new installation of ubuntu was working fine.  It booted the first time with a screen res of 1028 x whatever... a high res screen.  I added access to an aditional drive, and when I rebooted I had 640X480.  When I tried to change it, there were no other choices.  I suspect I was changed to a default driver for the video card or monitor.  How do I get it back?

---

### Post by mustang on 2006-01-14
Try

```
sudo dpkg-reconfigure xserver-xorg
```

and pay special attention when it asks what resolutions you would like supported.

---

### Post by zzigahertz on 2006-01-14
This is done from a command window?  (What is sudo?  I see it all the time.)

---

### Post by mustang on 2006-01-14
[QUOTE=zzigahertz]This is done from a command window?  (What is sudo?  I see it all the time.)[/QUOTE]

Command window aka terminal, yeah. "Sudo" refers to super user and gives you administrative privledges, something you need to install applications.

Copy and paste what I posted into a terminal. It'll prompt you for the password you set for root when you initially installed Ubuntu.

---

### Post by Teroedni on 2006-01-14
edit

---

### Post by zzigahertz on 2006-01-14
I got this:

sudo: dpkg-reconfigure: command not found

Now what?

---

### Post by mustang on 2006-01-15
[QUOTE=zzigahertz]I got this:

sudo: dpkg-reconfigure: command not found

Now what?[/QUOTE]

Not just sudo dpkg-reconfigure, but **sudo dpkg-reconfigure xserver-xorg**

---

