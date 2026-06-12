---
title: "Networking at home fails after 12.04 upgrade"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by presbyreformed on 2012-05-28
I have a Dell Vostro Netbook that I've taken through Ubuntu 8 till now with never a problem.
Recently I upgraded to 12.04 and had no problems with the upgrade.  I didn't try to get it onto the network for a few weeks after that.  First time I tried the wireless on my home network, it would not send or receive traffic.

Problem is home network - Comcast wireless router, nothing else
Wireless works great at other places such as my workplace
Using brand new CAT5 ethernet cable will not connect either
Sometimes it will connect to internet for up to a minute then loses it
Had no networking problems at home with 11.10
A Windows 7 laptop on the home network has no problems connecting to internet

I am connecting to the Comcast wireless and getting an ip address and routing information.

Any suggestions?

Updated:  I continued looking and found something interesting and tried it.  See here:
[http://ubuntuforums.org/showthread.php?t=1156441](http://ubuntuforums.org/showthread.php?t=1156441)
I don't know why removing references to rfc 3442 in the dhclient.conf file would work but I made that change and rebooted and I'm on the network.

If someone knows why this worked and if it is correct, please reply.  I'm not sure if this should be a permanent solution.

Update 2:  Intermittent internet using ethernet cable.  At first after the reboot I was getting good speeds online and everything was working.  After a few minutes however, it slowed down and has trouble refreshing web pages. 
Still something wrong.

---

### Post by presbyreformed on 2012-05-28
No joy.  that fix did not fix it.

I still need help, please!

---

### Post by mattsvensson on 2012-07-13
I had connectivity issues as well and was able to finally narrow it down (with help from other forums) to adding the below entries to the below two files. Looks like Ubuntu was trying to resolve the DNS servers and having DNS resolution issues doing so (ironic, no?).

Entries to add - these are Comcast DNS servers:
nameserver 75.75.75.75
nameserver 75.75.76.76

Files to add it to:
/etc/resolv.conf
/etc/resolvconf/resolv.conf.d/head

Before there was just:
nameserver 127.0.0.1
search hsd1.ga.comcast.net

---

