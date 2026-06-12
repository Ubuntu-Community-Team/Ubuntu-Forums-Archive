---
title: "no wireless and some info"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by Pedroski55 on 2013-02-06
Hi. At home my wireless does not work if I use Ubuntu, or Fedora. It works with Windows. I have wondered about this for at least 2 years now, hoping an update might fix it. Recently I got an Android phone. It also cannot connect to my home wifi. Sorry, that is, my laptop and my mobile say they are connected, but there is no internet connection. So they connect to the router, but not to the internet. What else do I need??

Someone told me to run this on my laptop:

pedro@pedro-bedro:~$ nslookup web.qq.com
Server:        127.0.0.1
Address:    127.0.0.1#53

Non-authoritative answer:
web.qq.com    canonical name = web2.qq.com.
Name:    web2.qq.com
Address: 183.60.3.84
Name:    web2.qq.com
Address: 183.62.126.217
Name:    web2.qq.com
Address: 183.60.3.126
Name:    web2.qq.com
Address: 121.14.74.112

pedro@pedro-bedro:~$ 

**and at the same time run this:**

pedro@pedro-bedro:~$ sudo tcpdump -i wlan0 -vn port 53
[sudo] password for pedro: 
tcpdump: listening on wlan0, link-type EN10MB (Ethernet), capture size 65535 bytes
07:05:09.322452 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 55)
    192.168.1.4.44891 > 192.168.1.1.53: 51356+ A? baidu.com. (27)
07:05:09.325613 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 55)
    192.168.1.1.53 > 192.168.1.4.44891: 51356 Refused 0/0/0 (27)
07:05:30.678848 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 60)
    192.168.1.4.34747 > 192.168.1.1.53: 24042+ A? tj.qstatic.com. (32)
07:05:30.683109 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 60)
    192.168.1.1.53 > 192.168.1.4.34747: 24042 Refused 0/0/0 (32)
07:06:10.289010 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.4.58841 > 192.168.1.1.53: 42198+ A? nboard.nciku.com. (34)
07:06:10.292560 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.1.53 > 192.168.1.4.58841: 42198 Refused 0/0/0 (34)
07:06:42.671737 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.4.7091 > 192.168.1.1.53: 3138+ A? [www.bbc.co.uk]("http://www.bbc.co.uk"). (31)
07:06:42.674722 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.1.53 > 192.168.1.4.7091: 3138 Refused 0/0/0 (31)
07:07:10.290107 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.4.58863 > 192.168.1.1.53: 33531+ A? nboard.nciku.com. (34)
07:07:10.293262 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.1.53 > 192.168.1.4.58863: 33531 Refused 0/0/0 (34)
07:07:43.855657 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.4.32039 > 192.168.1.1.53: 32512+ A? [www.bbc.co.uk]("http://www.bbc.co.uk"). (31)
07:08:10.288994 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.4.17200 > 192.168.1.1.53: 37366+ A? nboard.nciku.com. (34)
07:08:10.291992 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.1.53 > 192.168.1.4.17200: 37366 Refused 0/0/0 (34)
07:08:45.080348 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.4.14305 > 192.168.1.1.53: 30877+ A? [www.bbc.co.uk]("http://www.bbc.co.uk"). (31)
07:08:45.083224 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.1.53 > 192.168.1.4.14305: 30877 Refused 0/0/0 (31)
07:09:10.287703 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.4.14023 > 192.168.1.1.53: 39037+ A? nboard.nciku.com. (34)
07:09:10.291137 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.1.53 > 192.168.1.4.14023: 39037 Refused 0/0/0 (34)
07:09:46.305470 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.4.30784 > 192.168.1.1.53: 57327+ A? [www.bbc.co.uk]("http://www.bbc.co.uk"). (31)
07:09:46.308706 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.1.53 > 192.168.1.4.30784: 57327 Refused 0/0/0 (31)
^C
19 packets captured
19 packets received by filter
0 packets dropped by kernel
pedro@pedro-bedro:~$ 

I don't know what 'tcpdump -i wlan0 -vn port 53' does, but I can see, there are a lot of 'Refused' and my wifi does not work.

Maybe there is a connection?? Can it be changed to 'Accepted'???

---

### Post by thenox on 2013-02-07
Hi Pedroski55,

I have had similar issues. Could we get the hardware and software specifications? What is the:
Version of Ubuntu
Wireless card
Wireless router
Computer specs

Also, try typing "ifconfig" (without the quotes) in a terminal

Could you post the output in code tags? Just select the text from the command and hit the # button in the reply window.

Example:
```
pedro@pedro-bedro:~$ sudo tcpdump -i wlan0 -vn port 53
[sudo] password for pedro: 
tcpdump: listening on wlan0, link-type EN10MB (Ethernet), capture size 65535 bytes
07:05:09.322452 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 55)
    192.168.1.4.44891 > 192.168.1.1.53: 51356+ A? baidu.com. (27)
07:05:09.325613 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 55)
    192.168.1.1.53 > 192.168.1.4.44891: 51356 Refused 0/0/0 (27)
07:05:30.678848 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 60)
    192.168.1.4.34747 > 192.168.1.1.53: 24042+ A? tj.qstatic.com. (32)
07:05:30.683109 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 60)
    192.168.1.1.53 > 192.168.1.4.34747: 24042 Refused 0/0/0 (32)
07:06:10.289010 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.4.58841 > 192.168.1.1.53: 42198+ A? nboard.nciku.com. (34)
07:06:10.292560 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.1.53 > 192.168.1.4.58841: 42198 Refused 0/0/0 (34)
07:06:42.671737 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.4.7091 > 192.168.1.1.53: 3138+ A? [www.bbc.co.uk]("http://www.bbc.co.uk"). (31)
07:06:42.674722 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.1.53 > 192.168.1.4.7091: 3138 Refused 0/0/0 (31)
07:07:10.290107 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.4.58863 > 192.168.1.1.53: 33531+ A? nboard.nciku.com. (34)
07:07:10.293262 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.1.53 > 192.168.1.4.58863: 33531 Refused 0/0/0 (34)
07:07:43.855657 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.4.32039 > 192.168.1.1.53: 32512+ A? [www.bbc.co.uk]("http://www.bbc.co.uk"). (31)
07:08:10.288994 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.4.17200 > 192.168.1.1.53: 37366+ A? nboard.nciku.com. (34)
07:08:10.291992 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.1.53 > 192.168.1.4.17200: 37366 Refused 0/0/0 (34)
07:08:45.080348 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.4.14305 > 192.168.1.1.53: 30877+ A? [www.bbc.co.uk]("http://www.bbc.co.uk"). (31)
07:08:45.083224 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.1.53 > 192.168.1.4.14305: 30877 Refused 0/0/0 (31)
07:09:10.287703 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.4.14023 > 192.168.1.1.53: 39037+ A? nboard.nciku.com. (34)
07:09:10.291137 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 62)
    192.168.1.1.53 > 192.168.1.4.14023: 39037 Refused 0/0/0 (34)
07:09:46.305470 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.4.30784 > 192.168.1.1.53: 57327+ A? [www.bbc.co.uk]("http://www.bbc.co.uk"). (31)
07:09:46.308706 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 59)
    192.168.1.1.53 > 192.168.1.4.30784: 57327 Refused 0/0/0 (31)
^C
19 packets captured
19 packets received by filter
0 packets dropped by kernel
pedro@pedro-bedro:~$ 
```

Makes it cleaner :)

---

