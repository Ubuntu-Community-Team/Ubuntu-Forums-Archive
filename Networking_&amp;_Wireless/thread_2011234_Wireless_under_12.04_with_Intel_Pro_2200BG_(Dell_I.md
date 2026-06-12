---
title: "Wireless under 12.04 with Intel Pro 2200BG (Dell Inspiron 1300)"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by topmoose on 2012-06-26
Hello all,

I am trying to equip my old Dell Inspiron 1300 with Ubuntu 12.04. Unfortunately, wireless is not working properly. It's ironic because I installed via the netinstall image (according to [this tutorial]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html")), and during installation, wireless worked perfectly fine!

After booting now, though, it does not work anymore. I tried following [this thread]("http://ubuntuforums.org/showthread.php?t=1982509"), but no success: NM tells me "device not managed" in the GUI. I have repeated the analytical stepts from the old thread. It would be great if someone could help me out:

```
username@hostpc:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
``````
username@hostpc:~$ sudo lshw -C network
[sudo] password for username: 
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 02
       serial: xx:xx:xx:xx:xx:xx
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:18 memory:dfbfe000-dfbfffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 05
       serial: xx:xx:xx:xx:xx:xx
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.2.106 latency=64 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:dfbfd000-dfbfdfff
``````
username@hostpc:~$ lspci -nn | grep 2200
02:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
``````
 username@hostpc:~$ ls -al /lib/firmware | grep ipw
-rw-r--r--  1 root root  209190 Apr  2 21:51 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 Apr  2 21:51 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 Apr  2 21:51 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 Apr  2 21:51 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 Apr  2 21:51 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 Apr  2 21:51 ipw2200-sniffer.fw
``````
username@hostpc:~$ dmesg | grep ipw
[   26.350512] libipw: 802.11 data/management/control stack, git-1.1.13
[   26.350517] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   26.356141] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   26.356145] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   26.356277] ipw2200 0000:02:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.356306] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   27.651516] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)
```The weird thing is that I SEEM to be connected:

```
       configuration: broadcast=yes driver=ipw2200  driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007)  ip=192.168.2.106 latency=64 link=yes
```

Anyone an idea?

Thank you!


topmoose

---

### Post by chili555 on 2012-06-26
You certainly do seem to be connected. What is the problem? Please post:```
iwconfig
ifconfig
ping -c3 8.8.8.8
ping -c3 www.google.com
nm-tool
```Thanks.

---

### Post by topmoose on 2012-06-27
Thanks for the quick reaction!

I am connected - but NM does not care, apparently:

```
username@hostpc:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      IEEE 802.11bg  ESSID:"NetworkName"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: xx:xx:xx:xx:xx:xx 
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=85/100  Signal level=-45 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:7  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:11
``````
username@hostpc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:192.168.2.106  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: xxxx::xxxx:xxxx:xxxx:xxxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75 errors:8 dropped:8 overruns:0 frame:0
          TX packets:106 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18687 (18.6 KB)  TX bytes:13647 (13.6 KB)
          Interrupt:17 Memory:dfbfd000-dfbfdfff 

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
``````
username@hostpc:~$ ping -c3 www.google.com
PING www.l.google.com (173.194.69.105) 56(84) bytes of data.
64 bytes from www.l.google.com (173.194.69.105): icmp_req=1 ttl=47 time=27.4 ms
64 bytes from www.l.google.com (173.194.69.105): icmp_req=2 ttl=47 time=28.1 ms
64 bytes from www.l.google.com (173.194.69.105): icmp_req=3 ttl=47 time=27.5 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 27.410/27.680/28.119/0.313 ms
``````
username@hostpc:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             unmanaged
  Default:           no
  HW Address:        xx:xx:xx:xx:xx:xx

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            b44
  State:             unavailable
  Default:           no
  HW Address:        xx:xx:xx:xx:xx:xx

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```When I log into my router, it also tells me that "hostpc" is connected. What can I do?

EDIT: If this has any relevance after those outputs - under Windows the card works flawlessly!

---

### Post by chili555 on 2012-06-27
It still appears that you are perfectly connected. If you can ping and resolve Google, I'm surprised that you can't open Firefox and get their page. Can't you?

I do notice a couple of puzzling things. First, nm-tool usually shows the IP address, gateway and DNS nameservers; it's absent here. Second, your wireless interface is eth0 and wired eth1, the reverse of what's usually found. I've seen this in a few cases, but it usually causes no problems.

Let's have a look at:```
cat /etc/NetworkManager/NetworkManager.conf
cat /etc/network/interfaces
cat /etc/udev/rules.d/70-persistent-net.rules
```> EDIT: If this has any relevance after those outputs - under Windows the card works flawlessly! It's not. A great many things work perfectly in one but not the other. A great many things work perfectly in both. In this case, we see nothing, so far that suggests the card isn't working perfectly here also. Perhaps Network Manager isn't working properly.

About all that 'under Windows the card works flawlessly' means is that it isn't electrically defective, but we know that:> $ ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (173.194.69.105) 56(84) bytes of data.
64 bytes from [www.l.google.com](www.l.google.com) (173.194.69.105): icmp_req=1 ttl=47 time=27.4 ms

---

