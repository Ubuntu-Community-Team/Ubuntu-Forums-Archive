---
title: "Compaq Wifi"
date: 2010-03-30
forum: Networking &amp; Wireless
---

### Post by genesisleighton883BC on 2010-03-30
My wifi doesn't seem to be working, in fact it had a wired connection today and it didn't even recognize that!

I switched from Windows 7 to Karmic [9.10]- I had wifi but no sound so I thought if I made a more gradual switch over I'd have both. So I loaded Hardy [8.04]: I had sound but no wireless so I plugged the computer into the internet and ran the update to 8.10 and now I have no internet.

I downloaded Wine and tried to update the drivers from HP.com. Three out of the four registered but I still have no wifi.

The computer seems to run just fine but I have no internet, which under most circumstances would suck but I'm a full time online student. So any help would be much appreciated. 

-Genesis

---

### Post by Iowan on 2010-03-30
What does **sudo lshw -C network** reveal about your interfaces?

---

### Post by genesisleighton883BC on 2010-03-30
Here's the results:


   [I]    *-network UNCLAIMED
               description: Network Controller
               product: Atheros Communications Inc.
               vendor: Atheros Communications Inc.[/I]
  *                physical ID: 0*
  *                bus info: pci@0000 :02.0*
  *                version: 01*
  *                width: 64 bits*
  *                clock: 33MHz*
  *                capabilities: pm msi pciexpress bus_master cap_list*
  *    *-network UNCLAIMED*
  *                description: Ethernet controller*
  *                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller*
  *                vendor: Realtek Semiconductor Co., Ltd.*
  *                physical id: 0*
  *                bus info: pci @0000:03.0*
  *                version: 02 *
  *                width: 64 bits*
  *                clock: 33MHz*
  *                capabilities: pm msi pciexpress msix vpd bus_master cap_list*
  *                configuration: latency=0*
  *    *-network DISABLED*
  *                description: Ethernet interface*
  *                physical id: 2*
  *                logical name: pan0*
  *                serial:  42: f2 : d3 : 0a : 14 : 3c*
  *                capabilities: ethernet physical*
  *                configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A *
  *link=yes multicast=yes*

---

