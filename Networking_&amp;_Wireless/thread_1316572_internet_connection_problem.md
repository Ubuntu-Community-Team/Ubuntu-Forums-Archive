---
title: "internet connection problem"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by madcat_ninja on 2009-11-06
Hello, I was wondering if anyone can help me? I've just started using Ubuntu today and I'm totally noob so bear with me!!! 

I've installed Ubuntu version 9.04 and I have an problem connecting to the internet. I can access my network but I couldn't browse using firefox. 
I could ping my router or any sites but I couldn't access my router or browse using firefox! 

Heres ifconfig: 

xbmc@xbmc-desktop:~$ ifconfig 
eth0 Link encap:Ethernet HWaddr 90:e6:ba:6c:3e:d0 
inet addr:192.168.1.65 Bcast:192.168.1.255 Mask:255.255.255.0 
inet6 addr: fe80::92e6:baff:fe6c:3ed0/64 Scope:Link 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:663 errors:0 dropped:0 overruns:0 frame:0 
TX packets:366 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:47068 (47.0 KB) TX bytes:44715 (44.7 KB) 
Interrupt:22 Base address:0x6000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) 

Thanks in advance if anyone can help me [IMG]https://avatar.bethere.co.uk/forum/images/smiles/icon_smile.gif[/IMG]

---

### Post by arjuntank on 2009-11-06
if you are using a home DSL connection, you can try "sudo pppoeconf" at the terminal and follow the instructions. this is what i do with my home connection. see if it helps you.
what type of internet connection are you using?
i you were using windows before, and used to connect with username and password than it's definitely the DSL connection and the above command would do just fine.this is the best i can do.

---

### Post by madcat_ninja on 2009-11-06
I'm using ADSL and it is connected to my router. In windows, I just provide ip address + DNS Server or let it assign ip address through DHCP server and it will work. 
 
Heres more information which you guys might want to see:
 
[FONT=Batang][SIZE=3]xbmc@xbmc-desktop:~$ route -n[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Kernel IP routing table[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/SIZE][/FONT]
[FONT=Batang][SIZE=3]192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]xbmc@xbmc-desktop:~$ cat /etc/resolv.conf[/SIZE][/FONT]
[FONT=Batang][SIZE=3]nameserver 208.67.222.222[/SIZE][/FONT]
[FONT=Batang][SIZE=3]nameserver 208.67.220.220[/SIZE][/FONT]
[FONT=Batang][SIZE=3]xbmc@xbmc-desktop:~$ sudo iptables -nvL[/SIZE][/FONT]
[FONT=Batang][SIZE=3][sudo] password for xbmc:[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Chain INPUT (policy ACCEPT 0 packets, 0 bytes)[/SIZE][/FONT]
[SIZE=3][FONT=Batang] pkts bytes target     prot opt in     out     source               destination         [/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)[/SIZE][/FONT]
[SIZE=3][FONT=Batang] pkts bytes target     prot opt in     out     source               destination         [/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)[/SIZE][/FONT]
[SIZE=3][FONT=Batang] pkts bytes target     prot opt in     out     source               destination         [/FONT][/SIZE]
[FONT=Batang][SIZE=3]xbmc@xbmc-desktop:~$[/SIZE][/FONT]

---

### Post by arjuntank on 2009-11-06
> **madcat_ninja said:**
> I'm using ADSL and it is connected to my router. In windows, I just provide ip address + DNS Server or let it assign ip address through DHCP server and it will work. 
 
Heres more information which you guys might want to see:
 
[FONT=Batang][SIZE=3]xbmc@xbmc-desktop:~$ route -n[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Kernel IP routing table[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/SIZE][/FONT]
[FONT=Batang][SIZE=3]192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0[/SIZE][/FONT]
[FONT=Batang][SIZE=3]xbmc@xbmc-desktop:~$ cat /etc/resolv.conf[/SIZE][/FONT]
[FONT=Batang][SIZE=3]nameserver 208.67.222.222[/SIZE][/FONT]
[FONT=Batang][SIZE=3]nameserver 208.67.220.220[/SIZE][/FONT]
[FONT=Batang][SIZE=3]xbmc@xbmc-desktop:~$ sudo iptables -nvL[/SIZE][/FONT]
[FONT=Batang][SIZE=3][sudo] password for xbmc:[/SIZE][/FONT]
[FONT=Batang][SIZE=3]Chain INPUT (policy ACCEPT 0 packets, 0 bytes)[/SIZE][/FONT]
[SIZE=3][FONT=Batang] pkts bytes target     prot opt in     out     source               destination         [/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)[/SIZE][/FONT]
[SIZE=3][FONT=Batang] pkts bytes target     prot opt in     out     source               destination         [/FONT][/SIZE]
[FONT=Batang][SIZE=3] [/SIZE][/FONT]
[FONT=Batang][SIZE=3]Chain OUTPUT (policy ACCEPT 0 packets, 0 bytes)[/SIZE][/FONT]
[SIZE=3][FONT=Batang] pkts bytes target     prot opt in     out     source               destination         [/FONT][/SIZE]
[FONT=Batang][SIZE=3]xbmc@xbmc-desktop:~$[/SIZE][/FONT]

okay, try using wicd. then enter the entries, that is the ip addr and DNS just like you did in windows. it's simple and it should work. 
plus, try using the default gateway ip of your router as nameservers in your resolv.conf. i think you don't need opendns.

---

### Post by Bucky Ball on 2009-11-06
System->Administration->Network. Click on 'Wireless' and the 'Properties'.

All details need to match those in your router. It is jumping the gun to start thinking about wicd before checking some basic stuff. You can ping the router so there is nothing wrong with the connection. Probably have a setting wrong somewhere.

You need the ESSID of the router and the correct security key (to match the router). If your router is serving an IP (DHCP server) you need to set 'configuration' to 'auto-configure' (DHCP) and enable roaming to off.

Let us know how you go.

---

### Post by arjuntank on 2009-11-06
> **Bucky Ball said:**
> System->Administration->Network. Click on 'Wireless' and the 'Properties'.

All details need to match those in your router. It is jumping the gun to start thinking about wicd before checking some basic stuff. You can ping the router so there is nothing wrong with the connection. Probably have a setting wrong somewhere.

You need the ESSID of the router and the correct security key (to match the router). If your router is serving an IP (DHCP server) you need to set 'configuration' to 'auto-configure' (DHCP) and enable roaming to off.

Let us know how you go.

i think thats a wired connection(eth0), not wireless.

---

