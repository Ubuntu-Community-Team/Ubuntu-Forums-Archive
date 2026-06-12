---
title: "Unable to get Wireless on a Toshiba L350 with Realtek Semiconductor Co., Ltd. RTL8101"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by divingdon on 2011-05-24
Fed up with Vista so changed to Maverick Meerkat.  Whilst in Meerkat I found a few fixes which I tried to use, to no sucess.  updating drivers, turning router on/off, turning wireless switch on/off, various other fixes from ubuntuforums.  tried to upgrade to Natty Narwhale to see if the problem worked it's way out, to no avail.  I've spent two days trying for this. Anyone out there willing to point me in the right direction or hold my hand?

---

### Post by chili555 on 2011-05-24
I apologize in advance. I just can't help myself! I have no doubt you can't get any wireless on a Realtek 8101 because that's a wired ethernet device!

OK, fun's over. Please run and post:```
lspci -nn
rfkill list all
```I promise to roll up my sleeves and get serious.

---

### Post by smurphy_it on 2011-05-24
Any reason why you just didn't grab the most up-to-date version of ubuntu and install that ?  I ask as sometimes the upgrade path can break things, which will only add to your problems.

Best thing to do after installing ubuntu, is see what works and doesn't work, and go from there... one at a time.

One thing which would be very helpful once you have the system running, is the type of hardware and software.

Example:

acer x3450 with 2GB RAM, running Intel Xeon.  Installed ubuntu 11.04 32bit.  Ubuntu installed onto hard-drive (not using wubi).

Once all is setup and running, the fine folks here can walk you through the devices / setup of things which aren't working.

---

### Post by divingdon on 2011-05-24
I reckon I need to show that I'm helping myself for others to help me so everytime I try a fix from the forum, I'll list it here.

> **Plumtreed said:**
> ...have you gone to " System>Additional  Drivers" to see if you need to download a driver to support your  laptop?

Nothing comes up to be installed

---

### Post by divingdon on 2011-05-24
@ Chilli glad to give you a giggle :O)

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Any of this help????


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


sudo lshw -C network
[sudo] password for don: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:3c:ac:01
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.85 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:3000(size=256) memory:90010000-90010fff memory:90000000-9000ffff
  *-network
       description: Wireless interface
       physical id: 1
       bus info: usb@2:6
       logical name: wlan0
       serial: 00:16:44:c9:c7:fa
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.35-22-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

---

### Post by chili555 on 2011-05-24
It appears you have a USB wireless device.> *-network
description: Wireless interface
physical id: 1
bus info: [COLOR="Red"]usb[/COLOR]@2:6
logical name: wlan0
serial: 00:16:44:c9:c7:fa
capabilities: ethernet physical wireless
configuration: broadcast=yes [COLOR="Red"]driver=rtl8187[/COLOR] driverversion=2.6.35-22-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg It uses the always tricky rtl8187.

Do you see networks when you detach the ethernet cable and click the Network Manager icon? Does it try to connect? Any useful information here?```
dmesg | grep -e 8187 -e wlan
```

---

### Post by divingdon on 2011-05-25
When I click on the wireless icon it seems to think about connecting then in the end decides that it would rather not connect.  Is that what the deauthenticating by local choice is in the following script?  

dmesg | grep -e 8187 -e wlan
[   12.506463] phy0: hwaddr 00:16:44:c9:c7:fa, RTL8187BvE V0 + rtl8225z2, rfkill mask 4
[   12.539267] rtl8187: Customer ID is 0x04
[   12.539344] Registered led device: rtl8187-phy0::radio
[   12.539369] Registered led device: rtl8187-phy0::tx
[   12.539393] Registered led device: rtl8187-phy0::rx
[   12.540890] rtl8187: wireless switch is on
[   12.540942] usbcore: registered new interface driver rtl8187
[   16.757491] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.029358] wlan0: authenticate with 00:8b:5d:81:83:1a (try 1)
[   41.032597] wlan0: authenticated
[   41.032622] wlan0: associate with 00:8b:5d:81:83:1a (try 1)
[   41.035606] wlan0: RX AssocResp from 00:8b:5d:81:83:1a (capab=0x431 status=0 aid=2)
[   41.035610] wlan0: associated
[   41.110617] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   51.712044] wlan0: no IPv6 routers present
[   88.389117] wlan0: deauthenticating from 00:8b:5d:81:83:1a by local choice (reason=3)

---

### Post by divingdon on 2011-05-25
Now knowing what the issue is, it looks like this is the solution.  [http://ubuntuforums.org/showthread.php?t=1763023&highlight=rtl8187](http://ubuntuforums.org/showthread.php?t=1763023&highlight=rtl8187)  Sounds a bit over my level of compentence...  Back to the wonderful world of windows it is for me :O(

---

