---
title: "Setep a linux router for GSM, WLAN and Wired"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by fidde88pven on 2010-07-29
HI!

I've been trying to setup a router for several days and not found anything that meets up with our requirements.

I've so far tried:

Admin:
-Webmin

Firewall:
-Iptables only (???)
-Shorewall
-Some I cant remember

OS:
-Ubuntu 
-Debian
-Fedora (Wont even install webmin)
-Mandriva
+++

Now Im completely open for suggestions on wich software/os/config to use!


Every configuration has something not working, and Its a little bit anoying.

I'm not a noob at linux, but not that good either.

Here is the things we want it to do:

- Share internet from one of: USB 3g modem, WLAN or wired. (The router will move arround on our LANs, and the internet comes in different ways). 
- Share internet to WLAN and wired
- Monitor as most as possible of the users traffic. We aim to be 100% legal and dont want anyone sharing illegal files.
- Be able to block ports and IPs from using internet.
- Have DC++hub. This is for the legal files, mainly free game installation files.

Is this possible?

If you help me, I can make a good and easy to understand HowTo on the subject.


Please help me.

Best regards Fredrik

---

### Post by marc.verwerft on 2010-07-30
What you want looks like a router, firewall, monitor and file sharing in one machine hooked to your internal network and to the internet. While possible, you'll create a 'single point of failure' - if that goes down, you'll end up with a lot of frustrated users. Besides that, it's good practice for a machine to be hooked to the internet to run as few services as possible since every service could be a potential security hole through which an attacker can gain access to your trusted network.

Dividing the tasks over multiple machines will make your setup more manageable and secure from as well maintenance as security point of view. I'd suggest you do some extra lookup on the theory and setup of demilitarized zones, firewalls and security before diving into setting up a single machine that does it all.

Regards,

Marc

---

### Post by Iowan on 2010-07-30
[Here]("https://help.ubuntu.com/community/Router") is a help page that might be useful.

---

