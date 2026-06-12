---
title: "Ubuntu won't connect wireless..."
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by linuxfly on 2009-07-08
Wiped out XP and installed Ubuntu. I can connect to the web with a hardline but can't connect to (or even locate) a wireless connection. Has to be a driver right? Anybody know where I should start looking for (and how to install) this driver?

---

### Post by t0mppa on 2009-07-08
To start looking, you need identify what kind of a chipset your card has. So, open up a terminal and run **lspci** if it's a PCI card or **lsusb** if it's a USB card and post back with the results (just the output for your wireless interface, if you can figure it out on your own).

---

