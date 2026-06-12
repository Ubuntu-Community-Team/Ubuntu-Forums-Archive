---
title: "Endless hits, please, help."
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by oefuin on 2010-11-29
Hi!
I'm using ubuntu 10.04. I need some help with Internet security. Someone is trying to break into the network 24/7, using range of IPs starting with 184.  and using ports 40000 to 56000.  
My Firestarter events log looks like this:
[I]Time:Nov 29 13:42:51 Direction: Unknown In:wlan0 Out: Port:39321 Source:184.105.146.17 Destination:192.168.1.72 Length:40 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov 29 13:49:01 Direction: Unknown In:wlan0 Out: Port:33263 Source:184.105.146.11 Destination:192.168.1.72 Length:40 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov 29 13:49:01 Direction: Unknown In:wlan0 Out: Port:33264 Source:184.105.146.11 Destination:192.168.1.72 Length:40 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov 29 13:49:45 Direction: Unknown In:wlan0 Out: Port:57348 Source:184.105.146.17 Destination:192.168.1.72 Length:40 TOS:0x00 Protocol:TCP Service:Unknown
Time:Nov 29 13:49:45 Direction: Unknown In:wlan0 Out: Port:57347 Source:184.105.146.17 Destination:192.168.1.72 Length:40 TOS:0x00 Protocol:TCP Service:Unknown[/I]
I'm using 2WIRE wireless router, and I set up ISP firewall on “Maximum protection*–*Disallow unsolicited inbound traffic”, with MAC filtering option turned on, Stealth Mode, Block Ping, Strict UDP Session Control. 
Inbound and Outbound Control was set to disallow all inbound traffic, and allow outbound traffic only for  HTTP, HTTPS, 
FTP.
I wonder what does it mean and how to deal with it.
Any help would be greatly appreciated.
Thank you.
P.S. I captured packets on several occasions, using Wireshark, just in case. Please, let me know if that would help to determine what is going on.

---

### Post by theDaveTheRave on 2010-11-29
oefuin,

firstly I would download a copy of a tool called nmap
```

sudo apt-get nmap
```

then using the tool you can determine what the attacker has open,and some extra info, here is the result that I just ran on the ip address you supplied as being the source of the attacks.

```

nmap -A 184.105.146.17

Starting Nmap 5.00 ( http://nmap.org ) at 2010-11-30 00:49 CET
Interesting ports on hosted.by.ioflood.com (184.105.146.17):
Not shown: 990 closed ports
PORT     STATE SERVICE        VERSION
22/tcp   open  ssh            OpenSSH 4.3 (protocol 2.0)
|  ssh-hostkey: 1024 63:a3:e6:6d:be:d2:d9:1b:4c:23:de:e8:7e:2f:1b:6f (DSA)
|_ 2048 0a:27:bd:a1:59:b9:c2:cc:20:f8:e3:08:10:36:8b:e2 (RSA)
80/tcp   open  http-proxy     Squid webproxy
81/tcp   open  http           Apache httpd
|  robots.txt: has 2 disallowed entries 
|_ /index.php/0* /index.php/1*
82/tcp   open  http           Apache httpd
|_ html-title: Vtunnel.com is here to help you beat internet filtering!
|  robots.txt: has 2 disallowed entries 
|_ /index.php/0* /index.php/1*
83/tcp   open  http           Apache httpd
|_ html-title: Vtunnel.com is here to help you beat internet filtering!
|  robots.txt: has 2 disallowed entries 
|_ /index.php/0* /index.php/1*
111/tcp  open  rpcbind
|  rpcinfo:  
|  100000  2    111/udp  rpcbind  
|  100024  1    717/udp  status   
|  100000  2    111/tcp  rpcbind  
|_ 100024  1    720/tcp  status   
443/tcp  open  ssl/http-proxy Squid webproxy
|_ sslv2: server still supports SSLv2
720/tcp  open  rpcbind
3306/tcp open  mysql          MySQL (unauthorized)
5666/tcp open  tcpwrapped

Service detection performed. Please report any incorrect results at http://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 139.30 seconds
```

A quick look at the ioflood.com site tells me that they are VPS suppliers. This is good, if you can prove that the attacks are comming from there they will probably be happy to take action against the offending party on your behalf.

Next I put in the IP address to the browser, [http://184.105.146.17/](http://184.105.146.17/)
and it belongs to vtunnel.com -  read thier site

I'm not sure what that tells you though!

I would also run an nmap against your 'router' (if you have one) and any other pc or servers that are open directly to the internet. If you are running a web server, you may of course be being hit my someone 'masquerading' their IP address..

Next off you will want to look at your IP tables rules (or whatever you use for your fifewall, and start blocking your open portsto reduce you 'inbound traffic')

Elswhere you will find a large number of things on how to harden your linux box security.

Otherwise I'm not going to be much more help, other than to ask how you realised this was occuring in the first place?

David

---

