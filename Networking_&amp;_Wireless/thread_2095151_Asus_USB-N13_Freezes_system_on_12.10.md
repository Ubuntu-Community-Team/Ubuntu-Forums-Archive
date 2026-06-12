---
title: "Asus USB-N13 Freezes system on 12.10"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by larrylc on 2012-12-16
Hi! I recently bought the Asus USB-N13 [ralink 3072] because I read online that it does support linux.

When I got the USB plugged it in my Ubuntu 12.10. The system automatically recognizes it and I was able to connect to my 802.1 G WPA 2 network with no problem.

But I noticed really slow speed in the network. And what I realized after testing its speed is that:

1. The dongle gives me full speed after plugging it in. But after about 5 minutes. The speed drops to only half of the full speed.
2. Every time I unplug and plug the dongle back in, it always give me full speed in the beginning, and then slows down afterwards.

So then I googled about the speed problem with this dongle and apparently found a lot of others having the speed problem like me. 
So following this post [http://ubuntuforums.org/showthread.php?t=1986354](http://ubuntuforums.org/showthread.php?t=1986354)
I downloaded the latest driver from Ralink's website. [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)  and downloaded the exact same file that other link showed me.

I also followed the instruction of the 3rd reply on the OP. After restarting, the system detects the network just fine and connected just fine. I also see a big increase in signal compare to the old driver, but after about 5-6 seconds, the system freezes and becomes unresponsive. I cannot even ctrl+alt+f1 or REISUB. The only way was to force power off and turn the PC back on.

I tried this 3 times over and over again and the system alwasy lock up after 5-6 seconds. 

The system only lock up AFTER I am connected to a network. If there is no network for it to connect to, the system doesnt hang even when the dongle is plugged in.

I had to use my HTC Sensation XL phone to tether to the computer to get Internet. Interestingly, I realized that while I am connected to the HTC AND connecting to a wireless network, the system doesn't lock up.

So I only guess is that the system only locks up once it is using the internet from the N13 dongle.

This is my lsusb:

```
Bus 002 Device 003: ID 0bb4:0ffe HTC (High Tech Computer Corp.) Desire HD (modem mode)
Bus 002 Device 004: ID 0b05:1784 ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. A1) [Ralink RT3072]
Bus 003 Device 002: ID 0461:4d64 Primax Electronics, Ltd 
Bus 003 Device 003: ID 047b:0011 Silitek Corp. SK-1688U Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```uname -r

```
3.5.0-19-generic
``````
lsmod | grep rt2870sta
``` returns nothing

iwconfig

```
usb0      no wireless extensions.

ra0       Ralink STA  ESSID:"DmitriLC"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: B8:E6:25:BA:21:F9   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=97/100  Signal level:-68 dBm  Noise level:-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lo        no wireless extensions.
```ifconfig


```
eth0      Link encap:Ethernet  HWaddr 00:30:67:cb:90:c1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2417 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:262222 (262.2 KB)  TX bytes:262222 (262.2 KB)

ra0       Link encap:Ethernet  HWaddr f4:6d:04:b1:64:2e  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:feb1:642e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4799074 (4.7 MB)  TX bytes:850354 (850.3 KB)

usb0      Link encap:Ethernet  HWaddr 6e:08:8a:86:36:2d  
          inet addr:192.168.42.123  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::6c08:8aff:fe86:362d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:48833 errors:2 dropped:0 overruns:0 frame:2
          TX packets:32902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63767840 (63.7 MB)  TX bytes:5038089 (5.0 MB)
``` modinfo rt5370sta

```

filename:       /lib/modules/3.5.0-19-generic/kernel/drivers/net/wireless/rt5370sta.ko
version:        2.5.0.3
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     B5F68EDB8F10C7E19E04080
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       3.5.0-19-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)
```lsmod | grep rt5370

```
rt5370sta             805498  1 
```None of the commands I used with rt2870 returns anything, but I recognized that in etc/wireless there is a folder called RT2870STA

I have added the following to etc/wireless/blacklist.conf

```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
blacklist 8192cu
blacklist rtl8192cu
```I think I am just so close to make this dongle work properly. Any help would be appreciated. Thank you.

---

### Post by QuantumKnot on 2013-01-05
Hello, are you by any chance running on x86_64?  Since I've noticed the ralink drivers only work on 32 bit systems, not 64 bit.

---

### Post by tahdas on 2013-01-06
Hi i have a 32bit 12.10 system. Im looking for a usb wifi adapter for Ubuntu and wondering if this one would work?

Thanks,
tahdas

---

