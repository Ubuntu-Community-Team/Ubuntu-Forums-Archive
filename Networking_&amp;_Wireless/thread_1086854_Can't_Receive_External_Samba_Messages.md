---
title: "Can't Receive External Samba Messages"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by FyberOptic on 2009-03-04
Howdy folks.  I've decided to setup another Linux machine, this one needing to be able to communicate with other Windows machines on a network using the 'ol Winpopup style of communicating.  The Windows machines actually use RealPopup, which is much better, but it can be configured to communicate as WinPopup too, which is probably necessary for talking to Samba.

In any case, I have never ever had any luck with receiving messages in Linux.  This isn't the first time I've tried this, even, and I've never made it work.  For testing, I set my Samba configuration to log received messages rather than deliver them via Linpopup, so that I can more easily debug what's going on.  

I can, for what it's worth, receive messages sent from the same Linux machine via smbclient.  It's just ones from Windows that I send with "net send" and RealPopup which I never get.  It's strange, because when I run nmbd and such from the console, I see some acknowledgement scroll by that it perhaps saw the message.  It's just not handling it.

Some useful information might be in the fact that when I do a normal net send from Windows, such as "net send ubuntu Test Message", I get this:  "The message alias could not be found on the network."  The only time it "works" is if I use "net send jeff /domain:ubuntu dsfsdf", and then it acknowledges that the message was sent.

Anyway, as I said, I have never had any luck with making this work, on any installation of Linux I've ever made.  It's important that the machine can both send and receive these messages in order for me to put any sort of extended use into it via that OS.  

So my biggest question is, is anyone out there actively using a setup like this?  It'd be nice to know that it's possible, to start with.  I'm hoping somebody can shed some light on what might get this working properly this time!  Thanks in advance.

---

