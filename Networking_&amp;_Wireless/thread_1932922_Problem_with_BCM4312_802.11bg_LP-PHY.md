---
title: "Problem with BCM4312 802.11b/g LP-PHY"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by james591 on 2012-02-28
```
shri@ubuntu:~$ sudo lshw -C network
[sudo] password for shri: 
Sorry, try again.
[sudo] password for shri: 
  *-network DISABLED      
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:5d:a9:56
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:99700000-99703fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:e5:35:af
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:3000(size=256) memory:93410000-93410fff memory:93400000-9340ffff memory:93420000-9343ffff
shri@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:e5:35:af  
          inet6 addr: fe80::21e:ecff:fee5:35af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2043 (2.0 KB)  TX bytes:4267 (4.2 KB)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:168 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12208 (12.2 KB)  TX bytes:12208 (12.2 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.224.163.56  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:233 errors:0 dropped:0 overruns:0 frame:0
          TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:84218 (84.2 KB)  TX bytes:47301 (47.3 KB)

shri@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

ppp0      no wireless extensions.

shri@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

shri@ubuntu:~$ ping -c 4 google.com
PING google.com (173.194.36.8) 56(84) bytes of data.
64 bytes from bom04s01-in-f8.1e100.net (173.194.36.8): icmp_req=1 ttl=51 time=449 ms
64 bytes from bom04s01-in-f8.1e100.net (173.194.36.8): icmp_req=2 ttl=51 time=459 ms
64 bytes from bom04s01-in-f8.1e100.net (173.194.36.8): icmp_req=3 ttl=51 time=449 ms
64 bytes from bom04s01-in-f8.1e100.net (173.194.36.8): icmp_req=4 ttl=51 time=450 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 13139ms
rtt min/avg/max/mdev = 449.652/452.350/459.922/4.374 ms


```

these are my results.

Please guide me how to resolve very slow internet, however my usb modem and wifi works very good in windows 7 on same machine.

Thanks

---

### Post by james591 on 2012-02-28
please give a solution

---

### Post by varunendra on 2012-02-28
> **james591 said:**
> ```

  *-network DISABLED      
       description: Wireless interface
       product: **BCM4312 802.11b/g [COLOR=Red]LP-PHY[/COLOR]**
..
       .. driver=wl0 driverversion=5.100.82.38 latency=0..

shri@ubuntu:~$ ping -c 4 google.com
PING google.com (173.194.36.8) 56(84) bytes of data.
64 bytes from bom04s01-in-f8.1e100.net (173.194.36.8): icmp_req=1 ttl=51 time=**449** ms
64 bytes from bom04s01-in-f8.1e100.net (173.194.36.8): icmp_req=2 ttl=51 time=**459** ms
64 bytes from bom04s01-in-f8.1e100.net (173.194.36.8): icmp_req=3 ttl=51 time=**449** ms
64 bytes from bom04s01-in-f8.1e100.net (173.194.36.8): icmp_req=4 ttl=51 time=**450** ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 13139ms
rtt min/avg/max/mdev = 449.652/452.350/459.922/4.374 ms

```
James, (or Shri??)

Assuming you are referring to your wireless interface, please try this first-
Open a terminal, and run these commands (while you are connected to internet via cable connection):
```
sudo apt-get purge firmware-b43-installer
sudo apt-get install firmware-b43-lpphy-installer
```Then reboot and try to connect via wireless and post back the results (whether it improved or not).

[s]If this does not help, please create a new thread and post your question there, since wireless problems and their causes are mostly different for different people, and your card is entirely different than the one originally discussed in this thread. (I'll request a mod to move your post to its own thread with a suitable title).[/s][COLOR=Red](obsolete now)[/COLOR]

As a side note, your ping latency seems very high (400+ ms). Generally, it shouldn't exceed 60-70ms. Accordingly, you should try changing DNS in Network Manager to get better latencies. Try google's public DNS servers (8.8.8.8 and 8.8.4.4) and see if it gets below 70ms (result of *ping google.com*)


**_PS_:**
When you post any output codes, you should wrap it into [ code].. and .. [ /code] tags by clicking on # at the top of edit box (in which you create new post) to automatically generate those tags, then just copy-paste the output code in-between those tags.

It preserves formatting, makes it more readable, and avoids turning of code parts into those smileys :)

---

### Post by james591 on 2012-02-28
```


sudo apt-get remove bcmwl-kernel-source

```

thanks for your reply with a solution, i have installed the driver for my wifi card but it worked after removing bcmwl-kernel-source with the code given above. My ping time is also reduced by changing the DNS server.

Thanks a lot

---

### Post by varunendra on 2012-02-28
> **james591 said:**
> ```


sudo apt-get remove bcmwl-kernel-source

```thanks for your reply with a solution, i have installed the driver for my wifi card but it worked after removing bcmwl-kernel-source with the code given above. My ping time is also reduced by changing the DNS server.

Thanks a lot
You're welcome.

It is interesting that you got it working after removing the driver! Because the package I suggested is just a 'firmware' installer, not the driver itself. So I'm wondering which driver is currently in use. It would be great if you post the outputs of:
```
lsmod
```

Also, if the connection is stable now, I think you should mark this thread as [Solved]. (see how in my signature).

---

### Post by bkratz on 2012-02-29
> **varunendra said:**
> You're welcome.

It is interesting that you got it working after removing the driver! Because the package I suggested is just a 'firmware' installer, not the driver itself. So I'm wondering which driver is currently in use. It would be great if you post the outputs of:
```
lsmod
```Also, if the connection is stable now, I think you should mark this thread as [Solved]. (see how in my signature).


The driver that he/she removed is related to the STA driver--which was probably conflicting with the B43 required.

---

