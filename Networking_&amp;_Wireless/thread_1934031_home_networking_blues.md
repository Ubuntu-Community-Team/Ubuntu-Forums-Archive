---
title: "home networking blues"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by mamboze on 2012-03-01
It seems incredibly difficult to set up a simple home network on Ubuntu 10.04.

I've set the IPs for both machines static on a desktop and a laptop, editing /etc/network/interfaces to:
```

auto lo
iface to inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.3  * for the desktop
address 192.168.1.4  * for the laptop
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

```

and on the laptop
```

medea:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e8:11:32:15:7f:9f  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::ea11:32ff:fe15:7f9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1112252 (1.1 MB)  TX bytes:268014 (268.0 KB)
          Interrupt:26 

eth1      Link encap:Ethernet  HWaddr 4c:ed:de:f5:6f:56  
          inet6 addr: fe80::4eed:deff:fef5:6f56/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19590 (19.5 KB)  TX bytes:19590 (19.5 KB)

```
on the desktop
```

prospero:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:80:3a:1b:d3  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:80ff:fe3a:1bd3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31839 (31.8 KB)  TX bytes:12342 (12.3 KB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

```
openssh-server and openssh-client have been installed on both machines and the connect to server configured with service type: ssh  and server: roy@192.168.1.3 (or 4).

Attempting to connect gives this error message on the laptop

Could not open location 'sftp://roy@192.168.1.3/'
Host key verification failed

on the desktop

Could not open location 'sftp://roy@192.168.1.4/'
ssh program unexpected exited

openssh-server and openssh-client were uninstalled and reinstalled, machines rebooted but no change

Any help would be much appreciated.

---

### Post by mamboze on 2012-03-01
anyone?

---

### Post by Iowan on 2012-03-02
Can you successfully **ping** from each machine to the other?

I'm a bit confused why you would get the "Could not open location 'sftp://roy@192.168.1.4/'" when attempting an SSH connection. 
You are trying **ssh roy@192.168.1.4** or **ssh roy@192.168.1.3** ?

---

### Post by mamboze on 2012-03-03
Hi,

Yes, ping is successful both ways. 

I remembered that I had the ufw firewall enabled on the laptop when I disabled it, I was able to connect from the desktop to the laptop but not the reverse. Duh!

Attempting to connect from the laptop to the desktop gives this (different to before):

Cannot display location "sftp://roy@192.168.1.3"

Host key verification failed

I was trying to connect from the desktop (IP 192.168.1.3) to the laptop (IP 192.168.1.4). This returned the  "Could not open location 'sftp://roy@192.168.1.4/'" message.

 Hope this helps. Thanks

---

### Post by mamboze on 2012-03-03
Just to finish up on this. The laptop gave awhile ago an Host key verification failed error. 

I found this thread 
[http://ubuntuforums.org/showthread.php?t=1448376](http://ubuntuforums.org/showthread.php?t=1448376)
which suggested: 

 sudo mv ~/.ssh/known_hosts ~/.ssh/known_hosts_backup

This worked. 

BTW where is the solved button/icon?

---

### Post by Iowan on 2012-03-03
Glad you got the problem fixed!
To mark the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

