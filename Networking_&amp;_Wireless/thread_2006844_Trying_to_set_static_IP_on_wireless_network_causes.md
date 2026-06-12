---
title: "Trying to set static IP on wireless network causes disconnection"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by thomas144 on 2012-06-19
Hi, everyone.
I've been trying to set a static IP address for my laptop for a while now, but I can't get past this problem. I have tried to change my IP address with this procedure: I right-click on the Network Manager icon and select "Edit Connections...," which opens up the network settings screen. I go to the wireless tab, select my wireless profile and edit it. Going to the IPv4 settings tab, I change the method to manual. I enter the IP address, the subnet mask, the gateway address, and the IP addressed of my DNS servers. When I click "Apply" is where the problem starts. My wireless connection immediately disconnects. I am able to reconnect to the router by typing in my password again, but then it creates a new profile instead of using the one I modified.

Some additional information: I used this procedure before to assign a static IP to my desktop computer, but that was over a wired connection. Also, I'm a fairly experienced Linux user and I'm comfortable with using the command line, but I'm no expert. My wireless card is a BCM4312 card, but it hasn't given me any trouble once it was configured.

---

### Post by TheMrOrange on 2012-06-19
open a terminal and type
ifconfig

then try to set the profile as you described and type ifconfig again

post the two output here.

I think that, for some reason, your Network Manager is not writing the configuration that you set

---

### Post by thomas144 on 2012-06-19
First of all, thanks for being willing to help me! ;)

Now, the output of the command you requested. This is the output of ifconfig when I'm connected with the default settings. At this point, my Internet connection is working fine. My IP is 192.168.2.11, which was assigned by the router's DHCP. Also, the connection we're working with is eth1, my wireless network. Eth0 is the wired connection.
```
eth0      Link encap:Ethernet  HWaddr 00:25:64:76:6a:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 70:1a:04:8d:c7:ca  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe8d:c7ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93805 errors:0 dropped:0 overruns:0 frame:11867
          TX packets:78903 errors:62 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108431940 (108.4 MB)  TX bytes:11493498 (11.4 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```Now, I change the configuration method to manual and set my IP address to 192.168.2.5. To the best of my knowledge, this address is not taken by any of the devices on my network and is not in the range of addresses the router uses for DHCP. When I click "Accept," I'm suddenly offline. Here's the output of ifconfig at this point:
```
eth0      Link encap:Ethernet  HWaddr 00:25:64:76:6a:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 70:1a:04:8d:c7:ca  
          inet6 addr: fe80::721a:4ff:fe8d:c7ca/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:93976 errors:0 dropped:0 overruns:0 frame:11905
          TX packets:79050 errors:62 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108594564 (108.5 MB)  TX bytes:11522573 (11.5 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```Then, I can reconnect to the network after typing in my password, which is usually unnecessary. Now, ifconfig says this:
```
eth0      Link encap:Ethernet  HWaddr 00:25:64:76:6a:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 70:1a:04:8d:c7:ca  
          inet addr:192.168.2.11  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::721a:4ff:fe8d:c7ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94004 errors:0 dropped:0 overruns:0 frame:11927
          TX packets:79081 errors:68 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:108606153 (108.6 MB)  TX bytes:11526893 (11.5 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```Everything is up and running as usual. However, the network connection settings screen says otherwise. Attached is a screenshot of it. As demonstrated by the picture, there are two profiles. On the bottom is the profile whose settings I've modified. Above it is another profile that Network Manager generated when I reconnected. It seems that when I reconnect to the network, it doesn't use the modified settings and instead generates a new set of settings automatically and uses that.

---

### Post by thomas144 on 2012-06-21
*Bump*

---

### Post by thomas144 on 2012-06-26
*Bump*
Sorry if I shouldn't be bumping repeatedly, but it's been four days.
Can anyone help?

---

### Post by chili555 on 2012-06-26
I think I might delete all instances of your current profile. Set your details and then restart Network Manager:```
sudo service network-manager restart
```I am not sure how the address x.11 can be inside the range of the DHCP server but not x.5. Can you please check in the administration pages of the router? Better yet, try 192.168.2.105.

Can you connect now?

---

