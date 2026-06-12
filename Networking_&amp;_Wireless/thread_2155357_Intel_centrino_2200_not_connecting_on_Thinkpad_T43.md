---
title: "Intel centrino 2200 not connecting on Thinkpad T430s on 12.04"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by japhyr on 2013-06-18
I am setting up a brand new Thinkpad T430s, using 12.04.2 64-bit. Everything is working well except the wireless, an intel centrino 2200. Can anyone point me in the right direction?

$ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)

$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 9c:4e:36:bb:13:54  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9e4e:36ff:febb:1354/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2724990 (2.7 MB)  TX bytes:32500 (32.5 KB)

$ iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Laura2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:23:69:EC:1A:B6   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-19 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:232   Missed beacon:0

$ lsmod
[https://dpaste.de/bbhW0/](https://dpaste.de/bbhW0/)

$ dmesg
[https://dpaste.de/uIpSp/](https://dpaste.de/uIpSp/)

$ lshw -C network
 description: Wireless interface
       product: Centrino Wireless-N 2200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: 9c:4e:36:bb:13:54
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-48-generic firmware=18.168.6.1 ip=192.168.1.113 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:f1c00000-f1c01fff

$ iwlist scan
[https://dpaste.de/Ksvj0/](https://dpaste.de/Ksvj0/)

$ uname -mr
3.2.0-48-generic x86_64

Thank you if you can help!

---

### Post by ahallubuntu on 2013-06-18
~

---

### Post by japhyr on 2013-06-18
I tried those suggestions, and turning off 802.11n worked.

My version is definitely 12.04.2, and the kernel is definitely 3.2:
```
$ cat /etc/issue
Ubuntu 12.04.2 LTS \n \l

$ uname -r
3.2.0-48-generic
```

I downloaded a version of 12.04 specifically for the thinkpad t430s, and I think that release must have had an older kernel version. Rather than messing with a kernel update, I'm going to download the regular 12.04.2 and see how well things work.Thank you for the suggestions!

Update: I installed the regular 12.04.2, which included the 3.5 kernel. I still had to disable 802.11n in order to get the wireless to work.

---

