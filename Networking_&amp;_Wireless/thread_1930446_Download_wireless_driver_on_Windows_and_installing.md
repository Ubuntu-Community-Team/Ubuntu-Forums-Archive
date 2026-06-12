---
title: "Download wireless driver on Windows and installing on Ubuntu 10.04"
date: 2012-02-23
forum: Networking &amp; Wireless
---

### Post by Digital Silence on 2012-02-23
I am unable to connect to the internet via wireless PCI card.  I don't have a USB wireless card and (it's a little difficult to explain) I am unable to connect an Ethernet port directly into my PC.  Is it possible with the information that I got from typing in *lspci -vnn | grep 14e4* that I can find the drivers online, put them on my usb drive, and install them when using Ubuntu?  And if so, how would I go about doing this?
Ubuntu 10.04

---

### Post by chili555 on 2012-02-23
Let's see what you have first, before we devise a strategy. Please run and post:```
lspci -nn | grep 0280
```I am pretty confident we can do what you suggest.

---

