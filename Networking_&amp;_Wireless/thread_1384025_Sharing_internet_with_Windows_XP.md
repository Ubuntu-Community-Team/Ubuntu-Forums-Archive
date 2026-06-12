---
title: "Sharing internet with Windows XP"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by bovus on 2010-01-17
I have a laptop running Windows XP with a secure wireless internet connection.  I want to share this connection to my desktop running Ubuntu 9.10 via an direct ethernet cable connection.

So far in Windows I checked the "Allow other network users to connect through this computer's Internet connection" in the Wireless Network Connection Properties menu. Doing this creates a new IP Configuration.  Here is an output of running the *ipconfig* command:
Windows IP Configuration

```

Ethernet adapter Wireless Network Connection:

        Connection-specific DNS Suffix  . : home
        IP Address. . . . . . . . . . . . : 192.168.1.3
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.1
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . :

```

I believe this is set up correctly in windows.  However I am not able to get my internet connection working on Ubuntu.  I am using the Network Manager and configuring unsecure 802.1x connection with IPv4 method set to "Shared to other computers".  This is the output of the *ifconfig* command run on the Ubuntu machine:
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:aa:f4:9c  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:feaa:f49c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1986 (1.9 KB)  TX bytes:13148 (13.1 KB)
          Interrupt:28 Base address:0x200

```

Does anyone know what I am doing wrong?  thanks

---

### Post by bovus on 2010-01-17
Solved:

Set the IPv4 Method to "Automatic (DHCP)" in the Network Manager and I was successfully able to connect to the internet on my desktop through my laptops wireless internet connection.  Here is the output of the *ifconfig* command on my desktop while connected to my laptop:
```

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:aa:f4:9c  
          inet addr:192.168.0.207  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:7dff:feaa:f49c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2428301 (2.4 MB)  TX bytes:354416 (354.4 KB)
          Interrupt:28 Base address:0x2000

```

---

### Post by Iowan on 2010-01-18
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")  :D

---

