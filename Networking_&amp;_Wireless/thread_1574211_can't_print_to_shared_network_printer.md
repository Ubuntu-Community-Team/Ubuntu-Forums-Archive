---
title: "can't print to shared network printer"
date: 2010-09-13
forum: Networking &amp; Wireless
---

### Post by ReplicateThis on 2010-09-13
Hi.  I am trying to print to a shared printer and having difficulty.  I have followed all instructions listed at [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu).

PC1 has a printer attached that I have set to share as listed in the Network printing article.  The printer is working and I can print to it from PC1. PC2 (the PC without a printer attached) can find the networked printer and when I right-click the printer its properties list the proper IP for the printer's host computer (PC1) and all seems well.  I have it set to be the default printer as I've read that Ubuntu seems to prefer this.  I should also mention both PCs are using Ubuntu Lucid Lynx.

Now I click the 'Print Test Page' button on PC2, and a dialog box says the job was successfully sent to the printer on PC1.  Trouble is, no printing actually occurs.  The printer works, and PC2 can see it through the network, and I've checked that all steps from the Network Printing With Ubuntu article I linked above have been followed.

What should I look at next?

---

### Post by MaindotC on 2010-09-14
I really don't deal very much with network printers but I'll attempt to help you.  Is the printer connected to another Ubuntu machine?

---

### Post by ReplicateThis on 2010-09-14
The printer is connected to a machine running Ubuntu Lucid.  The 2nd machine trying to connect is also running Lucid.

And thank you for your kind offer of helping.  :)

---

### Post by MaindotC on 2010-09-14
Can you print on the machine that is connected to the printer?

---

### Post by ReplicateThis on 2010-09-14
Yup.  Printer is attached to PC1 and I can print fine from PC1.  I just can't print from PC2 through the network.

Perhaps I should mention the two PCs can see each other on the network - proof is that I am using Synergy ([http://synergy-foss.org/](http://synergy-foss.org/)) to share a mouse and keyboard between the two machines.

---

### Post by MaindotC on 2010-09-14
Ahh Synergy...good application :D  Alright on the machine that can print - is there an option to share the printer?  Like right-click on it or something?  Sorry I don't have a printer or I'd verify before asking you.

---

### Post by ReplicateThis on 2010-09-14
Yup. Went into the basic server settings, selected to Publish the shared printers from this computer, then went into the printer's properties, into policies and set to share, all as listed on the help page at [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu).

The second PC, the one without a printer attached, can see the fact that the first PC is sharing a printer, and the correct printer is listed (HP DeskJet D2330).

---

### Post by MaindotC on 2010-09-15
Send a print job and check the syslog on both machines.  I'm not sure if it would show on both machines but there should be something in /var/log/cups or /var/spool.  Again I apologize for not having a printer and being able to troubleshoot this fully with you, and I hope I'm not suggesting the obvious, but hopefully just my ideas will help.

---

### Post by ReplicateThis on 2010-09-15
Seems that brought up something interesting...  This is the "access log" located at /var/log/cups :

```
localhost - - [15/Sep/2010:09:43:08 -0400] "POST /printers/Deskjet-D2300-series HTTP/1.1" 200 19496 Print-Job successful-ok
localhost - - [15/Sep/2010:09:43:10 -0400] "POST / HTTP/1.1" 200 344 Create-Printer-Subscription successful-ok
192.168.0.111 - - [15/Sep/2010:09:48:27 -0400] "POST /printers/Deskjet-D2300-series HTTP/1.1" 200 270933 Print-Job successful-ok
```

I printed first from the PC connected to the printer, and the document printed correctly.  The log indicates it as well.

The second trial from the second networked machine (192.168.0.111) showed up in the log, but the printer never actually printed it.

The error log covering this period of time is blank.  I am not sure how to access the directory at /var/spool - Nautilus says I don't have permissions, and not sure how to get there with the terminal.  With XP I was like Neo in the Matrix, but on Ubuntu I'm more akin to Homer Simpson so far...  :p

On another note -  I really do appreciate the help.  I'm needing an OS upgrade, and am trying Ubuntu instead of going down the Micro$oft road yet again.  So far I'm quite impressed and appreciative of how helpful the community is.  Thanks strAlan!

---

### Post by ReplicateThis on 2010-09-21
Well, I kinda forgot about this issue while trying to figure out how to share files, but had to print something for class today and was reminded of my issue.  

I still haven't found a fix to be able to print through the network, but on playing around with LiveCDs, I've discovered that printing through the network works just fine if both machines use Linux Mint.  Now I'm trying to figure out why.  I'd prefer to stay with Ubuntu rather than Mint, but since Mint is essentially Ubuntu-plus-a-few-things, I'm sure it is fixable in Ubuntu.

Anyone have any suggestions?

---

### Post by ReplicateThis on 2010-09-21
It seems the ghosts of Windows Past have invaded my machine.

I went through the steps again to share printers, and lo and behold, this time it worked.  I must've done something wrong.

Anyway, turned out the problem was a short circuit between the keyboard and chair.  Marking issue resolved, and thanks to all for the assistance!  :)

---

### Post by MaindotC on 2010-09-24
I'm glad the problem went away and I wish I could have done more :(

---

