---
title: "Connects to internet, but not to home network"
date: 2010-08-25
forum: Networking &amp; Wireless
---

### Post by j_freshman on 2010-08-25
Hello,

I installed Ubuntu 10.04 32-bit on an old desktop (1.5ghz Pentium 4, 20GB hard drive, 768MB RAM) a week or two ago, at the same time that I installed Xubuntu 10.04 on an even lower performance IBM tower server. The server functions perfectly and my other (Windows XP) desktop recognized it from the start, as did the Ubuntu desktop. However, I rearranged a few ethernet cables the other day without turning off the desktops and ever since my Ubuntu machine does not recognize my server, even though all of the devices are connected via ethernet cable to a linksys router and it connects to the internet without a problem. I'm a linux newbie - this is my first move away from Windows - and I don't know where to turn. Far more confusing is the fact that, when I boot from a LiveCD, the network is recognized and I can read/manipulate files on my server without a problem. Oh, and I briefly flirted with OpenSUSE KDE (not as noob-friendly as Ubuntu, so I'm back) and encountered the same problem.

Needless to say, booting from the hard drive is preferable to booting from CD every time

Any help is much appreciated,
Joe

---

### Post by Iowan on 2010-08-25
From a terminal (Applications>Accessories>Terminal), check **sudo lshw -C network** from CD, then from HD - in particular, notice if the driver changes. You might also notice if theinterface gets an IP address. Another way to check that is by **ifconfig -a**. If the internet is working, you might check **route -n** to see if something unusual is there...

---

### Post by j_freshman on 2010-08-25
Iowan,

Thanks for replying so quickly! About an hour ago I completed a (third) reinstallation and my shared drives on the server are showing up again. But I don't know if they'll stay that way, so your advice may still come in handy. I need to dive into terminal anyways so that I can understand the system beyond the GUI. I remember a bit of wisdom that equated graphical interfaces to picture books and text commands to true literacy...

---

### Post by Iowan on 2010-08-26
Glad you got it going...
Use what works for you - it's no sin to use a GUI!

---

