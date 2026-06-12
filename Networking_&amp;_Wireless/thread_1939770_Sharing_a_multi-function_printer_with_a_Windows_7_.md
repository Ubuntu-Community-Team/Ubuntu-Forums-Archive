---
title: "Sharing a multi-function printer with a Windows 7 client"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by Robert Finley on 2012-03-12
I am trying to share an HP Deskjet 2050 J510 that is physically connected (via USB) to an Ubuntu 12.04 machine.  The client is a Windows 7 laptop connected wirelessly to my home network.

I edited smb.conf and have the printer functioning correctly over network.  To accomplish this I followed the steps outlined here: [http://ubuntuforums.org/showthread.php?t=1339956](http://ubuntuforums.org/showthread.php?t=1339956) 

I am now investigating how to get the scanner to function remotely as well.  Can anyone help me in this endeavor?

---

### Post by wyliecoyoteuk on 2012-03-12
Scanners cannot be shared in the same way as printers.

It is possible between LinuxPCs,using SANE. There is also a Windows SANE client

[http://forums.fedoraforum.org/showthread.php?t=639](http://forums.fedoraforum.org/showthread.php?t=639)
[http://hardc0l2e.wordpress.com/2009/07/10/sane-sharing-in-ubuntu/](http://hardc0l2e.wordpress.com/2009/07/10/sane-sharing-in-ubuntu/)
[http://sanetwain.ozuzo.net/](http://sanetwain.ozuzo.net/)

---

### Post by Robert Finley on 2012-03-12
Thank you my friend.  The information you provided is what I was looking for.

---

