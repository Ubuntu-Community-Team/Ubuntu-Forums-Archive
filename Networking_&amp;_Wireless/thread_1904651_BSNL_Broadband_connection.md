---
title: "BSNL Broadband connection"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by srikrishnan on 2012-01-05
I have installed Ubuntu 11.10 (latest version) as a second OS in my system. First is windows XP. Newly I have bought BSNL broadband connection. It works well in Windows XP. Whereas in Ubuntu it will not automatically detected. (after getting BSNL connection, I have newly installed latest ubuntu version as a fresh copy)

I have tried sudo pppoeconf

it checks the system for sometime and finally it throws the following error:

"Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond. Please check your network and modem cables. Another reason for  the scan failure may also be another running pppoe process which controls the modem."

My System configuration is as follows:

AMD Phenom[tm] 8750
Triple-Core processor
2.40Ghz, 2.87 GB of RAM

My Modem is:

beetel
220BX
ADSL2 + MODEM

Can anybody helpme to solve this problem?

Thanks in Advance,
Srikrishnan

---

### Post by KrisDouglas on 2012-01-05
USB modems are never that great. A good option if it is available to you is to get a router which supports wireless/ Ethernet. They are relatively cheap now. 

Someone seems to have been able to work out the soltion here, it's an old post but I would imagine it would work. 

[http://www.honeytechblog.com/configuring-airtel-beetel-220bx-in-ubuntu/](http://www.honeytechblog.com/configuring-airtel-beetel-220bx-in-ubuntu/)

---

### Post by vasa1 on 2012-01-05
> **KrisDouglas said:**
> USB modems are never that great. ...
It wasn't clear to me that OP was connecting via USB.

---

### Post by KrisDouglas on 2012-01-05
> **vasa1 said:**
> It wasn't clear to me that OP was connecting via USB.

beetel 220BX is a USB device.

---

### Post by rahul_bhise on 2012-01-05
have you added a connection in network manager.
i.e.= go to system > preferences > network connection and in the wired tab click the add button then in ipv4 setting tab add the ip addresses of PC, gateway and dns. then click save.try to connect to the net by clicking on network manager icon in the taskbar and then on the newly added connection. then in Firefox goto ip address of gateway and in the adsl modem put the username and password give by bsnl in the appropriate place, and click save.

---

### Post by srikrishnan on 2012-01-06
Hi all,

Thanks for your reply.

my modem is not an usb modem.

it has been connected through network cord

Thanks,
Srikrishnan

---

### Post by dineshs on 2012-01-09
> I have tried sudo pppoeconf
sudo pppoeconf is required only if your modem is in bridge mode.Are you using a dialler in windows?
Please open a terminal and post the result of ```
sudo lshw -C network
```when the modem is connected and switched ON

---

