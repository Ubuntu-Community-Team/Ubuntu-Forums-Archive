---
title: "Decreasing Minimum Wireless Signal to Connect?"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by UbuNoob001 on 2010-07-12
Hi all,
   I am new(ish) to linux. 

My box: Dell Inspiron 1545. lspci results below. I have enabled the Broadcom STA restricted driver. 

Problems: 

1. I am noticing in Ubuntu (using Network Manager and Wicd) that I am unable to connect to wireless signals that are very weak. In my other OS (dual boot), I am able to connect to these weak signals. 

2. And the speed of these networks is much slower, and the disconnect rate is much higher than in my other OS

I am THRILLED with Ubuntu otherwise, just looking to fix this issue so I can use Ubuntu as my primary OS. 

Could this be an Broadcom STA issue, or Software config issue? etc? Obviously not hardware cause hardware is same on other OS. 

```
~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

---

### Post by mikewhatever on 2010-07-12
Perhaps you can adjust wireless power settings. What are the output of the following commands:
```
sudo iwconfig eth1
sudo iwlist eth1 txpower
```

---

### Post by UbuNoob001 on 2010-07-12
> **mikewhatever said:**
> Perhaps you can adjust wireless power settings. What are the output of the following commands:
```
sudo iwconfig eth1
sudo iwlist eth1 txpower
```


mikewhatever, thanks in advance for your help: 

```
~$ sudo iwconfig eth1
[sudo] password for xxxxxxx: 
eth1      IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: xxxxxxx
          Bit Rate=5.5 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:xxxxxxx
          Power Managementmode:All packets received
          Link Quality=1/5  Signal level=-82 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3202  Invalid misc:0   Missed beacon:0

```and 

```
~$ sudo iwlist eth1 txpower
eth1      2 available transmit-powers :
      0 dBm      (1 mW)
      25 dBm      (255 mW)
          Current Tx-Power:24 dBm      (200 mW)

```

---

### Post by mikewhatever on 2010-07-13
Well, as per iwconfig output, the signal strength is very low indeed. Here is the output of mine for comparison.
```
Quality:5/5  Signal level:-44 dBm  Noise level:-92 dBm

```
I think you won't get a reliable connection on that network, unless you relocate the router or get an amplifier.
That said, what I had in mind was increasing the txpower level. In Karmic, the same card, powered by the STA driver, showed txpower level of 32. You could try switching to that level with this command:
```
sudo iwconfig eth1 txpower 32
```

---

### Post by libssd on 2010-07-13
I'm trying to follow what device is being measured in this thread. My environment is an Acer AA1 D150 netbook and an Apple airport.

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     IEEE 802.11bg  ESSID:"Stay Out"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:51:76:37:99   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I'm assuming that wlan0 is the Airport. I'm not really having any problems with access/signal strength anywhere inside my house, and I don't particularly want my signal to be used outside the house (even though access to the AP is restricted). Is there anything here that is configurable?

---

### Post by mikewhatever on 2010-07-13
> **libssd said:**
> I'm trying to follow what device is being measured in this thread. My environment is an Acer AA1 D150 netbook and an Apple airport.

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     IEEE 802.11bg  ESSID:"Stay Out"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:51:76:37:99   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
I'm assuming that wlan0 is the Airport. I'm not really having any problems with access/signal strength anywhere inside my house, and I don't particularly want my signal to be used outside the house (even though access to the AP is restricted). Is there anything here that is configurable?

Wlan0 is the wireless interface (of your computer). The router is what broadcasts your wireless network signal. Some routers allow configuring the signal strength, take a look at its manual.

---

