---
title: "Newbie question : Where are the kernel headers in order to install my NIC driver?"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by Parapan on 2011-07-08
Hello all,

I am running Ubuntu 11.04 with a Dlink DGE-530T NIC. My browsing in Ubuntu on ALL browsers is horribly slow. It works perfectly fine on windows and other PCs on the LAN. So I know for sure my router and my internet line is fine.I figured it could be a problem with my NIC drivers and decided to install the drivers from the CD. (All this while it was running on the default drivers that ship with Ubuntu). I'm trying to install the sk98lin drivers and my understanding of the kernel so far is still very weak. When I try to run the install.sh script it gives me an error saying : 


```

Create tmp dir (/tmp/Sk98IknhDHEiLKnkWUSoYMTLi)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (2.6.38-8-generic)                              [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (2)                                             [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (x86_64)                                            [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (kernel)                                         [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check archive file (sk98lin)                                         [   OK   ]
Check kernel gcc version (4.5.2) (Kernel:4.5.2 == gcc:4.5.2)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (not found)                                [ failed ]
Kernel header not found. Please install the linux header files
development package or crate a symbolic link from the
/usr/src/KERNEL_VERSION directory to linux
    Example: ln -s /usr/src/KERNEL_VERSION /usr/src/linux


Installation of sk98lin driver module failed.
Delete temp directories (done)                                       [   OK   ]

```

If my understanding of this is correct, then is it trying to find the kernel headers under /usr/src/linux-headers.xx? I'm not sure how exactly to get it to find the required kernel header files. I tried 
```

apt-get install linux-headers-$(uname -r)

```


But the installation script is still not able to find it. I tried searching a few threads on google but wasn't able to make too much sense of whats going on because of my lack of understanding of the linux kernel. As of now I would really appreciate it if someone would give me a quickfix to this problem or guide me with any particular commands or symbolic links that need to be made in order for this to work, because my browsing times are realllly slow (~6 seconds to load a page that normally takes ~.5seconds), and I need my browsing speeds back asap  :D. I will soon begin to learn about the kernel when I buy some books, but for now it would be great if anyone can help me out with this , thanks :D

---

### Post by chili555 on 2011-07-08
Please be sure, in Synaptic, that you have *build-essential* installed. Then you might try linux-source-2.6.38.

sk98lin, eh? Is it using skge now? If so, you'll need to blacklist it.

---

### Post by Parapan on 2011-07-09
Thanks for the reply! After doing some reading on various forums I decided not to use the sk98lin driver because a lot of people suggest using the skge driver itself. At first I thought my problem was with the network drivers but now I'm beginning to think its because I installed Ubuntu with an onboard NIC and later switched to a PCI NIC. I'll close this thread for now because the kernel headers are not an issue anymore..

---

### Post by chili555 on 2011-07-09
> I installed Ubuntu with an onboard NIC and later switched to a PCI NICIt should make no difference whatever, although it might make Network Manager happier if you blacklisted the onboard.

---

### Post by Parapan on 2011-07-09
Oh, how can I do that? I also tried have uninstalling all installed network managers but it still didn't help!

---

### Post by chili555 on 2011-07-09
You have uninstalled Network Manager? A wise decision, my friend. How are you trying to connect? /etc/network/interfaces?

Blacklisting the onboard simply means finding out its driver and making sure it does not load so that the interface never starts. What is your problem with the onboard?

---

### Post by Parapan on 2011-07-09
Oops I meant the network managing applets. The network-manager package in synaptic package manager still exists. I have configured the IP settings in /etc/network/interfaces. But the same problem remains. Lookups are still very slow only in Ubuntu. A ping request to google took 10 seconds (The same request takes 2seconds in Windows 7). Sorry but I'm very lost here , I'm not too sure myself where this is going. I've tried fixing only what I suspected.. What do you suggest? How should I go about blacklisting the onboard device's drivers?

---

### Post by chili555 on 2011-07-09
Before we blacklist it, let's troubleshoot it. First, let's see what it is. Please open a terminal and run and post:```
lspci -nn | grep 0200
```What does it do when you try to connect?

---

### Post by Parapan on 2011-07-09
```

01:08.0 Ethernet controller [[COLOR="Red"]0200[/COLOR]]: D-Link System Inc DGE-530T Gigabit Ethernet Adapter (rev 11) [1186:4b01] (rev 11)

```

I can connect fine, the NIC works , but its just lookups that are very slow..

---

### Post by chili555 on 2011-07-09
> I can connect fine, the NIC works , but its just lookups that are very slow..Can you hook it up, connect and let us see:```
sudo ethtool eth0
```Isn't it a bit late there?


--------------

Hint to chili: sky2 MSI??

---

### Post by Parapan on 2011-07-10
```

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: No
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pg
    Wake-on: g
    Current message level: 0x00000037 (55)
                   drv probe link ifdown ifup
    Link detected: yes

```

---

### Post by chili555 on 2011-07-10
That looks perfect. Now let's do some more diagnostics. Still with only the D-link internal hooked up, please run and post:```
cat /etc/resolv.conf
route -n
ping -c3 www.google.com
ping -c3 74.125.93.105
```Thanks.

---

### Post by Parapan on 2011-07-10
Hey firstly thanks a lot chili555 for continuing to help me on this issue :D..

Did you mean D'link PCI? The Internal Card is a nForce network controller.. Which one did you want me to test again?


Anyways here are the results of those commands with the D'link PCI enabled and onboard NIC disabled


**cat /etc/resolv.conf**
```

# Generated by NetworkManager
domain Home
search Home Subnet
nameserver 192.168.1.1
nameserver 125.22.47.125
nameserver 202.56.250.5
nameserver 8.8.8.8

```



**route -n**
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

```



**ping -c3 [www.google.com](www.google.com)**
```

PING www.l.google.com (74.125.236.80) 56(84) bytes of data.
64 bytes from 74.125.236.80: icmp_req=1 ttl=54 time=60.2 ms
64 bytes from 74.125.236.80: icmp_req=2 ttl=54 time=68.7 ms
64 bytes from 74.125.236.80: icmp_req=3 ttl=54 time=45.9 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10297ms
rtt min/avg/max/mdev = 45.926/58.299/68.734/9.413 ms



```




**ping -c3 74.125.93.105**
```

PING 74.125.93.105 (74.125.93.105) 56(84) bytes of data.
64 bytes from 74.125.93.105: icmp_req=1 ttl=46 time=295 ms
64 bytes from 74.125.93.105: icmp_req=2 ttl=46 time=297 ms
64 bytes from 74.125.93.105: icmp_req=3 ttl=46 time=346 ms

--- 74.125.93.105 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 295.888/313.285/346.245/23.326 ms

```

---

### Post by chili555 on 2011-07-10
I thought we were troubleshooting the onboard. Is that not what you wanted to do?

---

### Post by Parapan on 2011-07-11
Hmm not exactly actually.. I have stopped using the onboard NIC and I don't want to use it anymore. The reason I brought it into the picture was because I was wondering if it's old configuration in linux is causing issues after installing the new D'link NIC. I don't intend on using the onboard for anything. All I'm trying to do is just figure out why websites take 5-10 seconds to lookup and load when the same happens in Windows in under 2-3 seconds..

---

### Post by chili555 on 2011-07-11
The settings you posted above, route, particularly, relate to eth0 which is usually, not always, the first (in your case the internal) ethernet interface. Let's take a look at:```
sudo lshw -C network
```Completion of this command takes a few moments, please be patient. When we are clear on which is eth0 and which is eth1, we'll blacklist the driver for the internal and fix the route for the add-on. Hopefully, then your lookups will improve.

---

### Post by Parapan on 2011-07-11
```

  *-network               
       description: Ethernet interface
       product: DGE-530T Gigabit Ethernet Adapter (rev 11)
       vendor: D-Link System Inc
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 11
       serial: 00:24:01:14:eb:39
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 duplex=full firmware=N/A ip=192.168.1.10 latency=32 link=yes maxlatency=31 mingnt=23 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 memory:fdefc000-fdefffff ioport:ac00(size=256) memory:fdec0000-fdedffff

```

---

### Post by chili555 on 2011-07-11
Only one listing is here. Is that the add-on PCI card? Why doesn't the internal show up? Is it disabled in the BIOS? 

I assume the extra settings in /etc/resolv.conf were DNS nameservers you added in Network Manager. You might edit /etc/resolv.conf to read as follows and see if lookups improve or degrade:```
# Generated by NetworkManager
#domain Home
#search Home Subnet
nameserver 192.168.1.1
nameserver 125.22.47.125
nameserver 202.56.250.5
nameserver 8.8.8.8
```I might also try:```
# Generated by NetworkManager
#domain Home
#search Home Subnet
#nameserver 192.168.1.1
#nameserver 125.22.47.125
#nameserver 202.56.250.5
nameserver 8.8.8.8
```I believe the change is immediate after you save and close. Test with:```
ping -c3 74.125.93.105

```NM will rewrite on reboot but if this helps, we can make it persistent.

---

### Post by Parapan on 2011-07-11
```

PING 74.125.93.105 (74.125.93.105) 56(84) bytes of data.
64 bytes from 74.125.93.105: icmp_req=1 ttl=46 time=312 ms
64 bytes from 74.125.93.105: icmp_req=2 ttl=46 time=458 ms
64 bytes from 74.125.93.105: icmp_req=3 ttl=46 time=517 ms

--- 74.125.93.105 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 312.792/429.454/517.141/85.905 ms

```

Thats the result of the first ping using all 4 nameservers as you suggest



```

PING 74.125.93.105 (74.125.93.105) 56(84) bytes of data.
64 bytes from 74.125.93.105: icmp_req=1 ttl=46 time=294 ms
64 bytes from 74.125.93.105: icmp_req=2 ttl=46 time=304 ms
64 bytes from 74.125.93.105: icmp_req=3 ttl=46 time=297 ms

--- 74.125.93.105 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 294.890/298.885/304.742/4.278 ms

```

Thats the result of the second ping using only google 8.8.8.8 nameserver

---

### Post by chili555 on 2011-07-11
> Thats the result of that after I changed the .. My first suggestion or my second?

---

### Post by Parapan on 2011-07-12
Sorry that was a bit vague, I've edited the post above to show you the results of both the suggestions

---

### Post by Parapan on 2011-07-12
WOOOT Its fixed! I just remembered the other day I was trying to configure a Network attached storage and files and I read some random blog post and changed the "host" value in the /etc/nsswitch.conf to  "mdns4_minimal [NOTFOUND=return] wins dns mdns4".. Now I changed it back to "files dns, and everything is back to normal :D. Thanks a ton for everything chili555. If theres any way I can give you credit points for helping me out on these forums , let me know :). Finally, I can close this thread!

---

### Post by chili555 on 2011-07-12
Great work! Glad it's all working as expected. Have fun!

---

