---
title: "Wireless Driver not working with Acer Aspire 5560 Broadcom STA Ubuntu 12.04"
date: 2012-07-19
forum: Networking &amp; Wireless
---

### Post by earthsmurf on 2012-07-19
Hello Ubuntu Forums,

I just bought an Acer Aspire 5560.  I installed Ubuntu from scratch on clean SSD from Ubuntu 12.04 64 bit Live CD.  The wireless worked (before installing updates) until I installed the Broadcom STA driver from Additonal Drivers in System Settings.  Looking back on it, I'm not sure why I installed the driver if it was already working.  Anyways, it said my Broadcom STA driver is activated but it wouldn't detect any wireless networks.  So I tried many different things to try and fix this, and since I'm new to Ubuntu/linux I think I'm tangled.  Where I've left off is, I installed the Broadcom hybrid 64bit driver from Broadcom website manually after I deactivated the Broadcom STA proprietary driver.
Looks like I still have 2 drivers installed though..

Here's the output to some helpful commands:

```
 lspci -nn  
``````

00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h Processor Root Complex [1022:1705]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:9647]
00:01.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series] [1002:1714]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 12h Processor Root Port [1022:1709]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] Family 12h Processor Root Port [1022:170b]
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode] [1022:7804]
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] Hudson SMBus Controller [1022:780b] (rev 13)
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] Hudson Azalia Controller [1022:780d] (rev 01)
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] Hudson LPC Bridge [1022:780e] (rev 11)
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] Hudson PCI Bridge [1022:780f] (rev 40)
00:16.0 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB OHCI Controller [1022:7807] (rev 11)
00:16.2 USB controller [0c03]: Advanced Micro Devices [AMD] Hudson USB EHCI Controller [1022:7808] (rev 11)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 [1022:1700] (rev 43)
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 [1022:1701]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 [1022:1702]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 [1022:1703]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 [1022:1704]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 [1022:1718]
00:18.6 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 [1022:1716]
00:18.7 Host bridge [0600]: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 [1022:1719]
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
01:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
01:00.2 System peripheral [0880]: Broadcom Corporation Device [14e4:16be] (rev 10)
01:00.3 System peripheral [0880]: Broadcom Corporation Device [14e4:16bf] (rev 10)
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]

``````
  rfkill list all  
``````

0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

``````

sudo lshw -C network

``````

  *-network
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 20:6a:8a:7f:5f:d9
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom  ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd  autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3  driverversion=3.121 firmware=sb latency=0 link=no multicast=yes  port=twisted pair
       resources: irq:16 memory:f0000000-f000ffff memory:f0010000-f001ffff memory:f0050000-f00507ff
  *-network
       description: Wireless interface
       product: BCM43227 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth2
       version: 00
       serial: c0:18:85:81:9d:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f0100000-f0103fff

```

Thanks for looking!

---

### Post by mikewhatever on 2012-07-19
Wouldn't be quicker and easier to reinstall?

Anyway, if you want to troubleshoot it, add the outputs of the following:

dpkg -l | grep bcmwl-kernel-source

lsmod | grep -e brcm -e b43 -e ssb

Can you also post a link to the driver you've installed from Broadcom's site.

---

### Post by earthsmurf on 2012-07-19
Let's shoot trouble

> 
dpkg -l | grep bcmwl-kernel-source
```

rc  bcmwl-kernel-source                    
5.100.82.38+bdcom-0ubuntu6.1            
Broadcom 802.11 Linux STA wireless driver source

```> 
lsmod | grep -e brcm -e b43 -e ssb
Returned blank

The website where I got the Broadcom Driver is here:
[http://www.broadcom.com/support/802.11/linux_sta.php/](http://www.broadcom.com/support/802.11/linux_sta.php/)

---

### Post by mikewhatever on 2012-07-19
Looks like you still have the STA driver installed. Make sure it's deactivated, or remove it with
"sudo apt-get purge bcmwl-kernel-source".

Reboot after that, and hopefully, some other module will get loaded.

---

### Post by chili555 on 2012-07-19
With all due respect to my esteemed colleague mikewhatever, wl, provided by bcmwl-kernel-source, is correct for this device and should *NOT* be removed.> Broadcom Corporation BCM43227 802.11b/g/n [[COLOR="Red"]14e4:4358[/COLOR]]I'd be interested in what the message logs say about this:```
dmesg | grep -e wl -e eth
```

---

### Post by earthsmurf on 2012-07-19
After removing  bcmwl-kernel-source I ran:

> 
dmesg | grep -e wl -e ethSorry I didn't see the latest post by chili until after I removed it... but here is the output.

```


[    0.560205] i2c-core: driver [aat2870] using legacy suspend method
[    0.560208] i2c-core: driver [aat2870] using legacy resume method
[    1.596437] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_.ADP1._PSR] (Node ffff880118647b90), AE_ALREADY_EXISTS (20110623/psparse-536)
[    1.628437] ACPI: Marking method _PSR as Serialized because of AE_ALREADY_EXISTS error
[    1.695057] tg3 0000:01:00.0: eth0: Tigon3 [partno(BCM57785) rev 57785100] (PCI Express) MAC address 20:6a:8a:7f:5f:d9
[    1.695062] tg3 0000:01:00.0: eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    1.695065] tg3 0000:01:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.695068] tg3 0000:01:00.0: eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    7.156898] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.616124] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.617324] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.156639] tg3 0000:01:00.0: eth0: Link is up at 1000 Mbps, full duplex
[   12.156645] tg3 0000:01:00.0: eth0: Flow control is on for TX and on for RX
[   12.156648] tg3 0000:01:00.0: eth0: EEE is enabled
[   12.157392] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.944085] eth0: no IPv6 routers present
[   51.143370] tg3 0000:01:00.0: eth0: Link is down
[   55.210566] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  783.990239] tg3 0000:01:00.0: eth0: Link is up at 1000 Mbps, full duplex
[  783.990250] tg3 0000:01:00.0: eth0: Flow control is on for TX and on for RX
[  783.990256] tg3 0000:01:00.0: eth0: EEE is enabled
[  783.991388] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  794.064159] eth0: no IPv6 routers present


```

---

### Post by chili555 on 2012-07-19
I expect you'd better reinstall it:```
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
dmesg | grep -e wl -e eth
```

---

### Post by earthsmurf on 2012-07-19
Here's output after reinstall:

```

[    0.560205] i2c-core: driver [aat2870] using legacy suspend method
[    0.560208] i2c-core: driver [aat2870] using legacy resume method
[    1.596437] ACPI Error: Method parse/execution failed [\_SB_.PCI0.LPC0.EC0_.ADP1._PSR] (Node ffff880118647b90), AE_ALREADY_EXISTS (20110623/psparse-536)
[    1.628437] ACPI: Marking method _PSR as Serialized because of AE_ALREADY_EXISTS error
[    1.695057] tg3 0000:01:00.0: eth0: Tigon3 [partno(BCM57785) rev 57785100] (PCI Express) MAC address 20:6a:8a:7f:5f:d9
[    1.695062] tg3 0000:01:00.0: eth0: attached PHY is 57765 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    1.695065] tg3 0000:01:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.695068] tg3 0000:01:00.0: eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    7.156898] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.616124] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.617324] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.156639] tg3 0000:01:00.0: eth0: Link is up at 1000 Mbps, full duplex
[   12.156645] tg3 0000:01:00.0: eth0: Flow control is on for TX and on for RX
[   12.156648] tg3 0000:01:00.0: eth0: EEE is enabled
[   12.157392] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   22.944085] eth0: no IPv6 routers present
[   51.143370] tg3 0000:01:00.0: eth0: Link is down
[   55.210566] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  783.990239] tg3 0000:01:00.0: eth0: Link is up at 1000 Mbps, full duplex
[  783.990250] tg3 0000:01:00.0: eth0: Flow control is on for TX and on for RX
[  783.990256] tg3 0000:01:00.0: eth0: EEE is enabled
[  783.991388] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  794.064159] eth0: no IPv6 routers present
[ 2964.989243] wl 0000:02:00.0: PCI->APIC IRQ transform: INT A -> IRQ 19
[ 2964.989251] wl 0000:02:00.0: setting latency timer to 64
[ 2965.061447] eth2: Broadcom BCM4358 802.11 Hybrid Wireless Controller 5.100.82.38
[ 2965.081343] udevd[604]: renamed network interface eth1 to eth2

```

I rebooted, but it's still not picking up any wireless networks.

---

### Post by chili555 on 2012-07-20
> udevd[604]: renamed network interface eth1 to eth2Your readings look pretty solid, actually. I'm not sure the udev rename is significant, but let's see what else we can see:```
sudo iwlist eth2 scan
iwconfig eth2
rfkill list all
```Please make these readings with the ethernet cable detached. Any errors, warnings, etc. are significant; please post them. Thanks.

---

### Post by earthsmurf on 2012-07-20
There were no results for the first command...

> 
iwconfig eth2
```

eth2      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```> 
rfkill list all
```

0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```When I click on the wireless at the top I can see Wireless Networks but it's grayed out.  It's not picking up any networks.  I even tried to manually add my wireless network, but it prompts for password, I type it in, and then it tries to connect and prompts for password again (i know my password is correct for sure).

Also, why does it say eth2 is BCM4358, but when I do lspci -nn it says Network Controller is BCM43227...

---

### Post by earthsmurf on 2012-07-22
Any thoughts anyone?

---

### Post by earthsmurf on 2012-07-23
Posting to keep this alive...

---

### Post by earthsmurf on 2012-07-24
If you look at the results from "lspci -nn" and the results of "dmesg | grep -e wl -e eth" you'll notice that lspci says that the network card is a BCM43227 but when i run dmesg is says eth2 is a BCM4358????  Why is that???  Shouldn't it say BCM43227??!!

---

### Post by earthsmurf on 2012-07-24
Hmm, very strange, I was able to solve my problem by accident.  All I did was do

```
 sudo update-grub
```

and when I restarted my computer my wifi was working.  I have idea how this is tied to wifi driver installation but it fixed it.

---

### Post by volscian on 2013-04-04
> **mikewhatever said:**
> Looks like you still have the STA driver installed. Make sure it's deactivated, or remove it with
"sudo apt-get purge bcmwl-kernel-source".

Reboot after that, and hopefully, some other module will get loaded.

> **chili555 said:**
> With all due respect to my esteemed colleague  mikewhatever, wl, provided by bcmwl-kernel-source, is correct for this  device and should *NOT* be removed.I'd be interested in what the message logs say about this:```
dmesg | grep -e wl -e eth
```

I realize at this point that this discussion is dead, however I just installed Ubuntu a couple days ago, updated my stuff, and the driver for my wireless was one of them. As it seems common, that broke it. Not only was that not working, but my Ethernet connection would not actually connect, leaving me with basically a fresh install, no programs, and no internet. I tried the route mikewhatever had suggested, seeing as how most other options I found required internet, and I figured if it broke it worse, I would reinstall the whole OS again. Ran the line in terminal, rebooted, and bam! Wireless internet! Just wanted to throw that out there that an odd selection of people may actually be able to get away with this fix, for now all of my headaches are gone...well, until I actualy start using everything I want to on here that is...

---

