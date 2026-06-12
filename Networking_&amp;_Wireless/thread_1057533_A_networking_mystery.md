---
title: "A networking mystery"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by mossman44 on 2009-02-01
I know a lot of people have been experiencing the problem of slow web browsing in Ubuntu 8.10. I have had this issue in 8.10 and 8.04 as well. Firefox will work fine for a little while then all of a sudden, it appears it gets hung up on looking up the dns name. I have tried all of the disabling ipv6 fixes to no avail. I've even tried to lower my mtu size from 1500 to 1492 on my eth0 interface and router but that didn't work either. I also replaced gnome network manager with wicd but the problem persists. But, the mystery gets deeper. I have a xubuntu laptop using a broadcom wireless adapter and it never experiences this issue and it has the same dns settings as my desktop. Even stranger, I have also tried using openSUSE and Debian Lenny on my desktop and neither of these systems experience the slow browsing problem using the same settings I used on Ubuntu. I'm beginning to think there may be a problem with the Ubuntu shipped version of Firefox or something wrong with the way ubuntu handles wired networking. I love Ubuntu, but this problem is very frustrating. Has anyone else had this experience as well or anyone have any insight on the problem? I have Debian Lenny up and working great so I don't think I will switch back to Ubuntu on my desktop, but I think this is an important issue that needs to be fixed in order to continue the ground breaking progress Ubuntu has made in the world of computing.

---

### Post by suda on 2009-02-01
Funny you should write about this. I was thinking the same thing as I waited for a page to download in Firefox. I was also thinking--how is it possible Vista is faster than Ubuntu? Unfortunately, I do not have an answer.

---

### Post by mossman44 on 2009-02-15
After experiencing this issue on my laptop while using the wired network at a hotel, the problem cannot be my router. This does not occur when I use the internet on a wireless network. I believe there is an issue with ubuntu's wired networking drivers. This is an extremely annoying issue and I'm probably going to move to another distro until this problem is resolved or someone can shed some more light on the problem or introduce a fix or workaround.

---

### Post by jivabill on 2009-02-15
Well, I had some serious problems with 8.10 I would not recommend it to anybody.

I had one of my several machines running 7.10.  I got the "update" promo at the top of my "update available" window.  So finally I went ahead and updated.  The result was a series of non fixable problems with my install, at least at my skill level.  And I had the dreaded message that says your linux module is not the right size.

To make a long story short I researched 8.10 and found many comments and posts about problems with that version.

So I had to totally rebuild the machine, installed 8.04 on it and it has been running fine ever since.  I don't plan upgrading to 8.10 for a LONG time, hopefully by then the developers will get it together to fix 8.10 so it works right.
My two cents
Bill

---

### Post by Matsukaze on 2009-02-15
I don't know if this is related to your problem, but I've had a problem with the DHCP server on my Actiontec DSL router supplying the router's address (192.168.0.1) instead of my ISP's DNS server. For some reason, this doesn't seem to bother my Windows box, but on Ubuntu web browsing suddenly slows down to molasses-in-February speed. When you experience slow browsing, look in /etc/resolv.conf and see if the nameservers are what they should be. 

I fixed the problem by following the setup instructions at [OpenDNS]("https://www.opendns.com/start/device/ubuntu"). This should also work if you use your ISP's nameserver addresses instead of the OpenDNS server addresses.

---

### Post by mossman44 on 2009-02-15
I've tried using both time warner's dns servers and open dns servers (which I normally use) but the problem still persists. Based on my own experience and those of others, I'm convinced this must be an issue with the way ubuntu handles wired networking. I hope this is fixed in an update soon.

---

### Post by error420 on 2009-02-15
I have the same problem. Web browsing is all of a sudden slow but all other network tasks wrok fine. Other pc running 8.10 works fine over wireless connection. Do you have an ASUS motherboard by any chance?

I'm on my ubuntu 8.10 machine but im using this forum via rdesktop client to connect to my windows machine. I think something changed in the past 2-3 days that is affecting my driver. I'm using an ASUS P5N E sli motherboard. Can anyone please help? All other computers on the network including my girlfriend's lenovo s10 netbook (also running 8.10) is working fine.

---

### Post by mossman44 on 2009-02-15
I have a gigabyte motherboard with a realtek ethernet adapter for my desktop. My laptop is an old Gateway 200ARC. Seeing this issue has persisted on different brands of hardware leads me to suspect this is a software issue rather than hardware incompatibility. The mystery continues, but we are starting to get somewhere.

---

