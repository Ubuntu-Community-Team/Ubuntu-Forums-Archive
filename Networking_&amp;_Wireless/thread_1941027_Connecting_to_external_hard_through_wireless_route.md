---
title: "Connecting to external hard through wireless router"
date: 2012-03-14
forum: Networking &amp; Wireless
---

### Post by tajreed on 2012-03-14
Asus n56u router shows the HD connected via USB but I can't figure out how to get my Ubuntu machines to "see" the HD through the router. Any thoughts, ideas?

Thanks

---

### Post by Bucky Ball on 2012-03-14
Is this a network drive with an assignable IP address?

---

### Post by tajreed on 2012-03-15
The router config shows no IP address for the HD. As it does for the laptop, printer, pc and Roku box. I must be missing something. I can use the router config to see the contents of the HD.

---

### Post by Bucky Ball on 2012-03-15
How are you looking at the HD contents via the router??? Unless this is a NAS external drive (a network storage device) I don't think it is as easy as plugging into the router and the HD's on the network and visible to all other machines on your LAN. Unless you can assign it an IP not sure you are going to have much joy. Dig through this:

[http://au.search.yahoo.com/search;_ylt=A0oGkmgN5WFPhwEAPl0L5gt.?p=usb%20external%20hard%20drive%20router&fr2=sb-top&fr=altavista&rd=r1]("http://au.search.yahoo.com/search;_ylt=A0oGkmgN5WFPhwEAPl0L5gt.?p=usb%20external%20hard%20drive%20router&fr2=sb-top&fr=altavista&rd=r1")

---

### Post by tajreed on 2012-03-15
I had to set up an Ftp with the Asus config then access via FileZilla. And I can upload and download from both pc and laptop. Awkward at best. I'll check out the site you suggested.
The ASUS router allows me to examine the HD.

Thanks

---

### Post by tajreed on 2012-03-16
Win7 as a guest in 12.04 can see the entire network including the external hard drive. Neither my 11.10 nor the 12.04 Ubuntu installations can do that. What am I missing here? 'Browse network' has no effect. Is there something in the repository that can fix this?

---

