---
title: "Use Printer Over Network?"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by soylentcola on 2011-05-16
So I'm generally new to Ubuntu and have been trying to figure this out for a while... I have Ubuntu installed on our home desktop, and our main printer is connected to it (an "ancient" HP Deskjet 970Cse).  The desktop is also connected to a wireless router (Netgear WGR614 v6) and I was wondering, is it possible for me to set this printer up to be used over the WiFi router in our home network? (Which consists of two Windows 7 laptops and a Mac laptop)

I have Samba installed on Ubuntu but I'm not 100% on how to go about setting this whole thing up...would someone mind walking me through how to get this accomplished?

---

### Post by soylentcola on 2011-05-19
Just so people can know, I managed to solve this myself! Instead of using Samba Server, I used the CUPS server and had to edit the config file a bit to get things properly situated (you'll need your Ubuntu's IP address and a few other things that escape me) but it was actually rather simple. Changing this to solved! :D

---

