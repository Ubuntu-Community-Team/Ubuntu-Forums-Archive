---
title: "Wireless connection, no internet"
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by DC80 on 2011-06-10
Hi all,

Finally I thought I solved my problem with the help of Dmizer. My networkcard wasn't functioning correctly due to the hardware switch on my laptop. For more information about this check this thread: [http://ubuntuforums.org/showthread.php?t=1775829&highlight=no+wireless+connection](http://ubuntuforums.org/showthread.php?t=1775829&highlight=no+wireless+connection)

Now I have a new problem, probably caused by the problem above. I have a connection (so the network manager says) but no internet. I checked the network settings by using the ifconfig command in a terminal. This tells me that I have an address of 10.43.42.2 (or similar) which should be something like this 192.168.x.x. 

I had already tried to use a command like "ifconfig release" but this didn't work. I know too much windows like but i had to try something. I also had the connection properties checked and changed to my network settings. After i did this I had still the same address (10.43.42.2 or similar).

Unless someone knows what is going on I'd like to know how to refresh of renew my IP address from the DHCP server.

Some information about my hardware and drivers:

NIC vendor: Atheros Communications Inc.
NIC chipset: AR2413 (i guess, i do not have my laptop with me at the time of writing)
Old driver: ath5k
New driver: ath_pci (installed from madwifi)

Kind regards,

DC80

---

### Post by jtarin on 2011-06-10
Post terminal results from the command ```
route -n
```

---

### Post by lz1dsb on 2011-06-10
Could you also post the output from the ifconfig command? Are you able to reach your default gateway? Do you have any DNS configuration?

---

### Post by DC80 on 2011-06-10
@ [jtarin]("http://ubuntuforums.org/member.php?u=738123"): I will do this command asap which is probably this afternoon or evening. (dutch time). 

@ lz1dsb: It seems to be a local address (10.x.x.x). Any other output will have to wait because i do not have access to my laptop at this moment.

I'm sorry for the delay. 

```

user@user-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:19:7d:3b:02:59  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7dff:fe3b:259/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1904 (1.9 KB)  TX bytes:1904 (1.9 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-19-7D-3B-02-59-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:12043 (12.0 KB)
          Interrupt:18


```

---

### Post by DC80 on 2011-06-10
This is the output of "route -n" command:

```
[FONT=monospace]
[/FONT] user@user-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     2      0        0 ath0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 ath0
user@user-laptop:~$ 

```

---

