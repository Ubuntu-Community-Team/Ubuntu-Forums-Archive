---
title: "PPTP VPN not working over 3g connection LCP: timeout sending Config-Requests"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by marxlv on 2012-03-27
Hi!

I have a problem with getting my PPTP VPN connection to Microsoft VPN server to work over 3g. PPTP VPN works over every single Wi-Fi or ethernet  network I tried. However  PPTP VPN **over 3g** status is:

[LIST]
[*]kubuntu 10.04 - does not work
[*]kubuntu 11.10 - does not work
[*]Windows 7 32bit -does work
[/LIST]
Hardware:

[LIST]
[*]Fujistu-Siemens P1610 Laptop with iwl3945
[*]Huawei e230 USB 3g dongle
[/LIST]
I have tried setting/unsetting compression/etc in PPTP VPN connection options but nothing works.
I have read many threads about the error and symptoms that I am having:

[LIST]
[*]pppd[xxxx]: LCP: timeout sending Config-Requests
[/LIST]
almost every time resolve in firewall/router configuration. But I have no control over 3g provider and PPTP VPN actually works in Windows 7 32bit, so the problem must be somewhere in configuration. I have found that sometimes setting:

[LIST]
[*]receive-all
[*]noccp
[/LIST]
options help, but I have tried to add them both to /etc/ppp/options and /etc/ppp/options.pptp and it did not help.
So if anyone knows how to:

[LIST]
[*]solve this problem
[*]add receive-all and noccp options to configuration
[*]add some more debug output to configuration (stuff at pptpclient.sourceforge.net did not work for me)
[/LIST]
please help.

Attached are two files with syslog from connection times over WiFi and over 3g.

--
Marx.

---

### Post by marxlv on 2012-04-24
I have some progress - after installing Huawei Mobile Partner on fresh kubuntu 10.04 PPTP connection works sometimes, but only if run sudo pon mypptp several times (anywhere from 2 to 5) in succession. Why does that happen - is this a software bug or is it a network issue?
Also I noticed two rather unpleasant things:
1. Huawei Mobile Partner messes with /etc/sudoers and I no longer have to provide password for sudo. :o
2. Huawei Mobile Partner uses own version of pppd - is there a source for the modification available? Huawei's pppd has several options which are not available in "regular" pppd.

--
Marx.

---

