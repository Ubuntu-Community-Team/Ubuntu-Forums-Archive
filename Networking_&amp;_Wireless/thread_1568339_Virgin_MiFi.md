---
title: "Virgin MiFi"
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by boondocks on 2010-09-05
Has anyone tried this Virgin MiFi (hotspot) via WiFi with a Ubuntu laptop?
[LIST]
[*]Unlimited data plan (no 5-gigabyte data limit)
[*]No contract
[*]$40 per month
[*]3G speed
[/LIST]
The device itself costs $150.
How is it?  Reliable?  

I came across it at:
[http://www.nytimes.com/2010/09/02/technology/personaltech/02pogue.html?_r=1&sq=virgin%20MiFi](http://www.nytimes.com/2010/09/02/technology/personaltech/02pogue.html?_r=1&sq=virgin%20MiFi)

---

### Post by ddettore on 2010-09-16
> **boondocks said:**
> Has anyone tried this Virgin MiFi (hotspot) via WiFi with a Ubuntu laptop?
[LIST]
[*]Unlimited data plan (no 5-gigabyte data limit)
[*]No contract
[*]$40 per month
[*]3G speed
[/LIST]
The device itself costs $150.
How is it?  Reliable?  

I came across it at:
[http://www.nytimes.com/2010/09/02/technology/personaltech/02pogue.html?_r=1&sq=virgin%20MiFi](http://www.nytimes.com/2010/09/02/technology/personaltech/02pogue.html?_r=1&sq=virgin%20MiFi)


You might check out walmart - It is a little cheaper there ... I use the mobile2go and it works great in windows - I have a little trouble in Ubuntu 10.04 - However I find by connecting using sprint rathen then Virgen/heleo I get  better results... 

If someone has a good fix to speed it up a little  I'd like to hear it...

---

### Post by eehouse@eehouse.org on 2011-01-01
I've had one for about a week -- paid about $142 with tax and shipping direct from Virgin -- and it's great so far.  I'm using an Ubuntu netbook (Samsung) and family members have connected using Dell/Debian and MacOS laptops and a Cruz Android tablet.

The WiFi router in the thing provides rudimentary firewall features such as port forwarding.  So in theory I could host a webserver on my netbook.  Only certain ports are supported, e.g. www and telnet but not ssh.

The only problem I've had so far is in trying to add an entry to my home machine's /etc/hosts.allow so that I can get in from my netbook using the MiFi.  The IP address reported to be the outbound interface of the MiFi is quite different from the address that my home machine reports it's trying to connect from (but not in the private Class A-C ranges either).  Neither address resolves to anything sensible -- so I can't put something analogous to the "sshd: .pools.spcsdns.net" that lets me connect from an ssh client on a Sprint smartphone.

--Eric

---

### Post by boondocks on 2011-01-02
> **eehouse@eehouse.org said:**
> I've had one for about a week -- paid about $142 with tax and shipping direct from Virgin -- and it's great so far.  I'm using an Ubuntu netbook (Samsung) and family members have connected using Dell/Debian and MacOS laptops and a Cruz Android tablet.

The WiFi router in the thing provides rudimentary firewall features such as port forwarding.  So in theory I could host a webserver on my netbook.  Only certain ports are supported, e.g. www and telnet but not ssh.

The only problem I've had so far is in trying to add an entry to my home machine's /etc/hosts.allow so that I can get in from my netbook using the MiFi.  The IP address reported to be the outbound interface of the MiFi is quite different from the address that my home machine reports it's trying to connect from (but not in the private Class A-C ranges either).  Neither address resolves to anything sensible -- so I can't put something analogous to the "sshd: .pools.spcsdns.net" that lets me connect from an ssh client on a Sprint smartphone.

--Eric
All this is very good to know.  Thank you.
If possible, can you give a general idea of where (geographically) you have used the MiFi?
Don't need to be specific, North ... or South ...  is good enough.

---

