---
title: "New to Ubuntu no internet"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by jcdavies on 2009-09-29
So i just set up Ubuntu for the first time never used any type on linux os before. was hopeing that as in windows it would show me a selection of the wireless networks and i could choose the one i want, but have been unable to find anything. how do i set up a wireless connection on ubuntu?

Sorry if i dont understand everything

---

### Post by castlefox on 2009-09-29
If you look on the top right of the top tool bar there should be an icon you can click on to see what wireless SSIDs you want to connect to.

---

### Post by mikehenson on 2009-09-29
in terminal type:
```
lspci
```
This will give you the hardware you have.
Search the net for the wireless card you have. If you have a broadcom try bcm43 or b43 drivers.

MSH

---

### Post by jcdavies on 2009-09-29
> **mikehenson said:**
> in terminal type:
```
lspci
```This will give you the hardware you have.
Search the net for the wireless card you have. If you have a broadcom try bcm43 or b43 drivers.

MSH

wow alot of stuff came up then what would it be listed under on that list, Ethernet controller or network controller dont see anythign labeld wirless this is teh system i have 

[http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=1&product=9446&part=9668#spectop](http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=1&product=9446&part=9668#spectop)

---

### Post by t0mppa on 2009-09-29
Or you could just run **lshw -C network** on terminal and post the results here, as it will show what chipset you have, what drivers they're using and the state of the interface.

---

### Post by bkratz on 2009-09-29
> **jcdavies said:**
> wow alot of stuff came up then what would it be listed under on that list, Ethernet controller or network controller dont see anythign labeld wirless this is teh system i have 

[http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=1&product=9446&part=9668#spectop](http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=1&product=9446&part=9668#spectop)



The link you provided says it is a realtek type, but not which one, that is why the previous posters wanted to see lspci, so they can help.

---

### Post by jcdavies on 2009-09-29
> **t0mppa said:**
> Or you could just run **lshw -C network** on terminal and post the results here, as it will show what chipset you have, what drivers they're using and the state of the interface.


hope this helps

   jcdavies@jcdavies-PC:~$ lshw -C network
  WARNING: you should run this program as super-user.
    *-network               
         description: Ethernet interface
         product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:0e:00.0
         logical name: eth0
         version: 02
         serial: 00:26:22:2e:f3:16
         width: 64 bits
         clock: 33MHz
         capabilities: bus_master cap_list ethernet physical
         configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
    *-network UNCLAIMED
         description: Network controller
         product: Realtek Semiconductor Co., Ltd.
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:14:00.0
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master cap_list
         configuration: latency=0
    *-network DISABLED
         description: Ethernet interface
         physical id: 2
         logical name: pan0
         serial: aa:f1:e5:d4:18:ba
         capabilities: ethernet physical
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by jcdavies on 2009-09-29
> **mikehenson said:**
> in terminal type:
```
lspci
```This will give you the hardware you have.
Search the net for the wireless card you have. If you have a broadcom try bcm43 or b43 drivers.

MSH


and here is that as well hope this helps 

   jcdavies@jcdavies-PC:~$ lspci
  00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
  00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
  00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
  00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
  00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
  00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
  00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
  00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
  00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
  00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
  00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
  00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
  00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
  00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
  00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
  00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
  00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
  00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
  00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
  0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
  14:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)

---

### Post by t0mppa on 2009-09-29
> **jcdavies said:**
> 
    *-network UNCLAIMED
         description: Network controller
         product: Realtek Semiconductor Co., Ltd.
         vendor: Realtek Semiconductor Co., Ltd.
         physical id: 0
         bus info: pci@0000:14:00.0
         version: 01
         width: 32 bits
         clock: 33MHz
         capabilities: bus_master cap_list
         configuration: latency=0


Ok, there we go. Your wireless interface (Realtek 8192) isn't getting associated with any drivers and thus it doesn't work. And it looks like it is so new that there are no stable Linux drivers for it yet. Check [this post]("http://ubuntuforums.org/showpost.php?p=7808142&postcount=11") for instructions on how to install Windows drivers for it through NDISWrapper.

---

