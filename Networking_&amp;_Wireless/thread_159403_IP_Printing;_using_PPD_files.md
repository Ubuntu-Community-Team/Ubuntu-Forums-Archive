---
title: "IP Printing; using PPD files"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by cls1chuck on 2006-04-12
I have a Ricoh Aficio CL5000, which has an Ethernet NIC built in; I use a static IP, and it is connected to my router.
1. Is the best/only way to configure this in 5.10 (BB) by selecting JetDirect port?  Or can/should I use CUPS or Unix?  the printer supports a variety of protocols (Netware, NetBEUI, AppleTalk)?
2. I wanted to see if a more specific/updated driver was available from Ricoh; they had (of COURSE) a bazillion Windows versions, and a MAC OSX PPD file.  Is this PPD file compatible w/ Linux?  Can i use it?

Thanks in advance!

---

### Post by rgrig on 2006-04-13
The PPD file should work.

However the printer config tool on my computer behaved a bit erratically and the only way to get the PPD file recognized was to copy it into /etc/cups/ppd.

---

### Post by cls1chuck on 2006-04-13
What about how to set it up in Linux?  JetDirect (even though I do not have a JetDirect card, the printer has its own ethernetcard)?  Or CUPS or Unix?  What settings (server/port/etc.) should I use?

---

