---
title: "How to SSH into my computers at home?"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by YourSurrogateGod on 2011-10-02
I have a Mac mini and my Ubuntu laptop running 11.04.  Eventually I will build up my tower to run Linux.

I have a Netgear router WGR614.  I would love to ssh into either one of them (using ssh -X would be _epic_), but to be honest, I have no idea how to set that up.  How can I even ping one of my PCs behind the router?

---

### Post by dave01945 on 2011-10-02
if you want to connect from the internet not the local network you will need to set the router to forward port 22 to the machine you want to ssh to also if you are connecting from the internet it would be best to set up key authentication and disable password it is less likely someone you don't want accessing your computer

---

### Post by papibe on 2011-10-02
On the other hand, if you want to access your computer from the Internet, there are several things you need to do to make it work, and that implies understanding several concepts like static vs. dynamic IP addreses, DNS, etc. Then in your home network, static LAN IPs (or DHCP reservation), port forwarding, etc.

This is a very helpul [youtube]("http://www.youtube.com/watch?v=bI52nF1BRNo") video from the revision3 channel. It is on the Windows-side-of-things, but explains VERY well several concepts related to access your home computer from the Internet.

I hope it helps.
Regards.

---

### Post by sammiev on 2011-10-02
Posted to say I did as I want to do the same as YourSurrogateGod when I go on vac in Nov for 3 weeks. ):P

---

### Post by nitstorm on 2011-10-02
Did you look into the [Ubuntu Community Documentation on SSH]("https://help.ubuntu.com/community/SSH")?

---

