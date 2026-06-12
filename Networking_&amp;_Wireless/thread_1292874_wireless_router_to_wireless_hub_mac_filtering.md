---
title: "wireless router to wireless hub mac filtering"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2009-10-16
my situation, i have 2 wireless routers. one i converted to a wired and wireless hub by disabling dhcp. the cable is plugged into the LAN not WAN of the new access point.

my question is this, i enabled mac filtering on the original first wireless router adding in my wireless devices. But i did not enable any mac filtering on the second wireless router (now a hub)
does the first router know anything about the wireless devices connected to the hub regarding mac filtering? or do you have to set up mac filtering in the second hub as well?

Also, once i turned off DHCP in the second wireless router, (now a hub), i can not access it login anymore. it is getting an adress from the first wireless router. how else can i log in except by doing a reset?

---

### Post by CharlesA on 2009-10-16
Make sure to change the IP of the other router to something other then 192.168.1.1 (or the default whichever it is).

Then type that IP into a browser.

---

### Post by cariboo on 2009-10-16
I have basically the same setup. I gave the access point a static ip address, so I can access it by entering the static ip addresss. The main router handles the dhcp and if I used mac filtering, it would do that to.

If you aren't sure what the ip address of the access point is you can use nmap to find the ip address. This script finds all the ip addresses of all the computers connected to the network

```
sudo nmap -PR -sP 192.168.1.0/24
```

---

### Post by sdowney717 on 2009-10-16
tried various options using zenmap on xp for the moment, but only shows laptop,desktop, main router?
i tried intense scan and got similar result.

> 

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2009-10-16 13:37 Eastern Daylight Time

Interesting ports on wr850g.hr.cox.net (192.168.1.1):

Not shown: 98 closed ports

PORT     STATE SERVICE VERSION

80/tcp   open  http    Linksys wireless-G WAP http config (Name Gateway 11G Router)

5190/tcp open  aol?

MAC Address: 00:0C:10:21:32:01 (PNI)

Device type: general purpose

Running: Linux 2.4.X

OS details: Linux 2.4.18 - 2.4.35 (likely embedded)

Network Distance: 1 hop

Service Info: Device: WAP



Skipping SYN Stealth Scan against scott2-desktop.hr.cox.net (192.168.1.101) because Windows does not support scanning your own machine (localhost) this way.

Skipping OS Scan against scott2-desktop.hr.cox.net (192.168.1.101) because it doesn't work against your own machine (localhost)

0 ports scanned on scott2-desktop.hr.cox.net (192.168.1.101)



Interesting ports on laptop.hr.cox.net (192.168.1.102):

Not shown: 93 filtered ports

PORT     STATE  SERVICE       VERSION

80/tcp   open   http?

135/tcp  open   msrpc?

139/tcp  open   netbios-ssn

443/tcp  open   skype2        Skype

445/tcp  open   microsoft-ds  Microsoft Windows XP microsoft-ds

5000/tcp closed upnp

5009/tcp closed airport-admin

1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [http://www.insecure.org/cgi-bin/servicefp-submit.cgi](http://www.insecure.org/cgi-bin/servicefp-submit.cgi) :

SF-Port80-TCP:V=5.00%I=2%D=10/16%Time=4AD8AF8D%P=i686-pc-windows-windows%r

SF:(GetRequest,1A,"HTTP/1\.0\x20404\x20Not\x20Found\r\n\r\n")%r(HTTPOption

SF:s,58,"\x92%:e\x95\xc8\xb6\xfd\xfaI&\xaa\x07G\xb7\x85P\xf0\x9e\xc2\.\xdd

SF:\x84\xb6\xdf@\t\t\xb6\x88\x171\xf9,%\x0c5z\"&\x142\x1a'\xc9\xde\)\x15jS

SF:\xe89\x16\x0ftU\x82\x8b\xc01\xae\xc7\xcc\xcd\x9a\xc3\x98\)F\x7f\$E\xb2\

SF:xfbp!\xde7\|\xbd\xca3H\x19v\xef\xd45")%r(RTSPRequest,30,"!\xe2/\xad\x1f

SF:\xa0\x83\xa4\xe6\xb2\x9e\xac\x97\xc7d\xea\xf6\xa4\xf6\xcf\x19\xd6\xc0_\

SF:x051\x10k\xd7\x84\xac\xa9\xa9=\x99T\xdc0\xfe\x10_xz'\x97\x0311")%r(Four

SF:OhFourRequest,1A,"HTTP/1\.0\x20404\x20Not\x20Found\r\n\r\n");

MAC Address: 00:13:02:1C:0F:77 (Intel Corporate)

Device type: general purpose

Running: Microsoft Windows 2000|2003

OS details: Microsoft Windows 2000 SP4 or Windows XP SP2 or SP3, Microsoft Windows 2003 Small Business Server

Network Distance: 1 hop

Service Info: OS: Windows



OS and Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .

Nmap done: 256 IP addresses (3 hosts up) scanned in 59.25 seconds



---

