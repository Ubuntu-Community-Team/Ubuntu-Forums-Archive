---
title: "Cannot detect usb hard drive(s) over ssh"
date: 2011-09-22
forum: Networking &amp; Wireless
---

### Post by BavidDowman on 2011-09-22
Hi,
I have a ssh server running on my  Ubuntu 10.04.3 LTS  work computer and I am connecting to it through my Ubuntu 11.04 laptop. I have 2 NTFS usb hard drives connected to the server which are automatically mounted in gnome and show up in /dev as sdd and sde respectively when I log in locally.

However, when I log in through ssh, or a graphical remote client such as NX, neither do any of the hard drives mount automatically, nor do they show up in /dev/ . This pretty much defeats the purpose of ssh since most of my data is inaccessible over a remote connection.

Any guesses as to what is causing this?

---

