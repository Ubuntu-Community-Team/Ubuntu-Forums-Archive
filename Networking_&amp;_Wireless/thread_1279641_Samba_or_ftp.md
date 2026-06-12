---
title: "Samba or ftp?"
date: 2009-10-01
forum: Networking &amp; Wireless
---

### Post by Chris Riley on 2009-10-01
Help please!

I run Hardy Heron (not the server edition).  I have recently purchased an Icybox MP308, which is a hardware media server. It will stream media (film, music, pics) from my desktop which is wireless connected, and will connect to internet to stream radio (but not other media content) through my adsl router. It has a SATA HDD installed. I can transfer media to the HDD via USB (it then acts as an external HDD). I can also play media from a USB-connected device.

What I believe I should be able to do is transfer media to the HDD via the network connection as well. I have no previous experience setting up a network. I would appreciate some guidance on where to start. There are plenty of guides on the forum for networking, but I don't know whether that is the way to go, or whether I need to use ftp.

Your help and advice will be much appreciated.

---

### Post by mattkoehn on 2009-10-01
If you are on your local network only, ftp is maybe a little clunky for what you are doing. However, that depends entirely on your level of experience with tools in your operating systems. It doesn't matter what protocol you use to transfer files to and from your server really. 

If you are doing it over the internet then ftp may be a little nicer only because it is routed and easily forward through a router.

The absolute simplest thing would be a share, like samba or windows equivalent. Again, if just local I would by far choose samba but that is maybe more of preference thing.

Good luck.

---

### Post by Chris Riley on 2009-10-02
Thanks for the suggestion that Samba is preferable over WLAN; unfortunately I don't think I have the choice because of the way that the Icybox is configured.

The Icybox can be configured with both host and client details. What do I need to do at the computer to ensure that I can send files to the Icybox? Which is the host, and which the client?

Thanks in anticipation,

---

