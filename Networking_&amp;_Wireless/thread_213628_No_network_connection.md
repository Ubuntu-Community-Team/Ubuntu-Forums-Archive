---
title: "No network connection"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by esd2609 on 2006-07-11
I'm a newbie.

DHCP assigns an ip address to my computer but I can't connect to the internet or anything else.

The computer is on a small office network.  The other computers are windows.  All the computers connect to a Vonage router (Linksys rtp300) which then connects to a DSL modem.

I can't ping the router, modem or any other computers on the network.  The other strange thing is it shows that there is  a windows network but none of the computers are listed.

I've tried several linux distro to see which I liked.  The only one that was able to connect was Fedora Core 5.  But I've tried reinstalling that and it now won't connect either.  I was able to connect to the internet when using the Ubuntu live CD and could connect to the windows networks as well.

So far I've like Ubuntu the best and would like to use it.  Any help is much appreciated.


Ifconfig:

eth0  Link encap:Ethernet Hwaddr 00:80:AD:54:F1
	inet addr:192.168.15.104 Bcast:192.168.15.255 Mask:255.255.255.0
	inet6 addr: fe80::280:adff::fe0d:54f1/64 Scope:Link
	UP BROADCAST MULTICAST MTU:1500 Metric:1
	RX packets:328 errros:1195 dropped:0 overruns:0 frame:0
	TX packets:17 erros:1 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:1000
	RX bytes: 30629 (29.9 kiB) TX bytes: 1596 (1.5 KiB)
	Interrupt: 3 Base address: 0xd800

Lo	Link encap:Local Loopback
	inet addr: 127.0.0.1 Mask: 255.0.0
	inet6 addr: ::1/128 Scope: Host
	UP LOOPBACK RUNNING MTU: 16436 Metric:1
	RX packets:51 errors:0 dropped:0 overruns:0 frame:0
	TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
	collisions:0 txqueuelen:0
	RX bytes: 4961 (4.8 KiB) TX bytes:4961 (4.8 KiB)

---

### Post by dasyar613 on 2006-07-11
Start with the most obvious. Goto System->Admin->Networking. Is your network card listed there, is it enabled or active? If it is not active then make it active, and try to get on line.

---

### Post by esd2609 on 2006-07-11
Thanks for the help.

I checked and it is both listed and active.

---

### Post by dasyar613 on 2006-07-11
If you do not have to much time invested in this install, I would do another clean install. Sometimes, but not very often, it does not go according to the plan.

You did mention that the live CD allowed you to access the internet, based on that I am thinking that something went bad during the install. During the install, was it able to get the upgrades. You may want to keep an eye open for that. Have fun.

---

### Post by esd2609 on 2006-07-11
I'm going to download a new install disc and try reinstalling.

Thanks again for your help.

---

### Post by esd2609 on 2006-07-13
It turned out to be my Davicom ethernet adapter.  I had to blacklist tulip and it's worked fine after that.

This post helped me figure out that it was the ethernet card:

[http://ubuntuforums.org/showthread.php?t=133599](http://ubuntuforums.org/showthread.php?t=133599)

I ran: tail -f /var/log/syslog

Which showed there was an error with something called tulip which I learned was something to do with Davicom ethernet cards.

And this one walked me through fixing the ethernet problem:

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

