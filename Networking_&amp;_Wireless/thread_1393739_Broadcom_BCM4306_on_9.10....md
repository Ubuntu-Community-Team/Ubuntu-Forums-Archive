---
title: "Broadcom BCM4306 on 9.10..."
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by Wintermut3 on 2010-01-29
Well, my second post here and I guess it's my first real glitch. There seem to be a lot of threads on various Broadcom controllers  - so far nothing suggested has worked, hence I'm starting one of my own.

Just installed 9.10 on a dual-boot compaq nx9105 that already had WinXP on it. This is my first time with Linux at home.

lspci tells me I have the following:
> 02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)iwconfig outputs:
> lo        no wireless extensions.
eth0      no wireless extensions.I followed the instructions here:
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)
which led me, via Synaptic, though doing a complete package update and installing bcmwl-kernel-source.

I then followed the instructions here:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
which led me through... I think... installing the STA drivers? Those were rather hard to follow though, and I'm not certain I got it right, I'm not sure how to check.

I then ran through these instructions in the "Definitive 9.10 Broadcom Solution Guide":
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
which installed b43-fwcutter

I finally installed WICD network manager (via Sytaptic), which tells me "No wireless networks found".

Each of the above was followed by a reboot. At all points, checking System -> Hardware Drivers showed no trace of any Wireless driver. Repeated pressing of the little wireless button on the front of the laptop has never resulted in the Little Blue Light of Internet Goodness.

The ethernet adapter's working fine, although I'd rather not be trailing a lump of CAT5 across the lounge.

The only other option I'm aware of at the moment seems to be something about using the Windows drivers? That looked a bit daunting so I'm asking if anyone knows of any other possibilities, or a simple walkthrough for this.

Thanks :)

---

### Post by Wintermut3 on 2010-01-30
Ok, an update. I removed the bcmwl-kernel-source, and I seem to have a driver. Under "Hardware Drivers", I now have the Broadcom B43 driver, and it's active.

However, that's as much as it's done. My wireless light is still off, Wicd still tells me no wireless networks have been found.

I'm stuck. I'm despondent. Anyone have any suggestions? :(

---

### Post by bkratz on 2010-01-30
Can you go to the terminal  (Applications>>Accessories>>Terminal) and copy paste the results of the following back here

sudo lshw -C network

(that is LSHW in lowercase)



Might as well do iwconfig also

---

### Post by bkratz on 2010-01-30
Here is a thread that may help you--the first few pages are kinda worthless but the posts afterwards should help.

[http://ubuntuforums.org/showthread.php?t=1339364](http://ubuntuforums.org/showthread.php?t=1339364)

---

### Post by Wintermut3 on 2010-01-31
Thanks - output from lshw is:
>  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:72:0a:39
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.66 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:18 ioport:7000(size=256) memory:e0108800-e01088ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e0104000-e0105fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:ec:69:4e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
and iwconfig produces:
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
which is certainly encouraging, if a little confusing. I'll have a read of the other thread and update this one if I have any luck. Thanks for your help :)

---

### Post by Wintermut3 on 2010-01-31
That doesn't seem to have done anything I'm afraid; I've got b43-fwcutter installed, I had a moment of hope when I read that having the ethernet connected auto-disables the wireless, but it doesn't seem to have any effect for me. Cable or no cable, Wicd tells me no wireless networks found.

Following the guide here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
I've got the following output from lsmod | grep b43:
> b43                   122168  0 
mac80211              181140  1 b43
cfg80211               93052  2 b43,mac80211
led_class               4096  1 b43
ssb                    35364  1 b43and the following from ifconfig:

> eth0      Link encap:Ethernet  HWaddr 00:0f:b0:72:0a:39  
          inet addr:192.168.1.66  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe72:a39/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2344945 (2.3 MB)  TX bytes:200378 (200.3 KB)
          Interrupt:18 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)


---

### Post by Wintermut3 on 2010-01-31
I don't know if this means anything to anyone... following advice on another thread I tried this:

> dmesg | grep -e b43and got this:

> [    2.418670] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   25.823135] b43-phy0: Broadcom 4306 WLAN found (core revision 5)The only odd thing I noticed is that it's saying rev 5 when the identifier string returned by lspci says rev 3? :confused:

---

