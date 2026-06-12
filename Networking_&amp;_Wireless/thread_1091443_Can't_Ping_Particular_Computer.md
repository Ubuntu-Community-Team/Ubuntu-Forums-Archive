---
title: "Can't Ping Particular Computer"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by N04h on 2009-03-09
I have a network here and I'm trying to backup all my machines using backuppc.  When I try to backup a particular machine it says it can't ping it, but I can ping other computers on the network.  For example:

```
noah@backup:/etc/backuppc$ ping lima
PING lima (192.168.0.62) 56(84) bytes of data.
64 bytes from lima (192.168.0.62): icmp_seq=1 ttl=128 time=0.859 ms
64 bytes from lima (192.168.0.62): icmp_seq=2 ttl=128 time=0.959 ms
64 bytes from lima (192.168.0.62): icmp_seq=3 ttl=128 time=0.974 ms

--- lima ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.859/0.930/0.974/0.062 ms

```

```
noah@backup:/etc/backuppc$ ping 192.168.0.62
PING 192.168.0.62 (192.168.0.62) 56(84) bytes of data.
64 bytes from 192.168.0.62: icmp_seq=1 ttl=128 time=2.77 ms
64 bytes from 192.168.0.62: icmp_seq=2 ttl=128 time=0.784 ms
64 bytes from 192.168.0.62: icmp_seq=3 ttl=128 time=0.843 ms
64 bytes from 192.168.0.62: icmp_seq=4 ttl=128 time=0.818 ms

--- 192.168.0.62 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.784/1.305/2.777/0.850 ms

```

Now the machine I can't ping(notice it does resolve the computer name to an IP address though):

```
noah@backup:/etc/backuppc$ ping adam
PING adam (192.168.0.36) 56(84) bytes of data.

--- adam ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4002ms



```

Let's try the IP address:

```
noah@backup:/etc/backuppc$ ping 192.168.0.36
PING 192.168.0.36 (192.168.0.36) 56(84) bytes of data.

--- 192.168.0.36 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6001ms

noah@backup:/etc/backuppc$

```

negative.

No firewalls, nothing should be blocking it.  Any Ideas?  Anything to try?

Thanks in advance.

---

### Post by Aemaeth on 2009-03-09
Have you tried to ping out from the computer "adam" to another computer? If you can verify that it has a network connection then try to ping other computers on the network. Are you using static addresses or is the machine "adam" behind a router?

---

### Post by N04h on 2009-03-09
> **Aemaeth said:**
> Have you tried to ping out from the computer "adam" to another computer? If you can verify that it has a network connection then try to ping other computers on the network. Are you using static addresses or is the machine "adam" behind a router?

Here is "adam" pinging the router:

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Administrator>ping 192.168.0.1

Pinging 192.168.0.1 with 32 bytes of data:

Reply from 192.168.0.1: bytes=32 time=38ms TTL=64
Reply from 192.168.0.1: bytes=32 time=2ms TTL=64
Reply from 192.168.0.1: bytes=32 time=2ms TTL=64
Reply from 192.168.0.1: bytes=32 time=2ms TTL=64

Ping statistics for 192.168.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 2ms, Maximum = 38ms, Average = 11ms


```

I'm actually SSH'd into backup from adam (So they can see each other enough to SSH from adam to backup) and that's how I got the text to copy in here in my first post.  Both machines are behind the same router and adam is DHCP and backup is static.

Thank You.

---

### Post by rickyjones on 2009-03-09
> **N04h said:**
> I have a network here and I'm trying to backup all my machines using backuppc.  When I try to backup a particular machine it says it can't ping it, but I can ping other computers on the network.  For example:

```
noah@backup:/etc/backuppc$ ping lima
PING lima (192.168.0.62) 56(84) bytes of data.
64 bytes from lima (192.168.0.62): icmp_seq=1 ttl=128 time=0.859 ms
64 bytes from lima (192.168.0.62): icmp_seq=2 ttl=128 time=0.959 ms
64 bytes from lima (192.168.0.62): icmp_seq=3 ttl=128 time=0.974 ms

--- lima ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 0.859/0.930/0.974/0.062 ms

```

```
noah@backup:/etc/backuppc$ ping 192.168.0.62
PING 192.168.0.62 (192.168.0.62) 56(84) bytes of data.
64 bytes from 192.168.0.62: icmp_seq=1 ttl=128 time=2.77 ms
64 bytes from 192.168.0.62: icmp_seq=2 ttl=128 time=0.784 ms
64 bytes from 192.168.0.62: icmp_seq=3 ttl=128 time=0.843 ms
64 bytes from 192.168.0.62: icmp_seq=4 ttl=128 time=0.818 ms

--- 192.168.0.62 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.784/1.305/2.777/0.850 ms

```

Now the machine I can't ping(notice it does resolve the computer name to an IP address though):

```
noah@backup:/etc/backuppc$ ping adam
PING adam (192.168.0.36) 56(84) bytes of data.

--- adam ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4002ms



```

Let's try the IP address:

```
noah@backup:/etc/backuppc$ ping 192.168.0.36
PING 192.168.0.36 (192.168.0.36) 56(84) bytes of data.

--- 192.168.0.36 ping statistics ---
7 packets transmitted, 0 received, 100% packet loss, time 6001ms

noah@backup:/etc/backuppc$

```

negative.

No firewalls, nothing should be blocking it.  Any Ideas?  Anything to try?

Thanks in advance.

Are you positive that adam has that IP Address? Did you confirm it on the actual machine?

First thing to check.

Thanks,
Richard

---

### Post by N04h on 2009-03-09
Yep, just triple checked Adam does us 192.168.0.36 as its IP address.  Any other things to check?

---

### Post by rickyjones on 2009-03-09
> **N04h said:**
> Yep, just triple checked Adam does us 192.168.0.36 as its IP address.  Any other things to check?

Can Adam ping any other IP addresses?
Can you do a full network IP scan using a program similar to Angry IP Scanner to ensure that everything else is as you expect?
What OS is Adam?

Thanks,
Richard

---

### Post by Aemaeth on 2009-03-09
if adam can ping [www.google.com](www.google.com) sucessfully and the router then it has network connectivity as well as able to resolve outside addresses. The next thing to check would be if the machine is able to reply to ICMP echo requests. 

Strange that you are able to connect SSH and not able to ping. seems to be that there is some form of a block in place. 

Might try looking here to configure firewall settings
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by N04h on 2009-03-09
```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Noah>ping 192.168.0.36

Pinging 192.168.0.36 with 32 bytes of data:

Request timed out.

Ping statistics for 192.168.0.36:
    Packets: Sent = 1, Received = 0, Lost = 1 (100% loss),
Control-C
^C
C:\Documents and Settings\Noah>
```

Looks like the issue maybe on Adam .  I can't ping it from my workstation.  I suspect it is a firewall on Adam.

---

### Post by N04h on 2009-03-10
> **Aemaeth said:**
> if adam can ping [www.google.com](www.google.com) sucessfully and the router then it has network connectivity as well as able to resolve outside addresses. The next thing to check would be if the machine is able to reply to ICMP echo requests. 

Strange that you are able to connect SSH and not able to ping. seems to be that there is some form of a block in place. 

Might try looking here to configure firewall settings
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

I've turned off the firewall and anti-hacker software on adam.  Still nothing.  Any other ideas?

---

### Post by rickyjones on 2009-03-10
> **N04h said:**
> I've turned off the firewall and anti-hacker software on adam.  Still nothing.  Any other ideas?

Can you post an "ipconfig /all" command from Adam? I assume Adam is running Windows XP.

Thanks,
Richard

---

### Post by N04h on 2009-03-10
What happened is that on adam I installed kaspersky, which says it is going to uninstall your anti-virus.  It must do something because all other antivirus is removed from the program menu and doesn't start up on startup.  However, the program is still listed in the add/remove programs menu on windows.  Once it was removed from here then I was about get it to work.

Thanks to everyone for trying to help me figure this out!

---

