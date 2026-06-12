---
title: "Problem with 88E8056 ethernet controller"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by majjj on 2011-07-27
Hello!

I have a problem and I would greatly appreciate if someone here could help!

Problem: I had a Ubuntu server (v. 10.04) running on a old computer of mine. Today I switched the hard drives (the system is on raid1) to another motherboard. I didn't want to install ubuntu again since I figured it would work normally. SO, now everything works except networking. The ethernet controller on the motherboard is:
Ethernet controller: Marwell Technology Group Ltd. 88E8056 PCI-E Gigabit ethernet controller (rev 13).

I found out somewhere that it uses module sky2 or something so I added it to /etc/modules and I also did "modprobe sky2" as I read someone suggested to do.

It doesn't work...

When I do "sudo ifconfig eth0 up" it gives me "eth0: ERROR while getting interface flags: No such device"

I don't know what to do. How do I get it working?
Any help would be greatly appreciated.

---

