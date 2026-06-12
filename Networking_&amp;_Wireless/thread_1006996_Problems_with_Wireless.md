---
title: "Problems with Wireless"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by argordon on 2008-12-09
Hi, after my hard drive crashed I decided to install Ubuntu 8.10 instead of Windows.  I am able to get the internet fine with a cable but can't seem to get the wireless working.  When I click on the network icon on the top right, my wireless network is displayed and the authentication screen pops up, but once I enter my key and hit connect it never actually connects.  The router is a D-Link DI-624 and the wireless network is "DEFAULT".  I don't know much about any of this, but here is some information about what's going on:

System->Administration->Hardware Drivers says "no proprietary drivers are  in use" and Support for Atheros 802.11 wireless LAN cards is activated and in use.

(the following were done while hooked up to a wired network) 
ashley@BASH:~$ sudo lshw -C network
[sudo] password for ashley: 
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:7a:15:02
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI duplex=full firmware=N/A ip=192.168.0.102 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:4e:4b:bf:4c
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 16:b1:81:ce:3d:19
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
ashley@BASH:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"DEFAULT"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:0B:2B:AA   
          Bit Rate:1 Mb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/70  Signal level=-38 dBm  Noise level=-92 dBm
          Rx invalid nwid:32631  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ashley@BASH:~$ sudo dhclient ath0
wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:05:4e:4b:bf:4c
Sending on   LPF/ath0/00:05:4e:4b:bf:4c
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Any help would be greatly appreciated!!

Ashley

---

### Post by superprash2003 on 2008-12-10
post output of ifconfig

---

### Post by argordon on 2008-12-10
ashley@BASH:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:05:4e:4b:bf:4c  
          inet6 addr: fe80::205:4eff:fe4b:bf4c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ath0:avahi Link encap:Ethernet  HWaddr 00:05:4e:4b:bf:4c  
          inet addr:169.254.5.251  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

eth0      Link encap:Ethernet  HWaddr 00:0d:60:7a:15:02  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fe7a:1502/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:56763719 (56.7 MB)  TX bytes:4402299 (4.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23876 (23.8 KB)  TX bytes:23876 (23.8 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-05-4E-4B-BF-4C-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:732987 errors:0 dropped:0 overruns:0 frame:26104
          TX packets:69329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:70869692 (70.8 MB)  TX bytes:2473401 (2.4 MB)
          Interrupt:11

---

### Post by superprash2003 on 2008-12-11
you have an ip address issue .. try this first install old network manager [http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html](http://prash-babu.blogspot.com/2008/11/how-to-enable-roaming-mode-in-ubuntu.html) follow this till step 4 .. then connect like this [http://prash-babu.blogspot.com/2008/10/wifi-tip-always-better-to-disable.html](http://prash-babu.blogspot.com/2008/10/wifi-tip-always-better-to-disable.html) .. first use DHCP .. if that doesnt work try static ip..

---

### Post by argordon on 2008-12-25
Thanks for your help! Everything is working well now!

---

