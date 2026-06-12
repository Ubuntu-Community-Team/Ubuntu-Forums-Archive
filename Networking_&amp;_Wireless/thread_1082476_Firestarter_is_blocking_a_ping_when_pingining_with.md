---
title: "Firestarter is blocking a ping when pingining with a host name"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by Greg Davis on 2009-02-27
Firestarter is blocking a ping from other computers in my home LAN when pinging with a host name.  For example, "ping DEV" from a remote computer gives "Ping request could not find host DEV."  It works fine when I ping with the ip address of DEV which is 192.168.1.108.  I have port 53 opened for everyone.  Pinging by host name works fine if I stop Firestarter.  It is as if my Linksys router does not properly perform DNS on my DEV computer when Firestarter is running.  I can not even ping from inside my router to DEV by host name when Firestarter is running.  

I am running Ubuntu Server 8.10.  I am new to Linux and would appreciate any help!

---

### Post by Greg Davis on 2009-02-28
After quite a bit of trial and error, I resolved the issue so I thought I would post the solution.  I needed one more policy for inbound traffic: Samba (SMB) ports 137-139, 445.  I should have stated that my remote PC was a Windows Vista box.  As soon as I allowed Samba for that specific remote IP, it worked.  I also noticed opening up Samba for everyone instead of the specific IP allowed me to see my network attached storage that is attached to my Linksys router.

---

