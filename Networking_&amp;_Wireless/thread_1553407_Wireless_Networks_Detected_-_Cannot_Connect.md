---
title: "Wireless Networks Detected - Cannot Connect"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by Ikka3990 on 2010-08-15
I am having problems with getting my wireless working on Ubuntu 10.04 (linux kernel 2.6.32-24-generic) on my Lenovo Y330 laptop. The network-manager can detect wireless networks but cannot connect. This problem has started only after upgrading to 10.04. Also, I am able to connect to the network using a live-cd.

```

root@shitikanth-laptop:~# lspci -nn | grep -E 'Ethernet|Network'
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]

``````

root@shitikanth-laptop:~# ps -ef | grep -E -i 'supplicant|Netwo|nm-app'
root      1885     1  0 09:52 ?        00:00:00 /sbin/wpa_supplicant -u -s
1000      5604     1  0 09:52 ?        00:00:07 /usr/bin/knetworkmanager
root     20698     1  0 10:44 ?        00:00:00 NetworkManager
root     21730 16495  0 11:14 pts/1    00:00:00 grep -E -i supplicant|Netwo|nm-app

``````
root@shitikanth-laptop:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:16:06:2e:6b  
          inet addr:172.24.64.158  Bcast:172.24.71.255  Mask:255.255.248.0
          inet6 addr: 2001:4490:0:e:21f:16ff:fe06:2e6b/64 Scope:Global
          inet6 addr: fe80::21f:16ff:fe06:2e6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:133137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10058143 (10.0 MB)  TX bytes:201567 (201.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:339025 (339.0 KB)  TX bytes:339025 (339.0 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:16:ea:ae:15:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:16:ea:ae:15:34  
          inet addr:169.254.6.77  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

``````

root@shitikanth-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"WPC1"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
vboxnet0  no wireless extensions.

``````

root@shitikanth-laptop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 66:DC:D6:87:00:07
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-28 dBm  
                    Encryption key:off
                    ESSID:"WPC1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=000000014b04a32c
                    Extra: Last beacon: 2768ms ago
                    IE: Unknown: 000457504331
                    IE: Unknown: 010882840B160C121824
                    IE: Unknown: 030101
                    IE: Unknown: 06020000
                    IE: Unknown: 32043048606C

vboxnet0  Interface doesn't support scanning.

```I hope I am giving the relevant information.

---

### Post by kiridude on 2010-08-15
lets see the output of lshw -C network

---

### Post by Ikka3990 on 2010-08-15
```
root@shitikanth-laptop:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:16:06:2e:6b
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=sb v3.04 ip=172.24.64.158 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:95100000-9510ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:ae:15:34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.32-24-generic firmware=8.24.2.12 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:94100000-94101fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by kiridude on 2010-08-15
Try removing network manager and install wicd (with the cable).  Select the router you want to connect to and click "properties" to enter your password. See if that helps.

---

### Post by Ikka3990 on 2010-08-15
I tried connecting using Wicd. It doesn't proceed after "Obtaining IP address" stage. Previously, I had tried this-
```
sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:16:ea:ae:15:34
Sending on   LPF/wlan0/00:16:ea:ae:15:34
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```
This might also be useful -
```

~$: dmesg| grep wlan0
[   41.320820] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  277.012899] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  614.948971] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  615.301072] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  745.528577] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  893.914922] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  894.240913] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  894.424872] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  952.336462] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1102.848260] Unknown OutputIN= OUT=wlan0 SRC=169.254.6.77 DST=169.254.255.255 LEN=164 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17500 DPT=17500 LEN=144 
[ 1132.888648] Unknown OutputIN= OUT=wlan0 SRC=169.254.6.77 DST=169.254.255.255 LEN=164 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=17500 DPT=17500 LEN=144 

```

---

### Post by kiridude on 2010-08-15
If you can see the router you want and wicd tries to connect, I assume you're drivers are in place. Have a look at administration > hardware drivers.

When I see wicd stuck on "obraining IP" its usually a password issue. Did you go into properties, check "use encryption" and enter your password and password type?

---

### Post by Ikka3990 on 2010-08-15
The network I am trying to connect to does not require any password. Besides, I am able to connect to the same network with a live-cd of ubuntu 10.04.

---

### Post by kiridude on 2010-08-15
when I last upgraded, my wireless also stopped working. I had to enable my wireless drivers as they were propriety. Did you check that?

---

### Post by larrydag on 2010-08-15
I'm having the same issue.  I checked for Hardware Drivers and it is telling me there are no proprietary drivers in use on the system.  I'm using a Dell C640

---

### Post by larrydag on 2010-08-15
I'm having the same issue.  I checked for Hardware Drivers and it is telling me there are no proprietary drivers in use on the system.  I'm using a Dell C640

---

### Post by kiridude on 2010-08-16
> **larrydag said:**
> I'm having the same issue.  I checked for Hardware Drivers and it is telling me there are no proprietary drivers in use on the system.  I'm using a Dell C640

Did you check "propriety drivers" in administration > software sources > ubuntu software tab?

---

### Post by Mojo- on 2010-08-31
Hi,

Are there any updates regarding this issue, I also upgraded to netbook recently and am seeing the same behaviour discribed here.  I am also using a Dell C640 and I can see my unencrypted wireless network, but am unable to get my laptop connected to it.

Any information you would need to get this moving forward again, just let me know.

Thanks in advance.
-M

---

### Post by Mojo- on 2010-09-01
Just to give you guys a heads up, I spent most of my evening looking for a solution and finally found on (partially so far).

I installed "wicd" instead of the normal network manager.  You can find information on how to install it in this thread : 
[http://ubuntuforums.org/showthread.php?t=1211513](http://ubuntuforums.org/showthread.php?t=1211513)

The installation of wicdgot my wireless to work again for my main user, however another user on my machine is unable to connect still.  Atleast it's a step in the right direction, hope this helped you guys.

Regards,
M

---

