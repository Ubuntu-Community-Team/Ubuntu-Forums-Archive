---
title: "static i.p. address"
date: 2009-05-17
forum: Networking &amp; Wireless
---

### Post by c0nfusedami on 2009-05-17
I've been looking around for a couple days now and I have yet to find a good way to set my I.P. address to a static one on a wireless network nothing I have tried has worked. Could someone point me in the right direction.

---

### Post by lisati on 2009-05-17
I found it easiest to enable DHCP on my computers, and tell my router to associate a set IP address with set MAC addresses. Although there are probably other ways of doing it (which might be more suitable, depending on what you're hoping to achieve) a lot of what I've read went straight over my head when I looked at it.

---

### Post by c0nfusedami on 2009-05-17
I would really like to set a static I.P. so that I can set up port forwarding

---

### Post by lisati on 2009-05-17
> **c0nfusedami said:**
> I would really like to set a static I.P. so that I can set up port forwarding

So using your router to assign a specific IP address to a particular machine isn't an option? Unfortunately, doing things a different way is beyond my level of knowledge. Anyone else?

---

### Post by c0nfusedami on 2009-05-17
I could be wrong but I'm pretty sure that I can have my router assign an I.P. address but it's within a certain set of parameters each time I start up my computer and not one specific one. I have a Mac and I was able to specify the I.P. address for that one to remain the same through my mac not my router

---

### Post by cariboo on 2009-05-17
Probably the easiest way is to uninstall network-manager-gnome and then install network-manager-admin, and set your static ip using the gui.

---

### Post by c0nfusedami on 2009-05-17
i couldn't locate the package for network manager admin

---

### Post by superprash2003 on 2009-05-18
hope this helps [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by Iowan on 2009-05-18
You didn't mention (or I missed) which version you're using.  I've had pretty good luck (so far) with Jaunty's manual configuration through NM... but I haven't tried it on wireless, yet.

---

### Post by c0nfusedami on 2009-05-19
thank you superprash2003 that tutorial was just what I needed to get a static I.P. address up and running

---

