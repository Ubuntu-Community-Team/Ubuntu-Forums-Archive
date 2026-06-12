---
title: "Understanding what UFW is saying"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by xsyw9998 on 2010-10-20
Greetings all,

I'm having a bit of trouble understanding what UFW is trying to tell me.

Environment: Laptop running Meerkat 10.10 connected to Speedstream 4200 DSL modem/router via eth0. Application is attempting to use port 7812 (Retroshare), UFW emits the following:

[UFW BLOCK] IN=eth0 OUT= MAC=[my-mac-address] SRC=192.168.254.254 DST=192.168.254.1 LEN=340 TOS=0x16 PREC=0x40 TTL=64 ID=11804 PROTO=UDP SPT=1900 DPT=34218 LEN=320 

Router info:
* uPNP enabled, full Internet Gateway Device (IGD) support
* DHCP enabled (range: 192.168.254.1 to 192.168.254.253, default gateway = 192.168.254.254)
* No port forwarding enabled at the present time
* "NAPT Only" Enabled

UFW rules:
To       Action          From
--        ------           ----
7812   ALLOW IN     Anywhere
7812   ALLOW OUT  Anywhere

The question: Given that OUT= is blank, is UFW saying that a *listen* request is being blocked? The SRC/DST addresses are confusing as well: the source appears to be the gateway/router and DST is eth0 address. What's up with that?? I'm assuming that if UFW stops complaining that my outbound messages are making it out to the 'net and my listen requests are being fulfilled...but I could use some clarification and advice on this.

Retroshare's documentation is scant...but I *really* want to get this working....

---

### Post by SeijiSensei on 2010-10-20
> **xsyw9998 said:**
> [UFW BLOCK] IN=eth0 OUT= MAC=[my-mac-address] SRC=192.168.254.254 DST=192.168.254.1 LEN=340 TOS=0x16 PREC=0x40 TTL=64 ID=11804 PROTO=UDP SPT=1900 DPT=34218 LEN=320

It looks like the host is sending a UDP packet to the router at 254.1. Looking up source port 1900 suggests it might be part of the [uPNP discovery process]("http://www.google.com/search?q=source+port+1900").

---

