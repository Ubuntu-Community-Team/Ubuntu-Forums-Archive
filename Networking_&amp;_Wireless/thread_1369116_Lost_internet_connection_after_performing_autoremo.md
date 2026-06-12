---
title: "Lost internet connection after performing autoremove"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by DanH 1970 on 2009-12-31
First Post.
 
Hello and thanks so much for taking the time to assist me here.
 
I am a relative newbie to Linux.  I have been using a USB-Live version of Xubuntu (with persistence) for a couple of months with few problems.  Today I learned of the "autoremove" sudo apt-get command, and I (apparently wrongly) assumed that this was like a cleanup wizard or something.  So I ran it, and now I cannot access the internet.
 
I did find a couple of threads on here where people lost their wi-fi or whatever after performing autoremove, but my network connections appear to be intact.  What happens though is that when I run Firefox or Opera now, I get a 'cannot access remote server' error message.  Also, when I run sudo apt-get update from the Terminal, I get similar 'can't connect' error messages.
 
Any help would be greatly appreciated.  It wouldn't be too big of a deal to reformat my USB and re-install the distro, but I'd like to see if there may be a quicker and easier solution.
 
Thanks,
 
DanH

---

### Post by Iowan on 2009-12-31
> **DanH 1970 said:**
>  It wouldn't be too big of a deal to reformat my USB and re-install the distro, but I'd like to see if there may be a quicker and easier solution.
Even if it'd be quicker/easier to re-install, it's worth at least a little troubleshooting effort just to get better acquainted with the OS.
Check (post results) of **ifconfig -a**, and **route -n**.

---

### Post by DanH 1970 on 2009-12-31
[FONT=Times New Roman][SIZE=3]ubuntu@ubuntu:~$ ifconfig -a[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]eth0      Link encap:Ethernet  HWaddr 00:0d:56:7d:88:e6  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet6 addr: fe80::20d:56ff:fe7d:88e6/64 Scope:Link[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:292 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:129313 (129.3 KB)  TX bytes:4051 (4.0 KB)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          Interrupt:11 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]lo        Link encap:Local Loopback  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]pan0      Link encap:Ethernet  HWaddr 62:f3:14:34:75:99  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:0 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]wlan0     Link encap:Ethernet  HWaddr 00:90:4b:6d:51:1b  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          inet6 addr: fe80::290:4bff:fe6d:511b/64 Scope:Link[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:194 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:82342 (82.3 KB)  TX bytes:3646 (3.6 KB)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-6D-51-1B-36-64-00-00-00-00-00-00-00-00  [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          UP RUNNING  MTU:0  Metric:1[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          collisions:0 txqueuelen:1000 [/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/SIZE]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]ubuntu@ubuntu:~$ route -n[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Kernel IP routing table[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]

---

### Post by Iowan on 2009-12-31
I remember seeing this same problem in another thread... but I don't remember if it got solved (I'm thinking it did not).  I'll try to find it. 
(BTW, settings look OK.)

---

