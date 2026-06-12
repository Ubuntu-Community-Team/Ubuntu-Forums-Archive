---
title: "Install wireless-tools from a command line installation?"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by malangbaba on 2010-01-07
I did a command-line installation.

I dont have an ethernet connection, only wireless.
For some reason the alternate installer doesnt install "wireless-tools"

How do i install it?
At this point I am thinking of booting off a live USB, downloading the wireless-tolls package from [here]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html")
Save it to a folder in the command line installation (where?)
then boot back into command line and install from there

But I am not that savvy with command lines, and dont know where to install to...

thoughts?

---

### Post by malangbaba on 2010-01-08
SOLVED!

Went and got the wireless-tools, libc6 (udev), libiw29 packages from packages.ubuntu.com

installed them on CL through dpkg

got wireless-tools on

now wireless works!

---

