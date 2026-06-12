---
title: "Struggling with ethernet problem for the past TEN days-Sporadic connection  on 12.04"
date: 2012-07-03
forum: Networking &amp; Wireless
---

### Post by ravikanth1988 on 2012-07-03
The following is the situation:
Laptop: Lenovo X200 Tablet
Dual boot with Windows 7 and ubuntu 12.04
ethernet works perfectly on windows 7. Works sporadically on ubuntu 12.04. Tried getting a solution on IRC channel. No progress on that front either.

I was suggested to live boot Ubuntu 12.10 to check if ethernet is working but the monitor blanks in the process and gets stuck. Bodhi.zazen says its a kernel issue.

Can you suggest a procedure for diagnosis and solution?

Laptop Specs[B]
Communications[/B]
Fax/modem description 56K V.92 designed modem AMOM
Fax/modem speed[3] 56Kbps data/14.4Kbps fax
Infrared port No
**Ethernet description**: Integrated Intel 82567LM Gigabit Network Adapter
Network speed 1000Mbps, 100Mbps, 10Mbps
Ethernet interface type Gigabit Ethernet- Integrated
Ethernet on motherboard Yes



regards,
ravikanth

---

### Post by ravikanth1988 on 2012-07-05
Here is the set of diagnostics I know of. If you need any more commands please let me know.

If you prefer the paste bin version Please head to [http://paste.ubuntu.com/1077338/](http://paste.ubuntu.com/1077338/)

```

ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ ifconfig
 

 eth0      Link encap:Ethernet  HWaddr 00:1f:16:1a:0e:7e   
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:6 errors:0 dropped:0 overruns:0 frame:0
           TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000  
           RX bytes:1464 (1.4 KB)  TX bytes:11780 (11.7 KB)
           Interrupt:20 Memory:f2700000-f2720000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:16 errors:0 dropped:0 overruns:0 frame:0
           TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0  
           RX bytes:1312 (1.3 KB)  TX bytes:1312 (1.3 KB)
 

 ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ dmesg | grep eth0
 [    2.192540] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:1f:16:1a:0e:7e
 [    2.192544] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
 [    2.192572] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1008FF-0FF
 [   18.248171] ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   20.140392] ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   21.680945] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
 [   21.680951] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
 [   21.681139] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
 [   26.392402] ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   26.768517] ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   28.432928] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
 [   28.432935] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
 [   28.433146] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
 [   39.136070] eth0: no IPv6 routers present
 [   80.352091] eth0: no IPv6 routers present
 

 ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ nm-tool
 

 NetworkManager Tool
 

 State: connecting
 

 - Device: wlan0 ----------------------------------------------------------------
   Type:              802.11 WiFi
   Driver:            iwlwifi
   State:             unavailable
   Default:           no
   HW Address:        00:22:FA:95:D1:C6
 

   Capabilities:
 

   Wireless Properties
     WEP Encryption:  yes
     WPA Encryption:  yes
     WPA2 Encryption: yes
 

   Wireless Access Points  
 

 

 - Device: eth0  [Auto Ethernet] ------------------------------------------------
   Type:              Wired
   Driver:            e1000e
   State:             connecting (getting IP configuration)
   Default:           no
   HW Address:        00:1F:16:1A:0E:7E
 

   Capabilities:
     Carrier Detect:  yes
     Speed:           100 Mb/s
 

   Wired Properties
     Carrier:         on
 

 ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ ip a | grep inet
     inet 127.0.0.1/8 scope host lo
 

 ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ dmesg | grep -e e100 -e eth
 [    0.389224] i2c-core: driver [aat2870] using legacy suspend method
 [    0.389227] i2c-core: driver [aat2870] using legacy resume method
 [    2.000887] e1000e: Intel(R) PRO/1000 Network Driver - 1.5.1-k
 [    2.000890] e1000e: Copyright(c) 1999 - 2011 Intel Corporation.
 [    2.000927] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
 [    2.000940] e1000e 0000:00:19.0: setting latency timer to 64
 [    2.001184] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
 [    2.192540] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 00:1f:16:1a:0e:7e
 [    2.192544] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
 [    2.192572] e1000e 0000:00:19.0: eth0: MAC: 7, PHY: 8, PBA No: 1008FF-0FF
 [   18.248171] ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   20.085552] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
 [   20.140122] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
 [   20.140392] ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   21.680945] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
 [   21.680951] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
 [   21.681139] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
 [   26.336243] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
 [   26.392112] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
 [   26.392402] ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   26.712268] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
 [   26.768106] e1000e 0000:00:19.0: irq 45 for MSI/MSI-X
 [   26.768517] ADDRCONF(NETDEV_UP): eth0: link is not ready
 [   28.432928] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
 [   28.432935] e1000e 0000:00:19.0: eth0: 10/100 speed: disabling TSO
 [   28.433146] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
 [   39.136070] eth0: no IPv6 routers present
 [   80.352091] eth0: no IPv6 routers present
 [  128.536091] eth0: no IPv6 routers present
 [  176.760115] eth0: no IPv6 routers present
 

 ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ ethtool eth0
 Settings for eth0:
     Supported ports: [ TP ]
     Supported link modes:   10baseT/Half 10baseT/Full  
                             100baseT/Half 100baseT/Full  
                             1000baseT/Full 
     Supported pause frame use: No
     Supports auto-negotiation: Yes
     Advertised link modes:  10baseT/Half 10baseT/Full  
                             100baseT/Half 100baseT/Full  
                             1000baseT/Full 
     Advertised pause frame use: No
     Advertised auto-negotiation: Yes
     Speed: 100Mb/s
     Duplex: Full
     Port: Twisted Pair
     PHYAD: 2
     Transceiver: internal
     Auto-negotiation: on
     MDI-X: on
 Cannot get wake-on-lan settings: Operation not permitted
     Current message level: 0x00000001 (1)
                    drv
 Cannot get link status: Operation not permitted
 

 

 ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ sudo ethtool eth0
 [sudo] password for ravikanth:  
 Settings for eth0:
     Supported ports: [ TP ]
     Supported link modes:   10baseT/Half 10baseT/Full  
                             100baseT/Half 100baseT/Full  
                             1000baseT/Full 
     Supported pause frame use: No
     Supports auto-negotiation: Yes
     Advertised link modes:  10baseT/Half 10baseT/Full  
                             100baseT/Half 100baseT/Full  
                             1000baseT/Full 
     Advertised pause frame use: No
     Advertised auto-negotiation: Yes
     Speed: 100Mb/s
     Duplex: Full
     Port: Twisted Pair
     PHYAD: 2
     Transceiver: internal
     Auto-negotiation: on
     MDI-X: on
     Supports Wake-on: pumbg
     Wake-on: g
     Current message level: 0x00000001 (1)
                    drv
     Link detected: yes
 

 

```

---

### Post by ravikanth1988 on 2012-07-06
More diagnostics

[http://paste.ubuntu.com/1077744/](http://paste.ubuntu.com/1077744/)

comment by compdoc on IRC: 70-persistent-net.rules  shows two network cards. Sometimes, when booting, one or the other can be ready first and screw things up

```

ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ cat /etc/network/interfaces
 auto lo
 iface lo inet loopback
 

 ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ cat /etc/udev/rules.d/70-persistent-net.rules
 # This file was automatically generated by the /lib/udev/write_net_rules
 # program, run by the persistent-net-generator.rules rules file.
 #
 # You can modify it, as long as you keep each rule on a single
 # line, and change only the value of the NAME= key.
 

 # PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
 SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1f:16:1a:0e:7e", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
 

 # PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwlwifi)
 SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:fa:95:d1:c6", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
 ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ 
 
```

---

### Post by Bucky Ball on 2012-07-06
12.10 is a bad idea if you're looking for a stable system. Not sure why anyone would advise that as it's three months off release; definitely no guarantee of stability there. 

10.04 LTS is rock solid and supported for another year. Or you could try 11.10 which is not a long-term support release but is supported til April 2013. Did everything work okay when you booted from the Live installation CD? (into 'Try Ubuntu', not Install, if you tried it first).

Could you perhaps post the result of this command:

```
sudo lshw -C network
```

If Bohdi is right and it is a kernel issue then you could try running the appropriate kernel - if it exists - on an older release (I run 10.04 LTS with the 11.04 kernel installed as that one has the driver for my wireless in it whereas my card will not work at all with the native 10.04 kernel). You could use the 12.10 kernel for instance on 11.10 I would think, with some tweaking and searching. That kernel may be pretty much 'bleeding edge' though so expect breakages.

---

### Post by ravikanth1988 on 2012-07-06
Here is the output

[http://paste.ubuntu.com/1077850/](http://paste.ubuntu.com/1077850/)


```



 

 ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ sudo lshw -C network
 [sudo] password for ravikanth:  
   *-network                
        description: Ethernet interface
        product: 82567LM Gigabit Network Connection
        vendor: Intel Corporation
        physical id: 19
        bus info: pci@0000:00:19.0
        logical name: eth0
        version: 03
        serial: 00:1f:16:1a:0e:7e
        size: 100Mbit/s
        capacity: 1Gbit/s
        width: 32 bits
        clock: 33MHz
        capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=1.8-3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
        resources: irq:45 memory:f2700000-f271ffff memory:f2925000-f2925fff ioport:1840(size=32)
   *-network DISABLED
        description: Wireless interface
        product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
        vendor: Intel Corporation
        physical id: 0
        bus info: pci@0000:03:00.0
        logical name: wlan0
        version: 00
        serial: 00:22:fa:95:d1:c6
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-23-generic-pae firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
        resources: irq:48 memory:f2500000-f2501fff
 ravikanth@ravikanth-ThinkPad-X200-Tablet:~$ 
 

```

---

### Post by Bucky Ball on 2012-07-06
Okay, well, theoretically that all looks okay for wireless. The Intel drivers should be in most kernels and there is indeed a driver loaded. 

```
driverversion=3.2.0-23-generic-pae
```

Your wireless, though, seems set to 'Disabled'. 

Sounds too simple but just in case: Could you right click on the network icon and make sure 'Enable wireless' and 'Enable Networking' are ticked, please?

---

### Post by ravikanth1988 on 2012-07-06
Bucky ball,
I am not using wireless at the moment because I dont have a wifi router. The manual switch of wifi is off on my laptop
By the way ethernet suddenly starts working again :( No idea why this is happening. 

One of the members in IRC says since I have a dynamic IP assigned the problem is that Ubuntu is not able to get an IP assigned to itself. The member really did not offer a workable solution at the moment

---

### Post by Bucky Ball on 2012-07-06
Ah, that makes more sense. You have a static IP assigned in network manager on your local machine, no? If so, you need to check your router is not trying to give you an IP as well via its DHCP server. Get into the router config and make sure you have the DHCP server switched OFF! (Otherwise the router is trying to serve you an IP and your local machine is trying to force the router to accept the static one you've set. Log jam!)

Your other option, if there are computers that aren't running static IPs and need one served from the router, is to limit the range of IP addresses the router will serve. 

To do this, leave DHCP serving ON on the router, but limit it to say 192.168.0.100-192.168.0.110. Then your machine can happily live with a static IP set at, say, 192.168.0.111 or whatever. Just as long as your static IP is NOT in the range the router is serving via DHCP, if you follow what I'm saying.

Give that a check and a try ... Good luck. ;)

---

### Post by ravikanth1988 on 2012-07-06
The problem is I don't even have a router. It is wireless based ethernet service. i have a small box at the top of my house. This gets connected to something in the nearby tower. The box on top of my house comes down. There is a little box near my computer with RJ-45 pin(connects to my computer) and ODU pin( connects to the top of my house) and that is it. I dont know what ODU pin is but it looks very similar to RJ-45. The support guy said I should not be reversing the connections under any cirucmstances and that is it ! 

An IP gets assigned everytime I power on the Ethernet  service.

---

### Post by Bucky Ball on 2012-07-06
Well, I don't doubt that is your problem, then. Most ISPs want you to pay extra if you want to use a static IP to connect to the internet else you will be served one, and you have no choice about that. The way around this is to use a router. That way the router is served the IP address but serves its own to the LAN (local area network, your computer) unless you set your own static inside the LAN (because you can't set it for the WAN).

My workaround for this is to buy a router. They are quite inexpensive but I know things are tight for a lot of us right now!

Easy way to test if this is your problem: Switch off your static IP set on the local machine (set to 'Automatic' in network manager), reboot and you should connect straight away. If you do, problem found. If you don't, keep hunting. ;)

---

### Post by ravikanth1988 on 2012-07-06
In the network manager. I always set it to automatic(DHCP) in the IPV4 settings and I dont get connected right away sometimes. That is the problem :(

---

### Post by Bucky Ball on 2012-07-06
You said you had a static IP address??? If you are directly plugged in (no router) I would contact the ISP about it as they are providing you local machine directly with its IP address. I'm starting to think this might not have anything to do with Ubuntu as your ethernet card seems to be in working order, identified, drivers and firmware loading. Further proof of this is that it does connect on occasion.

You might try opening a terminal and pinging your ISP if you have their IP. See what comes back.

---

### Post by ravikanth1988 on 2012-07-07
Hey Bucky,
firstly it is a dynamic IP. I dont know how that confusion came up:(
If I assume it is a network problem. Windows always connects fine(I am on dual boot) and that is all the network cares. They say they dont know anything about linux! what could be the problems with assigning dynamic IP in Linux?

---

### Post by ravikanth1988 on 2012-07-08
The pinging to the ISP does not work when it is not connected

---

### Post by ravikanth1988 on 2012-07-08
A Major "BREAKTHROUGH".
When ethernet did not work I copied the settings from WIndows  into ubuntu12.04 and surprisingly it worked.

So it is confirmed that the reason why ethernet was not working is because it is not able to get an IP assigned to itself manually. 

Will buying a router solve this problem? or is there anything else I should do ?

Also
When I added these two lines to /etc/network/interfaces the boot process was a little different but I still was not able to do anything.

auto eth0
iface eth0 inet dhcp 			 		

I would to thank ActionParsnip from IRC for this little insight.

---

