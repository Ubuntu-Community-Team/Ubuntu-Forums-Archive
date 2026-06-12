---
title: "Samsung s4 to ubuntu"
date: 2013-10-01
forum: Mobile Technology Discussions (CLOSED)
---

### Post by qzpac on 2013-10-01
Is it possible to connect Samsung galaxy s4 to ubuntu 11.04 pc and allow for data transfer?  How to do it?

---

### Post by 3rdalbum on 2013-10-01
[http://ubuntuforums.org/showthread.php?t=2175709&p=12800294#post12800294](http://ubuntuforums.org/showthread.php?t=2175709&p=12800294#post12800294)

---

### Post by BluegrassHero on 2013-10-01
I store my mass of music on a Linux server and connect via Samba service.  Set up a file share on the desktop and use a Samba client for your phone.  I use File Manager from Rhythm Software on the Google Play store.  Based on the limited explanation of what you're trying to accomplish, I believe this will fit your requirements.

[https://play.google.com/store/apps/details?id=com.rhmsoft.fm&hl=en](https://play.google.com/store/apps/details?id=com.rhmsoft.fm&hl=en)

FWIW, I've tried rooting, scp, rsync, NFS... Sure, there are plenty of more nerdy ways to do this; but a simple SMB connection seems to always work for this.  I've been doing it for a couple of years now with great success.

---

### Post by Bucky Ball on 2013-10-01
11.04 reached end-of-life a year ago. No longer supported. Your chances of getting help are minimal and your system is vulnerable if it is online as it hasn't received security updates in a year.

Install a supported release, 12.04 LTS is supported until 2017. At the moment a needle in a haystack and your needle is getting smaller as time passes. Your issue may well be non-existent in a newer release.

---

### Post by SeijiSensei on 2013-10-01
Actually your best bet is 13.04 which includes support for the MTP protocol that Android now uses for USB connections.  Then you can just attach the phone to the computer with its USB cable and move files between the devices.  Earlier versions of Ubuntu supposedly included MTP support, but it was spotty at best.  13.04 works fine with my Galaxy S3.

---

