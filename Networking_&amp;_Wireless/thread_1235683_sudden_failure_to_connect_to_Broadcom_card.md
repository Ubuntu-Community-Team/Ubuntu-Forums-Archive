---
title: "sudden failure to connect to Broadcom card"
date: 2009-08-09
forum: Networking &amp; Wireless
---

### Post by jmilana on 2009-08-09
A few days ago I had an sftp session fail in the middle of transferring files.  Ever since, I've not been able to get my Broadcom wireless card to connect to the Internet.  Can anyone help?

Below is the set of commands I've been running:

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod wl
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

---

### Post by Ayuthia on 2009-08-09
> **jmilana said:**
> A few days ago I had an sftp session fail in the middle of transferring files.  Ever since, I've not been able to get my Broadcom wireless card to connect to the Internet.  Can anyone help?

Below is the set of commands I've been running:

sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod wl
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

Did you compile ndiswrapper from source or did you install it from the repositories?  If you compiled it, it might just need to be recompiled because there was a recent kernel update.

---

### Post by jmilana on 2009-08-09
I believe my ndiswrapper came with my download of ubuntu 9.04.  How do I check if I have the latest version?  My update manager makes no indication that another version is ready/needed.

---

