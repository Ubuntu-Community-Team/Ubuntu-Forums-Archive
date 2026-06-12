---
title: "trying to connect to the Internet"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by slvfx on 2009-09-30
I did something that caused me to loose my connection to the Internet. I recently set up a linux desktop while running a server also. Everything was working fine. I started to work with apache through proftpd not being familiar with what I was doing. Then went to ubuntu essentials which I really like working with but anyway I am down. I have posted a couple of times and I got some suggestions but in many of the cases when I try to run a utility I get a message during installation that it can't check for upgrades so it doesn't install.
 
Is there a program that I can run which will sniff out the connection and update the config. so I can connect?
 
Here is some info
 
[FONT=Batang][SIZE=3]config[/SIZE][/FONT]
[SIZE=3][FONT=Batang]eth0      Link encap:Ethernet  HWaddr 00:24:8c:55:c8:a3  [/FONT][/SIZE]
[SIZE=3][FONT=Batang]          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          inet6 addr: fe80::224:8cff:fe55:c8a3/64 Scope:Link[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX packets:6495 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          TX packets:570 errors:0 dropped:0 overruns:0 carrier:1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX bytes:1330697 (1.3 MB)  TX bytes:112543 (112.5 KB)[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          Memory:dffc0000-e0000000[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[SIZE=3][FONT=Batang]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX packets:37 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          TX packets:37 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX bytes:23179 (23.1 KB)  TX bytes:23179 (23.1 KB)[/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Batang]pan0      Link encap:Ethernet  HWaddr 92:06:47:ec:18:0a  [/FONT][/SIZE]
[SIZE=3][FONT=Batang]          inet6 addr: fe80::9006:47ff:feec:180a/64 Scope:Link[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Batang]          RX bytes:0 (0.0 B)  TX bytes:636 (636.0 B)[/FONT][/SIZE]
---------------------------------------------------------------------------------

---

### Post by Iowan on 2009-09-30
Can you **ping** the router (or whatever you use to connect to internet)? Does machine get IP address via DHCP or is it manually set?

---

### Post by slvfx on 2009-09-30
I can ping the router

---

### Post by Iowan on 2009-09-30
Does **route -n** show your router address as the gateway (last line)?

---

### Post by slvfx on 2009-09-30
This is what its showing
 
[FONT=Batang][SIZE=3]Kernel IP routing table[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/SIZE][/FONT]
[FONT=Batang][SIZE=3]192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0[/SIZE][/FONT]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]

---

### Post by Iowan on 2009-09-30
Hmmm... the gateway line is missing. Is your IP address set up via */etc/network/interfaces* or Network Manager? A server would normally use the former, but you mentioned using a desktop. I'll assume the address is static rather than DHCP.
You can manually set a default gateway (read **man route** for details), but I dunno if it'll survive a reboot. You can also add it to */etc/network/interfaces* if your interface is configured that way.

---

### Post by slvfx on 2009-12-07
I ended up going into my verizon router and made changes in it to get the server working.

---

### Post by Iowan on 2009-12-07
Is it fixed - or are there still issues?

---

