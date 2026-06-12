---
title: "Can't connect to the internet"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by MC707 on 2009-02-27
As the title says, I can't connect to the internet using my Ubuntu 8.10 Intrepid. I don't recall doing anything stupid, but until the day before yesterday my internet connection was fine. I know my cable router and internet are fine, since I am typing this from my Vista partition in the very same computer. Therefore, the problem is with Ubuntu (dang). I hope someone can help me :cry:

BTW I did check Ubuntu forums before posting this, checked a lot of posts and tried a lot of things (which btw spent ALL my afternoon yesterday). Thanks in advance.

---

### Post by whoop on 2009-02-27
can you ping 74.125.79.147 ?
If you can you need to reassign you dns servers

---

### Post by MC707 on 2009-02-27
no. I tried pinging (I read previous post before postin this ;-)) but I can ping absolutely nothing (by this I mean ubuntu.com, google.com, IP xxx.yyy.zzz.www, etc).

---

### Post by Iowan on 2009-02-27
Does machine have IP address (check **ifconfig** in a terminal).

---

### Post by MC707 on 2009-02-27
I'll log onto my Ubuntu and copy the output of ifconf.

---

### Post by MC707 on 2009-02-27
user@user-desktop:~$ sudo ifconfig
[sudo] password for user: 
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:30:b4:b3  
          inet addr:190.10.179.192  Bcast:190.10.179.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe30:b4b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:1296736 (1.2 MB)  TX bytes:1152 (1.1 KB)
          Memory:e7200000-e7220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Iowan on 2009-02-28
Do you get the same (or similar) address when booted in Vista?

---

### Post by Paul41 on 2009-02-28
You can get the information in Windows with 

```
ipconfig /all
```

---

### Post by Iowan on 2009-02-28
Thanks Paul41 - I was gonna mention that, but that leads to the next question - How do I get to command line in Windows Vista?  Fired up my laptop (haven't yet got it dual-booting with Ubuntu) and learned that the "Run" dialog box is available via Window Key+R. Then "cmd" drops you to a command line.

---

### Post by MC707 on 2009-03-02
Thanks for answering and sorry for not answering - spent these days trying to make my connection work in Ubuntu but no luck. Now this is what I get in Windows. BTW I did know how to open Cmd. I've used Windows all my life before I met Linux, y' know? :P Hehehe, but thanks anyway. It might help a newb like me if he/she stumbles across a problem like this.

```
Microsoft Windows [Version 6.0.6001]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Windows\system32>ipconfig /all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : Mario
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : cpe.satnet.net

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : cpe.satnet.net
   Description . . . . . . . . . . . : Intel(R) 82566DC Gigabit Network Connecti
on
   Physical Address. . . . . . . . . : 00-1C-C0-30-B4-B3
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::6de2:2e98:19ff:e1e%10(Preferred)
   IPv4 Address. . . . . . . . . . . : 190.10.179.192(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Sunday, March 01, 2009 15:30:08
   Lease Expires . . . . . . . . . . : Thursday, March 05, 2009 15:30:06
   Default Gateway . . . . . . . . . : 190.10.179.1
   DHCP Server . . . . . . . . . . . : 10.102.101.94
   DNS Servers . . . . . . . . . . . : 200.63.212.110
                                       200.25.144.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : cpe.satnet.net
   Description . . . . . . . . . . . : isatap.cpe.satnet.net
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Local Area Connection* 7:

   Connection-specific DNS Suffix  . : cpe.satnet.net
   Description . . . . . . . . . . . : 6TO4 Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2002:be0a:b3c0::be0a:b3c0(Preferred)
   Default Gateway . . . . . . . . . : 2002:c058:6301::c058:6301
   DNS Servers . . . . . . . . . . . : 200.63.212.110
                                       200.25.144.1
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 11:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e50:10eb:26fd:41f5:4c3f(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::10eb:26fd:41f5:4c3f%12(Preferred)
   Default Gateway . . . . . . . . . :
   NetBIOS over Tcpip. . . . . . . . : Disabled

C:\Windows\system32>
```

---

### Post by MC707 on 2009-03-03
No one can help me? Dang. I want to use Ubuntu, but this way I can't.[-( Internet settings should be set automatically.

---

### Post by Iowan on 2009-03-03
> **MC707 said:**
>  BTW I did know how to open Cmd. I've used Windows all my life before I met Linux, y' know? :P Hehehe, but thanks anyway. You're ahead of a lot of Windows users who wouldn't know where to find (or how to use) the command line.  But I digress...

Can you ping your gateway(190.10.179.1)? If so, do your nameservers show up in /etc/resolv.conf?  Ordinarily, **dhclient** retrieves those from DHCP server. (I presume you're using DHCP).

---

### Post by MC707 on 2009-03-04
Sorry for late answer. 
I wasn't able to ping 190.10.179.1, but I was able to ping 190.10.179.192. This is what I get.
```

Bytes	Source	Seq	Time	Units
64	190.10.179.192	1	0.054	ms
64	190.10.179.192	2	0.042	ms
64	190.10.179.192	3	0.036	ms
64	190.10.179.192	4	0.040	ms
64	190.10.179.192	5	0.040	ms
Time minimum:	0.04 ms
Time average:	0.04 ms
Time maximum:	0.05 ms
Packets transmitted:	5
Packets received:	5
Successful packets:	100%

```
I got this in the resolv.conf
```

# Generated by NetworkManager
domain cpe.satnet.net
search cpe.satnet.net
nameserver 200.63.212.110
nameserver 200.25.144.1

```
Satnet is my ISP.
Hope thats what you were asking for.

---

### Post by MC707 on 2009-03-06
Cmon people! Gimme a helping hand please [-o<

---

### Post by Iowan on 2009-03-07
> **MC707 said:**
>    Physical Address. . . . . . . . . : 00-1C-C0-30-B4-B3
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::6de2:2e98:19ff:e1e%10(Preferred)
   IPv4 Address. . . . . . . . . . . : [COLOR="Red"]190.10.179.192[/COLOR](Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Sunday, March 01, 2009 15:30:08
   Lease Expires . . . . . . . . . . : Thursday, March 05, 2009 15:30:06
   Default Gateway . . . . . . . . . : [COLOR="Blue"]190.10.179.1[/COLOR]
   DHCP Server . . . . . . . . . . . : 10.102.101.94
   DNS Servers . . . . . . . . . . . : 200.63.212.110
                                       200.25.144.1
   NetBIOS over Tcpip. . . . . . . . : Enabled 
190.10.179.192 is the local machine IP address - if the network card is working, it *should* be reachable.  If you can't reach (ping) your gateway, the internet will also be unreachable.  I'm a bit confused why your DHCP server at 10.102.101.94 is giving out addresses in a different subnet... not impossible, but unusual.

---

### Post by jamesr on 2009-03-08
Hi MC707,

That seems an unusual inet address although not the normal failure address. What is the address when using Vista. 

Ignore my message as my system did not show all of the replies.

---

### Post by MC707 on 2009-03-13
> **Iowan said:**
> 190.10.179.192 is the local machine IP address - if the network card is working, it *should* be reachable.  If you can't reach (ping) your gateway, the internet will also be unreachable.  I'm a bit confused why your DHCP server at 10.102.101.94 is giving out addresses in a different subnet... not impossible, but unusual.
This is all kinda complicated, but maybe there is a way to reset all settings or something like that. I mean, my Vista's Internet is working, my Ubuntu's internet *was* working, so maybe a settings reset could do the trick. In the end, though, I think something is really wrong. Ubuntu is meant to be as simple and User friendly as possible (Linux for people), so the network should try to kinda fix by itself (like Vista does). Unfortunately, this networking issue has lead me to use Ubuntu sparringly (completely opposite of what I wanted when I installed my Vista partition).:(

Someone told me maybe I could use the Ubuntu cd to restore settings or something, so I'm gonna try that. Thanks for the replies, though. I appreciate them. :)

---

