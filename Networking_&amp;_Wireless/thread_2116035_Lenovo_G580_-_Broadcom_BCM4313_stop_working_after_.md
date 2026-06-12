---
title: "Lenovo G580 - Broadcom BCM4313 stop working after kernel upgrade"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by sushi80 on 2013-02-14
My wifi suddenly stop to work

I have a new Lenovo G580 with Broadcom 4313
Last week i've installed 12.10, update the os using wifi (i don't use lan) and no problem (maybe had some intermittent problems but i was able to stream and download)
On Tuesday 12th Feb I've received some update (i think there was the kernel) and my wifi was gone!
Was keep trying to connect but failing every time. i got connected just few times to my AP but i wasn't able to browse internet

I end up re-installing and is all good(using kernel 3.5.0.17), then after the upgrade to kernel 3.5.0.23 i'm stuck without wifi and lan!!

i collect some info from kernel3.5.0.17 and kernel3.5.0.23

```
lsmod | egrep -i 'b43|ssb|wl|brcm|bcma'
wl                   2573568  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
```


 ```
lspci -vvnn |grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0587]
```

```
Linux lenovo-ux 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```

```
dpkg -l |grep headers
ii  linux-headers-3.5.0-17                    3.5.0-17.28                               all          Header files related to Linux kernel version 3.5.0
```


 ```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr XXXXXXXXXXXX  
          inet addr:192.168.X.XXX  Bcast:192.168.xxxxx  Mask:xxxxxxx
          inet6 addr: fe80::c214:3dff:fec7:8835/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39208 errors:0 dropped:0 overruns:0 frame:24022
          TX packets:26252 errors:11 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52614064 (52.6 MB)  TX bytes:2169638 (2.1 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:64809 (64.8 KB)  TX bytes:64809 (64.8 KB)
```

 ```
iwconfig
eth0      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:233  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lo        no wireless extensions.
```



```
ping www.google.com
PING www.google.com (74.125.24.105) 56(84) bytes of data.
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=1 ttl=44 time=318 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=2 ttl=44 time=327 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=3 ttl=44 time=319 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=4 ttl=44 time=170 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=5 ttl=44 time=333 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=6 ttl=44 time=197 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=7 ttl=44 time=220 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=8 ttl=44 time=138 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=9 ttl=44 time=162 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=10 ttl=44 time=184 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=11 ttl=44 time=208 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=12 ttl=44 time=230 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=13 ttl=44 time=254 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=14 ttl=44 time=175 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=15 ttl=44 time=302 ms
64 bytes from de-in-f105.1e100.net (74.125.24.105): icmp_req=16 ttl=44 time=223 ms
^C
--- www.google.com ping statistics ---
17 packets transmitted, 16 received, 5% packet loss, time 20538ms
rtt min/avg/max/mdev = 138.127/235.439/333.307/63.438 ms
```


 ```
dmesg|grep wl
[   13.001970] wl: module license 'MIXED/Proprietary' taints kernel.
[ 1348.825150] wlc_print_ampdu_txstatus: txstatus 0xf1e3
[ 1348.826373] wlc_print_ampdu_txstatus: txstatus 0xf0e3
[ 1348.826386] wlc_print_ampdu_txstatus: txstatus 0xf0e3
[ 1348.826396] wlc_print_ampdu_txstatus: txstatus 0xf0e3
[ 1348.826405] wlc_print_ampdu_txstatus: txstatus 0xf0e3
```



and this after the update:


```
lsmod | egrep -i 'b43|ssb|wl|brcm|bcma'

result is empty!!

```

```
uname -a
Linux lenovo-ux 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

```
 dpkg -l |grep headers
ii  linux-headers-3.5.0-17                    3.5.0-17.28                               all          Header files related to Linux kernel version 3.5.0
iU  linux-headers-generic                     3.5.0.23.29                               amd64        Generic Linux kernel headers
```

 ```
ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6432 (6.4 KB)  TX bytes:6432 (6.4 KB)

```

I've tried to reinstall bcmwl-kernel-source but i get an error

```
(Reading database ... 146602 files and directories currently installed.)
Preparing to replace bcmwl-kernel-source 5.100.82.112+bdcom-0ubuntu3 (using bcmwl-kernel-source_5.100.82.112+bdcom-0ubuntu3_amd64_1.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement bcmwl-kernel-source ...
Setting up bcmwl-kernel-source (5.100.82.112+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.112+bdcom DKMS files...
Building only for 3.5.0-23-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
ERROR: Module b43 does not exist in /proc/modules
ERROR: Module b43legacy does not exist in /proc/modules
ERROR: Module ssb does not exist in /proc/modules
ERROR: Module bcm43xx does not exist in /proc/modules
ERROR: Module brcm80211 does not exist in /proc/modules
ERROR: Module brcmfmac does not exist in /proc/modules
ERROR: Module brcmsmac does not exist in /proc/modules
ERROR: Module bcma does not exist in /proc/modules
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-23-generic
```



I tried different guide but i can't find a solution!!
i'm thinking to reinstall end not update the kernel....

---

### Post by offgridguy on 2013-02-14
There might be something here that helps.

[http://askubuntu.com/questions/12355/how-do-i-get-my-broadcom-bcm4313-working-correctly](http://askubuntu.com/questions/12355/how-do-i-get-my-broadcom-bcm4313-working-correctly)

---

### Post by 23senick on 2013-02-14
I had similar issue (though on 12.04 not 12.10) and the issue was a new version of the proprietary driver for Broadcom 4313.  There are a number of solutions on this post

[http://ubuntuforums.org/showthread.php?t=2111403]("http://ubuntuforums.org/showthread.php?t=2111403")

The final one worked for me (pages 2 and 3) but read it right through as there were people with 12.10 and there may be an easier solution for you.

---

### Post by sushi80 on 2013-02-15
I've update my kernel to version 3.7.0 as pointed in this tread

[http://ubuntuforums.org/showthread.php?t=2090138&page=2](http://ubuntuforums.org/showthread.php?t=2090138&page=2) #13

and now wifi is working again.....I'm not sure if is a right solution, i don't like the idea to break wifi again next update!

With this kernel i'm also getting some errors during boot process...

---

### Post by sushi80 on 2013-02-23
Here we go again......new update (this time not even the kernel) and wifi broken! ....actually I can connect this time but extremely slow!

any suggestion??

---

### Post by sushi80 on 2013-03-01
few updates...

thanks to [COLOR=#000000]praseodym[/COLOR] instruction ([http://ubuntuforums.org/showthread.php?t=2111181](http://ubuntuforums.org/showthread.php?t=2111181) #4)  i'm now able to connect to lan but i still have problem with my wlan!!!

i can see my hotspot but i can't connect and  the signal is very poor!
 
here few details 

```
 lspci -nn |grep -iA2 net02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
ivan@ivan-Lenovo-G580:~$ lspci -nnk |grep -iA2 net
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0587]
	Kernel driver in use: bcma-pci-bridge



lsmod | egrep -i 'b43|ssb|wl|brcm|bcma'
brcmsmac              531905  0 
mac80211              540032  1 brcmsmac
brcmutil               14756  1 brcmsmac
cfg80211              206797  2 brcmsmac,mac80211
cordic                 12575  1 brcmsmac
bcma                   35657  1 brcmsmac


dpkg -l |grep headers
ii  linux-headers-3.5.0-17                          3.5.0-17.28                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-25                          3.5.0-25.39                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-25-generic                  3.5.0-25.39                               amd64        Linux kernel headers for version 3.5.0 on 64 bit x86 SMP
ii  linux-headers-generic  





```

---

### Post by tenmoi on 2013-03-24
Sushi. According to this website [http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices), your card model is not supported.

---

### Post by bishop__ on 2013-10-29
I also experienced this problem in my Lenovo G480. I have Ubuntu 12.04 and upgraded the kernel from 3.2.x to 3.5.x then suddenly my lan and wifi stop working. Was able to solve the problem thru [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php). You can follow the steps in README.txt. 

But I still reverted my kernel back to 3.2.x since my VirtualBox also stopped working in 3.5.x and I never updated my kernel again. I keep looking for solutions yet on how to have a stable fix for my virtualbox before i'll upgrade my kernel.

---

