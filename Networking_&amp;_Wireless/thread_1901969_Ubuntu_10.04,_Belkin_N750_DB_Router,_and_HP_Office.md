---
title: "Ubuntu 10.04, Belkin N750 DB Router, and HP Office Jet J4550 Printer Network Problem"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by dancar22 on 2011-12-29
I just purchased the Belkin N750 DB router from Costco.  The router lets you plug in external hard drives, printers, etc. into the back of it using two USB 2.0 connections.  I have no problem seeing my Maxtor external hard drive on the Ubuntu 10.04 network or on my daugher's Windows 7 laptop.  Her Windows 7 laptop can also see the HP Office Jet J4550 printer but I cannot find the printer on the Ubuntu 10.04 network.  Any suggestions?  Thank you for your help in advance.  Dub

---

### Post by dancar22 on 2011-12-30
Nothing?

---

### Post by dancar22 on 2011-12-30
bump

---

### Post by dancar22 on 2011-12-31
bump

---

### Post by dancar22 on 2012-01-01
bump

---

### Post by dancar22 on 2012-01-03
bump

---

### Post by alan.gustavo on 2012-01-03
Please i have a same problem.

---

### Post by dancar22 on 2012-01-04
bump

---

### Post by pennygov on 2012-01-05
I would like to know how you can even see your external hdd on ubuntu! I thought that you needed to install the Windows or Mac software to monitor them (which I tried to install using wine 1.3, which failed):(


Edit later: Oh sorry, checked networks again in file manager and found it!

---

### Post by dancar22 on 2012-01-06
bump

---

### Post by dancar22 on 2012-01-07
bump bump

---

### Post by dancar22 on 2012-01-09
bump bump

---

### Post by kurt18947 on 2012-01-09
I've had no problem seeing printers on networks.  I'm surprised HP in particular is a problem, that's usually the easiest brand to install in Linux.  I'd probably try installing hplip, hplip-data & hplip-gui.  I'd use synaptic but I'd guess Ubuntu software center would work as well.

---

### Post by dancar22 on 2012-01-09
Thank you so much.  I will give it a try.  Dub

---

### Post by dancar22 on 2012-01-10
No good.  Still cannot find the printer on Ubuntu while Windows 7 works flawlessly.  Any suggestions anyone?  Dub

---

### Post by dancar22 on 2012-01-13
No good.  Still cannot find the printer on Ubuntu while Windows 7 works flawlessly.  Any suggestions anyone?  Dub

---

### Post by dancar22 on 2012-01-20
bump

---

### Post by dancar22 on 2012-01-25
bump bump       bump

---

### Post by dancar22 on 2012-01-27
bump bump bump bump

---

### Post by praseodym on 2012-01-28
Hi,

I am also interested in that and did some research (this is why I subsrcibed to this threat).

Do you have an ethernet cable which can connect the printer directly to the router? If yes, add a static IP address for the printer and open the "printing" dialog to add a new printer->Network printer->AppSocket/HP JetDirect and add the IP.

I dont have a cable so I will try it somehow via USB with an Officejet J4580 All-In-One with Lucid

---

### Post by dancar22 on 2012-01-30
Thanks!  I will give it a try.  Dub

---

### Post by hturbulence on 2012-04-08
Did any of the suggestions work?  I have exactly the same problem with the N750DB router and an HP printer plugged into the router via USB.  I've been playing with this for two days before I came across this thread.

If anyone has resolved this, a little write up on it would be AWESOME!!!  Thanks :confused:

---

### Post by h4ck3rc1 on 2012-04-25
bump.

I have been able to get the USB storage part working, just not printer.

---

