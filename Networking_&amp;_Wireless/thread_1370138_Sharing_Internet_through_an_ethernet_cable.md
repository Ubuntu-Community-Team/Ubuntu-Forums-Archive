---
title: "Sharing Internet through an ethernet cable"
date: 2010-01-01
forum: Networking &amp; Wireless
---

### Post by Shack_ on 2010-01-01
I've been trying to get Ubuntu 9.04 set up on my desktop (dual-booted with Windows Vista) and I'm having problems getting connected to the Internet.

I have a wireless card installed in the desktop, and I know it will work, because it's been set up before. But I had to move the desktop into the room where my router is (because it's connected to another computer), connect it directly to the router, download the drivers for the wireless card, and then move it back.

I'd rather not move the computer again, so I've been trying to share Internet from a laptop running Ubuntu 8.10 off a LiveCD (which detects the wireless card in it without any configuration) with the desktop. I have an ethernet cable running between the two, but can't get the desktop to connect to the Internet.

I've searched all over the place, but I haven't found anything similar to my situation, and so I'm lost.

The OS on the desktop is a clean copy of Ubuntu 9.04, and I haven't made any kind of configuration changes to the network settings.

So, what I need to know is how to share an internet connection from a laptop to a desktop, where the laptop is connected to the Internet via a wireless ethernet card to a router.

I've tried to make this as clear as possible but please let me know if I need to include something else.

---

### Post by peepingtom on 2010-01-02
The ethernet cable must be a "crossover cable" if you're connecting two ethernet cards together. If your laptop runs windows, boot into it, select your wifi and ethernet connections, right-click and "bridge" the connection. Bridging and connection sharing are much more difficult under Linux, i'm not competent enought to describe the process.


[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
You can manually download packages here and move them over with a USB drive.

---

### Post by Shack_ on 2010-01-02
Bridging the connections worked! I had to use _[this guide]("http://www.microsoft.com/windowsxp/using/networking/expert/crawford_02april22.mspx")_ to force the wireless card into compatibility mode, but after that I was able to connect.

Thanks for the help!

---

