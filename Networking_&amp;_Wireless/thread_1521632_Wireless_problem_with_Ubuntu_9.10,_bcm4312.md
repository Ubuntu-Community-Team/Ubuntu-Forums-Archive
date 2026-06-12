---
title: "Wireless problem with Ubuntu 9.10, bcm4312"
date: 2010-07-01
forum: Networking &amp; Wireless
---

### Post by monx1 on 2010-07-01
My laptop (HP Mini) is having problems with wireless on Ubuntu 9.10. I tried everything mentioned in the forums but somehow, it is not detecting any networks. 

The icon on top says: Wireless Networks : disconnected

I tried creating a new wireless network, etc. but it is not working. 

I am giving the o/p of some of the commands below:

--------------------------------------------------------------------------------------------------------------------------

madhav@madhav-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:37:0e:e9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:feafc000-feafffff



madhav@madhav-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:24:2b:37:0e:e9  
          inet6 addr: fe80::224:2bff:fe37:ee9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

madhav@madhav-laptop:~$ 




madhav@madhav-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
madhav@madhav-laptop:~$




madhav@madhav-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.



madhav@madhav-laptop:~$ lspci |grep Network
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
madhav@madhav-laptop:~$ 



-------------------------------------------------------------------------------------------------------------------------
I am still not able to scan or browse any networks. 

Interestingly, the wired network works well. Also, the wireless networks used to work well until a few days. 

Any help is appreciated.

Best,
Madhav.

---

### Post by amitabhishek on 2010-07-01
Try using ndiswrapper application with Windows drivers. Its available in Ubuntu repos.

Navigate to XP folder in your driver CD. Copy the entire folder in your /home directory once copied select the file with extension .inf.

---

### Post by bkratz on 2010-07-01
> **monx1 said:**
> My laptop (HP Mini) is having problems with wireless on Ubuntu 9.10. I tried everything mentioned in the forums but somehow, it is not detecting any networks. 

The icon on top says: Wireless Networks : disconnected

I tried creating a new wireless network, etc. but it is not working. 

I am giving the o/p of some of the commands below:

--------------------------------------------------------------------------------------------------------------------------

madhav@madhav-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:37:0e:e9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:feafc000-feafffff



madhav@madhav-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:24:2b:37:0e:e9  
          inet6 addr: fe80::224:2bff:fe37:ee9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

madhav@madhav-laptop:~$ 




madhav@madhav-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
         [COLOR="Red"] Bit Rate:54 Mb/s   Tx-Power:off [/COLOR]  
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          
madhav@madhav-laptop:~$




madhav@madhav-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.



madhav@madhav-laptop:~$ lspci |grep Network
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
madhav@madhav-laptop:~$ 



-------------------------------------------------------------------------------------------------------------------------
I am still not able to scan or browse any networks. 

Interestingly, the wired network works well. Also, the wireless networks used to work well until a few days. 

Any help is appreciated.

Best,
Madhav.

I believe this is the important line ( in red ).  See this post for a brief explanation.

[http://ubuntuforums.org/showpost.php?p=8675153&postcount=2](http://ubuntuforums.org/showpost.php?p=8675153&postcount=2)

---

### Post by monx1 on 2010-07-01
I tried to turn Tx power to auto but could not do so. 

madhav@madhav-laptop:~$ sudo iwconfig eth1 txpower auto
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; Invalid argument.

Any other ideas ? 
Madhav.

---

