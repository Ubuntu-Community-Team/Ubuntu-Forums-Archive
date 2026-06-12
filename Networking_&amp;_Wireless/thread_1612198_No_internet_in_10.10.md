---
title: "No internet in 10.10"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by matskv on 2010-11-02
I have also encountered a similar version of [this problem]("http://ubuntuforums.org/showthread.php?p=10063677"). After upgrading from 9.10 (using a disk install, not via update manager), I lost my connection to my local network (as well as internet). All other devices attached to my local network have access to both internet and to the other devices on the local network, except for my Ubuntu 10.10 computer. 

According to my router, the Ubuntu 10.10-computer is attached and has been assigned an ip-address. However, it is not possible to successfully ping from my 10.10-computer or to it. From the computer I can ping "localhost" but 127.0.0.1 fails! 

Thankful for any help I can get!

---

### Post by Iowan on 2010-11-02
Does **ifconfig -a** show the 10.10 machine with an IP address? (hopefully not an **avahi** address...)
**ping 127.0.0.1** fails???   :confused:
Right-click Network Manager icon and verify that Networking is enabled.

---

### Post by matskv on 2010-11-03
I can not physically access the computer in question right now since I am at work, but according to what I can recall, ifconfig shows the same IP as my router has assigned to it. 

There was however a strange detail (for me at least) in the ifconfig-listing; after my IP-address 192.168.1.107 there was a broadcast-address 192.168.1.255 which I cannot remember I have seen before. 

I'll get back with more info when I get home in about 10 hours. 

Thanks!

---

### Post by matskv on 2010-11-03
Okay, I'm back. First of all, ping 127.0.0.1 works fine from the terminal window, but not from Network Tools. I don't know how to interpret that except for not trusting Network Tools. Or? Anyway, I guess it's good news. Also, ping 192.168.1.107 works from the terminal window. :-)


ifconfig -a says: (manually transcribed since I have no ethernet connection...)
eth0  Link encap: Ethernet   HWaddr bla:bla:bla:bla
        inte addr: 192.168.1.107 Bcast: 192.168.1.255 Mask 255.255.255.0
        inet6 addr: fe80::213:d4ff:fe7f:4e9f/64 Scope:Link
        UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
        ...various rx/tx stats about my pinging on 192.168.1.107 only

lo     Link encap: Local Loopback
        inet addr:127.0.0.1  Mask 255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING MTU:16436   Metric:1
        .. various stats concerning me pinging localhost and 127.0.0.1 

My /etc/network/interfaces says
auto lo
iface lo inet loopback

Another thing that might be of interest is that after login in I get the "Network service discovery disabled" message up on the right hand side, i.e. "Your current network has a .local domain, which is not recommended and incompatible with the Avahi network service discovery. The service has been disabled".  This message showed up in my 9.10 installation also. Is this something I should be concerned about? Frankly, I don't have a clue of what the message is trying to tell me, even after searching on forums about it.

Thanks again for any help and clues on how to solve my network problems!

---

### Post by al090187 on 2010-11-03
Usually the /etc/network/interfaces should have some additional lines, regarding the ethernet connection. Try adding

```
auto eth0
iface eth0 inet dhcp
```

---

### Post by matskv on 2010-11-03
Thanks, al090187, I'll try that soon. However, I made some similar additions yesterday to 'interfaces' but with no success.

Right now I'm partioning my boot disk in preparation for installing 9.10 and maybe 10.04 as well alongside the 10.10. I feel totally disabled now when my media server is not working so I will need something to boot to when I'm not trying to solve this issue with networking in 10.10. Because I won't give up! 

Note also that I have no problem networking with 9.10 and even from the 10.10 live-cd. Isn't that strange? And in all these cases I have the same interfaces-file as the current in 10.10. 

Thanks again!

---

### Post by Iowan on 2010-11-03
For what it's worth - on a Network Manager-controlled machine, */etc/network/interfaces* usually has only the following lines:```
auto lo
iface lo inet loopback
```
Although NM *should* attend to it, you can check your gateway by looking (from a terminal) at **route -n**... the line marked with "UG" is the gateway designation. You can also verify DNS by checking **cat /etc/resolv.conf**

Interfaces defined in */etc/network/interfaces* are normally not controlled by NM (although this can be changed), which means gateway and DNS must be manually configured. 

If you have a standard server-install (without a desktop/GUI), there is no Network Manager, so */etc/network/interfaces* is the normal method of configuration (unless something has changed in 10.10).

---

