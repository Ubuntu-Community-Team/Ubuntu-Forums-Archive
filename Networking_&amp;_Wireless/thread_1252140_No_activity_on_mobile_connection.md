---
title: "No activity on mobile connection"
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by Dy1anW on 2009-08-28
I've read about people having problems just trying to connect with those USB Vodems, and thought I'd have that as well, but the problem turned out to be something entirely different.

I'm using a Huawei E172; which having been plugged into my lapbomb, was instantly recognised by linux, and I set the Network Manager to connect automatically... and it does connect (at least the NM says it's connected, and the vodem lights blue).  The problem is that I get no data transfer at all.  No matter what I do, I always time out.

I've had a chat with Vodafone's "technical support", and all they said on the matter was that's it's impossible to run it on linux, and I would have to use it on another computer running Windows or OSX.  Since he's clearly out of his depth, does anyone else have an idea?

P.S. I've also read about VMC for linux by BetaVine (but also read that the current NM is better suited); tried installing it anyway, but was halted due to a dependency on ozerocdoff, which there's no package for as far as I can tell.

---

### Post by GeorgeVita on 2009-08-28
Hi **Dy1anW**,
as you are connected (blue light) via network manager, check APN and if you can get IP and DNS numbers. The simpler is to right click on network manager icon and then 'Connection information'.

Post also here country/provider and Ubuntu version to check.

Regards,
George

---

### Post by Dy1anW on 2009-08-28
Hi, thanks for the response.

This is the output from NM's connection information:

Interface: GSM (ttyUSB0)
Hardware Address: 
Driver: option
Speed: Unknown (that doesn't sound promising)
Security: Unknown

And then there's a list of IPv4 addresses for local, broadcast, default route, primary and secondary DNS, so it's definitely connected to something!

Extra info:
Location: Hong Kong
Provider: Smartone-Vodafone
OS: Ubuntu 9.04

---

### Post by GeorgeVita on 2009-08-29
Hi **Dy1anW**, as everything seems to be ok (!) just some ideas to check:

- Edit connection (from nm icon) and under IPv4 tab select automatic PPP (and not addresses only).
 APN=internet, phone=*99#

- disconnect ethernet and wifi (to remove anh conflict) and try again

- from terminal check the DNS (nm set them) ```
cat /etc/resolv.conf
``` and status of ppp0 ```
ifconfig ppp0
```

From 'Connection information' my data are:
ttyUSB0 option1 Unknown Unknown (as yours)
IP 212.152.123.456
broadcast address the same as IP
subnet mask 255.255.255.255
default route 10.64.64.64
primary DNS 212.152.70.6
secondary DNS 212.152.70.7

vodafone worldwide gives some help for linux (Betavine) so they cannot say 'it's impossible to run it on linux'. OK they don't 'typically' support it but it can be used. The info you must check from them is APN and user/password. You need this info if you have to setup an internet profile for a smart phone.

Finally I do not know if you can extract some info from windows 'modem log file' (control panel, modem properties, enable and later view log file?).

Regards,
George

---

### Post by Dy1anW on 2009-08-29
Ahh, that's got it!  Changed the PPP setting to automatic as suggested and recycled the vodem; my DNS went from 10.206.65.68 and 10.203.65.68 to 202.140.83.51 and 202.150.96.51 respectively, and now I'm actually getting data transfer.  So it all turned out to be an issue that domain names weren't being resolved! *facepalm* (maybe it's just at my end, but those original nameservers don't seem to exist).

Anyway, thanks for that! :P

---

