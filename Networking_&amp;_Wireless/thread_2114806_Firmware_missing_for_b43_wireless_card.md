---
title: "Firmware missing for b43 wireless card"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by bwallum on 2013-02-11
Hi

I have upgraded a pc to 12.04 i386 and found that the wireless card does not work anymore. Reports suggest that the firmware is missing. The following info has been cleaned:-

Motherboard N61PB-M2S
Ubuntu 12.04.2 i386

```
uname -r
```3.2.0-37-generic-pae

```
sudo iwconfig
```lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.

```
sudo lspci -v
```01:08.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
    Subsystem: Broadcom Corporation Device 0453
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at fd7fe000 (32-bit, non-prefetchable) [size=8K]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb

```
sudo lshw -c network
```*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:03:c9:53:e7:57
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-37-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

How do I make the firmware available/enable the interface please?

---

### Post by kc1di on 2013-02-11
Hi bwallum,

follow the procedure on [this page]("http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working").  and you should get it working again.

---

### Post by bwallum on 2013-02-11
Thanks kc1di, very quick response.

I found this advice worked, simply run
```
sudo apt-get install firmware-b43-installer
```I needed an alternative ethernet connection to do the job as files have to be downloaded. The above command does all this automatically and connects with no further manual intervention.

This link got me to the above solution:-
[http://www.linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy](http://www.linuxwireless.org/en/users/Drivers/b43#b43_and_b43legacy)

Many thanks again
Bob

---

### Post by kc1di on 2013-02-11
Glad you got it going - have fun :)

---

