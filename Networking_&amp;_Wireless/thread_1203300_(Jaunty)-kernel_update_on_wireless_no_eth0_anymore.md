---
title: "(Jaunty)-kernel update on wireless no eth0 anymore"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by mitch_77 on 2009-07-03
hi all,
i live in US and i spent june in my home country (italy) using a wifi connection.
during this month there was a kernel update (from 2.6.28-11 to -13) and when i came back home in US, i realized that i could not connect anymore via eth0.
when i boot into -11 every works fine but into -13 i dont see any coonection.

the card is fine cause i have a dual boot with vista and i can surf via cable....it just doesnt work on ubuntu -13!
how do i reset my connection maybe getting the parameters from the previous kernel?

thanks in advance,
mitch

---

### Post by computer13137 on 2009-07-03
Please paste the output of the "lspci" command for us.  (Just go run it in a terminal).

Also, I've heard of issues where eth0 will randomly be changed to eth1, so make sure that's not what happened after your kernel update.  (Just a thought... I haven't had this problem but I've heard of it.)

-Kirk

---

### Post by superprash2003 on 2009-07-03
you might have to follow the same procedure you followed in the -11 version to get your wifi card working

---

### Post by mitch_77 on 2009-07-03
this is the lspci

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
```

@superprash2003
my wifi card works, although im not using it now cause here i dont have a wifi connection.
i have problem with the ethernet connection.

i tried to re-update booting into -11....i did it but still...no connection.

running ifconfig i dont see either eth0 or eth1

what to do?

thanks,
mitch

---

### Post by superprash2003 on 2009-07-04
post output of **lshw -C network** . also contents of /etc/network/interfaces file

---

### Post by Crinale on 2009-07-04
I have a very similar issue... I had wireless (i have a broadcom 4306 as wlan0) working just fine, then yesterday i installed the update to -13, and after reboot i had no wireless.  The card is still visable to the system, but i cant see any wireless networks in Network Manager, and using "Connect to Hidden Wireless" doesnt work either... Also thinking that the kernel update was the issue, i booted into -11, and it didnt work there either.

iv been stumped so far.

---

### Post by adampope on 2009-07-04
Me too! Wireless and applications working fine, upgraded on Thursday and rebooted, network appears 'connected' but no applications are connecting (ie; Firefox, Skype, synaptic package manager and so on).

---

### Post by mitch_77 on 2009-07-04
> **superprash2003 said:**
> post output of **lshw -C network** . also contents of /etc/network/interfaces file

alright, here they are

lshw -C network
```
*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:19:d2:35:d0:69
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network UNCLAIMED
       description: Ethernet controller
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list
       configuration: latency=0
```

and /etc/network/interfaces says
```
auto lo
iface lo inet loopback
```

mitch

---

### Post by mitch_77 on 2009-07-06
does anybody know what's happening?

mitch

---

### Post by mitch_77 on 2009-07-13
i got it to work :popcorn:

i had forgotten to mention that because of some problem with my NIC, i had to blacklist the driver shipped with the jaunty kernel (r8169) and install r8101.

i did it again using [this script]("http://www.jamesonwilliams.com/r8101-linux") (with many thanks to the author jameson williams) and i got eth0 back.


cheers,
mitch

---

