---
title: "[SOLVED] Upgraded from 10.04 to 12.04, Wii-U suddenly can't connect."
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by deadtom on 2013-06-15
I have a PC acting as a firewall and router, using iptables. We have a Wii-U inside the network and until a few days ago, it was able to connect to the internet just fine. I upgraded the firewall PC from 10.04 to 12.04 and suddenly the Wii-U cannot connect.

I do an internet connection test in the Wii-U and it passes but it can't connect to any services such as Hulu, Netflix, the Nintendo e-shop channel or anything else.

I have no rules in place restricting the Wii-U at all. I do a grep in syslog for the Wii-U's IP and nothing comes up.

I also have several PC's, three Android devices, two Nintendo DS's, an old Xbox, a PSP and a PS3 and none of them have experienced any problems since the upgrade, they're all able to connect fine.

I checked Nintendo's support site and their advice is to forward all ports (specifically 1-65535) to the Wii-U, which I can't do for obvious reasons. 

Would anyone have any idea what might be preventing it from connecting? There has to be a change in the way that iptables or something else on the system is routing traffic, that doesn't agree with the Wii-U. Perhaps some way to at least turn up the verbosity of the firewall log? Or could it be a DNS thing? I have Bind9 handling DNS on that PC as well.

Thanks!

---

### Post by deadtom on 2013-06-15
Wait, I've been watching it for a while and something started to come up:

> $ sudo tail -f /var/log/syslog | grep 58.38
Jun 15 20:22:05 aragorn dhcpd: DHCPOFFER on 192.168.58.38 to 18:2a:7b:85:09:e5 via eth0
Jun 15 20:22:05 aragorn dhcpd: DHCPREQUEST for 192.168.58.38 (192.168.58.1) from 18:2a:7b:85:09:e5 via eth0
Jun 15 20:22:05 aragorn dhcpd: DHCPACK on 192.168.58.38 to 18:2a:7b:85:09:e5 via eth0
Jun 15 20:22:20 aragorn dhcpd: DHCPOFFER on 192.168.58.38 to 18:2a:7b:85:09:e5 via eth0
Jun 15 20:22:20 aragorn dhcpd: DHCPREQUEST for 192.168.58.38 (192.168.58.1) from 18:2a:7b:85:09:e5 via eth0
Jun 15 20:22:20 aragorn dhcpd: DHCPACK on 192.168.58.38 to 18:2a:7b:85:09:e5 via eth0
Jun 15 20:24:05 aragorn kernel: [21091.046570] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=339 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0 
Jun 15 20:24:05 aragorn kernel: [21091.848365] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=351 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0 
Jun 15 20:24:07 aragorn kernel: [21093.842142] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=355 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0                                                                                                                          
Jun 15 20:24:11 aragorn kernel: [21097.841679] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=366 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0                                                                                                                          
Jun 15 20:24:19 aragorn kernel: [21105.841724] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=388 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0                                                                                                                          
Jun 15 20:24:35 aragorn kernel: [21121.859395] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=391 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0                                                                                                                          
Jun 15 20:25:07 aragorn kernel: [21153.877525] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=69.25.139.191 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=396 PROTO=TCP SPT=4635 DPT=443 WINDOW=8192 RES=0x00 ACK FIN URGP=0                                                                                                                        
Jun 15 20:25:07 aragorn kernel: [21153.877757] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=397 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0                                                                                                                          
Jun 15 20:26:11 aragorn kernel: [21216.916384] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=96.7.66.90 LEN=1042 TOS=0x00 PREC=0x00 TTL=63 ID=405 PROTO=TCP SPT=4636 DPT=443 WINDOW=32768 RES=0x00 ACK PSH FIN URGP=0                                                                                                                    
Jun 15 20:26:12 aragorn kernel: [21217.913734] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=69.25.139.191 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=406 PROTO=TCP SPT=4635 DPT=443 WINDOW=8192 RES=0x00 ACK FIN URGP=0                                                                                                                        
Jun 15 20:26:12 aragorn kernel: [21217.914274] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=407 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0 
Jun 15 20:27:15 aragorn kernel: [21280.968090] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=96.7.66.90 LEN=1042 TOS=0x00 PREC=0x00 TTL=63 ID=435 PROTO=TCP SPT=4636 DPT=443 WINDOW=32768 RES=0x00 ACK PSH FIN URGP=0 
Jun 15 20:27:16 aragorn kernel: [21281.971034] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=69.25.139.191 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=436 PROTO=TCP SPT=4635 DPT=443 WINDOW=8192 RES=0x00 ACK FIN URGP=0 
Jun 15 20:27:16 aragorn kernel: [21281.971307] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=437 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0 
Jun 15 20:28:19 aragorn kernel: [21345.030400] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=96.7.66.90 LEN=1042 TOS=0x00 PREC=0x00 TTL=63 ID=444 PROTO=TCP SPT=4636 DPT=443 WINDOW=32768 RES=0x00 ACK PSH FIN URGP=0 
Jun 15 20:28:20 aragorn kernel: [21346.034619] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=69.25.139.191 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=445 PROTO=TCP SPT=4635 DPT=443 WINDOW=8192 RES=0x00 ACK FIN URGP=0 
Jun 15 20:28:20 aragorn kernel: [21346.035244] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=446 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0 
Jun 15 20:29:23 aragorn kernel: [21409.052440] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=96.7.66.90 LEN=1042 TOS=0x00 PREC=0x00 TTL=63 ID=454 PROTO=TCP SPT=4636 DPT=443 WINDOW=32768 RES=0x00 ACK PSH FIN URGP=0 
Jun 15 20:29:24 aragorn kernel: [21410.052648] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=69.25.139.191 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=455 PROTO=TCP SPT=4635 DPT=443 WINDOW=8192 RES=0x00 ACK FIN URGP=0 
Jun 15 20:29:24 aragorn kernel: [21410.052846] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=456 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0 
Jun 15 20:30:27 aragorn kernel: [21473.109959] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=96.7.66.90 LEN=1042 TOS=0x00 PREC=0x00 TTL=63 ID=463 PROTO=TCP SPT=4636 DPT=443 WINDOW=32768 RES=0x00 ACK PSH FIN URGP=0 
Jun 15 20:30:28 aragorn kernel: [21474.101616] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=69.25.139.191 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=464 PROTO=TCP SPT=4635 DPT=443 WINDOW=8192 RES=0x00 ACK FIN URGP=0 
Jun 15 20:30:28 aragorn kernel: [21474.101908] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=465 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0 
Jun 15 20:31:31 aragorn kernel: [21537.148920] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=96.7.66.90 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=472 PROTO=TCP SPT=4636 DPT=443 WINDOW=32768 RES=0x00 ACK RST URGP=0 
Jun 15 20:31:32 aragorn kernel: [21538.151828] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=69.25.139.191 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=473 PROTO=TCP SPT=4635 DPT=443 WINDOW=8192 RES=0x00 ACK FIN URGP=0 
Jun 15 20:31:32 aragorn kernel: [21538.152113] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=474 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK FIN URGP=0 
Jun 15 20:32:36 aragorn kernel: [21602.209008] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=69.25.139.191 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=482 PROTO=TCP SPT=4635 DPT=443 WINDOW=8192 RES=0x00 ACK RST URGP=0 
Jun 15 20:32:36 aragorn kernel: [21602.209114] Invalid packet: IN=eth0 OUT=eth1 MAC=00:c0:f0:2d:9e:b4:18:2a:7b:85:09:e5:08:00 SRC=192.168.58.38 DST=72.21.91.29 LEN=40 TOS=0x00 PREC=0x00 TTL=63 ID=483 PROTO=TCP SPT=4649 DPT=80 WINDOW=32768 RES=0x00 ACK RST URGP=0 


Um... can anyone translate?

---

### Post by deadtom on 2013-06-16
Other things I've tried:

I've opened the firewall up completely, allowing all traffic through.
I've explicitly allowed all traffic on all ports, to and from the Wii-U.
I've tried running several older kernels.
I've tried shutting down apparmor.

None of these have worked.

---

### Post by ahallubuntu on 2013-06-16
~

---

### Post by deadtom on 2013-06-16
I'm not convinced that it's iptables. It might be something else that's going on, which is why I tried an earlier kernel and tried disabling apparmor. No dice though.

It's a real stumper.

I just posted on linuxquestions.org and a few other places as well. I'm hoping someone smarter than me has some idea about what's going on.

Thanks for having a look though.

---

### Post by deadtom on 2013-06-20
After considerable toil and turmoil, I found the source of the problem. I had suspected an MTU issue early on but after tweaking settings on my wireless routers, my firewall and the Wii-U, I gave up on that idea. In desperation, I decided to revisit the possibility yesterday and came across this article:

[http://fabiobaltieri.com/2011/09/12/iptables-firewall-nat/](http://fabiobaltieri.com/2011/09/12/iptables-firewall-nat/)

A little better than half way down the page, I came to this:

> ...[COLOR=#555555][FONT=Arial]On the other side, if you are using that node as a NAT router, the systems behind it have no way to know the real MTU of the PPPoE interface. Therefore the systems will try to use packets bigger than the maximum allowed, which will be dropped without warning by routers.
[/FONT][/COLOR][COLOR=#555555][FONT=Arial]The solution for that, unless you want to configure all your devices with a reduced MTU, is to instruct the routing host to intercept all the TCP handshake packets and correct in-fly the wrong MSS value requested by internal hosts...[/FONT][/COLOR]

The following rule took care of that:

```
[COLOR=#555555]iptables -t mangle -A FORWARD -p tcp --tcp-flags SYN,RST SYN [/COLOR][COLOR=#555555]-j TCPMSS --clamp-mss-to-pmtu[/COLOR]
```

Applied the changes to iptables.rules, rebooted the Wii-U and viola! Problem solved.

---

### Post by ekeyser2 on 2014-05-26
Thank you so much!

---

