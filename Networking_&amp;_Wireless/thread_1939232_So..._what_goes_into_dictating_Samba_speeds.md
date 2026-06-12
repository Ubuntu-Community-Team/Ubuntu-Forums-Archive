---
title: "So... what goes into dictating Samba speeds?"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Roasted on 2012-03-11
I've always been a fan of Samba. I have a file server set up at home that works for data backup as well as basic file transfers. I'm testing Ubuntu on a 2007 Macbook and doing my best to use it as much as possible. When I connected to my file server I noticed a 17 MB file transfer taking forever. It was transferring at 250KB/s.

I hopped on my other laptop, an Atom powered 12" netbook with some sort of Intel or Atheros chip, it transferred the 17 MB file within 3 full seconds or so.

The Macbook's wireless is:


02:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)


I'm sure the wireless card/driver plays a certain role in things like this, but I've ran Broadcom before without too much hassle. Has any other Broadcom users had things like this happen? Or is this likely to be something in regard to the fact I'm on a Macbook? I've always touted that Apple systems aren't that different hardware wise, but it is a little food for thought this time - makes me wonder if the difference in hardware that MAY exist could be the reason why the file transfers are taking an easy 8-10x longer than my other, lesser powered laptop.

Note - All laptops are wireless N. Router is wireless N as well.

EDIT - The wireless card in the netbook I have is an Intel N1000. As I said above, the Macbook wireless card is a Broadcom BCM4321. Being this Macbook is from the 2007 area, whereas this Intel wireless card is 6 months old, I wonder if there's some sort of wireless capability that the Intel has over the Broadcom in reference to the brand new Wifi N router I got a matter of days ago (Netgear N600 3700).

Although, 300 KB/s average for a laptop that is supposedly wireless N speed and is within good signal range with no interference leaves me still confused, as I'd expect it, at the very least, to be in the MB/s section, not hovering at 300 KB/s steady.

---

### Post by 2F4U on 2012-03-11
I have Xubuntu on a 2008 Macbook. When I connect to my Samba server I don't notice a difference in speed compared to my other machines. However, I never use a WiFi connection, but always go through ethernet.

---

### Post by TheFu on 2012-03-11
Break down the problem to find the answer. You'll need to look at all the parts to determine where the slow down is really happening.
* disks
* networking
** router
** NICs
** drivers
* OS settings
** Samba
** firewalls
** routing
* CPU
* RAM / caching / buffering

My first test would be to stop using wifi and see if the problem still exists.  To me, wifi is never a preferred connection method. Wired is always preferred.

Next I'd try transferring in the opposite direction to see if the issue is read or write connected.

If you must still use wifi, be aware that if any device connects at slower speeds, then the entire wifi network drops back to that slower speed. It is for backwards compatibility.  Also, every device added to a wifi network reduces the throughput about 50% .... 300/150/75/ .... 50/25/12.5/6.25 .... as more and more devices are added, it gets slower and slower.  If any device has trouble due to range, all the devices will be impacted. You might want to disable wifi on the cell phone.

Samba has lots of settings to restrict which network interface is used. I suspect (but do not know) that it tries to use a wired interface before trying wifi interfaces. Be certain that you completely disable (ifdown eth0) the wired interface if you insist on using the wifi one.

---

### Post by jldoll on 2012-03-11
I had a similar issue on my Windows designed hardware, maybe be applicable to mac book if running ubuntu.  It was the power settings for wifi interface when on battery power. This fixed my issue: "sudo iwconfig eth1 power off" where eth1 is the wifi assignment.

---

### Post by jldoll on 2012-03-11
iwconfig will tell you your card assignments

---

