---
title: "Route statement needed for Bridging two Connections"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by joshuapurcell on 2006-06-25
I'm in the process of installing Ubuntu on my desktop computer, which currently doesn't have a network connection (It will eventually use a wireless connection that wasn't able to be automatically configured during install). So far I've done a base server install.

Since wireless isn't working on my desktop, I've brought my laptop over so that I can connect the two systems with a crossover cable. I am currently able to talk between the two computer without any problems. I'm also able to get out to the internet with the wireless connection on my laptop, but internet only works from my laptop at this time.

I would like to know the route command that is needed for me to be able to bridge the two network connections on my laptop. The only thing I've done so far is to install the bridge-utils package, and then I added the following to my /etc/network/interfaces file:```
iface br0 inet static
        address 192.168.1.6
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 172.18.6.1
        bridge_ports all
        dns-nameservers 172.18.6.1
```
Here is the details for my laptop's relevant network connections:```
joshua@jlplaptop:~/downloads/vmware$ ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:0D:60:36:B2:A9
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fe36:b2a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1088 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:276246 (269.7 KiB)  TX bytes:2232 (2.1 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0D:60:36:B2:A9
          inet6 addr: fe80::20d:60ff:fe36:b2a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1123 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:298184 (291.1 KiB)  TX bytes:8318 (8.1 KiB)
          Base address:0x8000 Memory:c0220000-c0240000

wlan0     Link encap:Ethernet  HWaddr 00:0C:41:2B:AB:C2
          inet addr:172.18.6.15  Bcast:172.18.6.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fe2b:abc2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:632221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:890375695 (849.1 MiB)  TX bytes:24689861 (23.5 MiB)
          Interrupt:11 Memory:c2000000-c2002000
```I'm not entirely sure that I even need the bridge-utils package to connect the two network connections on this laptop. Right now eth0 (which is the only wired connection on my laptop) does not have an IP address. Instead, br0 has the IP address and I'm communicating with my desktop through br0. I would think the same thing that is currently happening could be done if I were to just:
1.Delete br0
2.Give eth0 a 192.168.1.0 network address

I'm not sure though, and either way I know that I have two network connections on this laptop that seem to be working correctly at this point. Now all I need to do is get my laptop to route requests from the 192.168.1.0 network to my wireless connection (which is a 172.18.6.0 network).

Thanks for the help, and let me know if any more information is needed.

---

### Post by joshuapurcell on 2006-06-25
[https://help.ubuntu.com/community/WifiDocs/WirelessLaptopInternetAccessPoint](https://help.ubuntu.com/community/WifiDocs/WirelessLaptopInternetAccessPoint)

Found this helpful guide that fixed my problem.

EDIT: I had no idea that Firestarter had the functionality to share a network connection... I've always used for the lone purpose of denying/allowing access to a single network connection at one time. I would still like to know what route statement I would need to add in order to allow the two network connections to talk. One thing that's weird is that the output of **netstat -rn** still looks the same as before I made the simple change in the firestarter GUI.

---

