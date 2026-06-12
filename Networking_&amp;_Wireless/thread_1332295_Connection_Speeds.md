---
title: "Connection Speeds"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by ksmall1998 on 2009-11-20
I'm new to linux as this post will probably show. After a false start( due to not reading the documentation) I have been able to dual boot Ubuntu with WinXP. We use Wildblue satellite internet and connection speeds in XP are fairly good. But in Ubuntu, speeds are slow and very noticable. Can anyone point to some tweaks or possible setting corrections that I am missing to get connection speeds to be comparable with XP?

Wildblue does offer an optimizer( for settings) for Mac OS. Would this work for Ubuntu??

---

### Post by Yoann Juet on 2009-11-20
There's nothing to tweak for "personal" use of ubuntu. Maybe you have Domain Name resolution issues (DNS) or something related to speed/duplex negotiation with your switch/router.

Just try to download an ISO image. Don't worry, nothing is written on your hard disk (/dev/null) !

wget [http://cdimage.debian.org/debian-cd/5.0.3/i386/iso-cd/debian-503-i386-CD-1.iso](http://cdimage.debian.org/debian-cd/5.0.3/i386/iso-cd/debian-503-i386-CD-1.iso) -O /dev/null

What is your download speed ?

---
useful commands to see what's going wrong on your installation

ifconfig -a
cat /etc/resolv.conf
mii-tool -v YOUR_IFACE   (for instance mii-tool -v eth0)
ping [www.google.com](www.google.com)

---

### Post by ksmall1998 on 2009-11-21
Thanks for the reply.

The rated download speed is 512k, but that never happens. The speed on the link you provided fluctuated between 80 and 50 k. Plus it is dependent on time of day and total number of users. 

I'm now thinking that is network tweaks in FireFox itself. Any ideas for brower tweaks?

---

