---
title: "Setting up static IP"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by bcraig24 on 2010-10-28
I just purchased a static IP from my ISP so I can setup VPN.

I have Ubuntu 10.04LTS 64bit on my server and I use a vista laptop and windows 7 desktop to browse files and webserver and VNC remote desktop to Ubuntu.

I also hope to use VNC from my iPhone too.

I am using a Huawei hg520s wireless modem.

How do I go about setting up my static IP? Do I need to purchase a a router?

---

### Post by SeijiSensei on 2010-10-28
[You have a router as far as I can tell]("http://www.3gmodem.com.hk/Router/HUAWEI-HG520s.html").

Visit [http://whatsmyip.org/](http://whatsmyip.org/) and see if your public IP address matches the static one that you obtained from your provider.  If not, the ISP needs to fix that.  If it does match, you need to look into port forwarding through the Huawei device.

---

### Post by bcraig24 on 2010-10-29
Yep my IP is set. How do I point the IP to my local apache server on Ubuntu??

---

### Post by SeijiSensei on 2010-10-29
As I said,

> **SeijiSensei said:**
> **you need to look into port forwarding through the Huawei device.**

---

### Post by bcraig24 on 2010-10-30
I am now using a D-Link DSL-526B modem and Netgear N600 WNDR3700 router.

So far Ive got my static IP to pull up my modem webpage.
But how do I forward that to my router and then to my private IP of my webserver??

In my D-Link modem I have added a NAT - Virtual Server...

Server Name - webserver
External Port Start - 80
External Port End	- 80
Protocol - TCP/UDP
Internal Port Start - 80
Internal Port End - 80
Server IP Address - 192.168.1.3
Remote Host - 192.168.1.1

---

### Post by SeijiSensei on 2010-10-31
Try [http://portforward.com/](http://portforward.com/).

---

### Post by bcraig24 on 2010-11-02
My issue was I was trying to double port forward from modem to router to pc.

I fixed this by directly wiring my server pc to the modem on lan1 and my router off lan2.

---

