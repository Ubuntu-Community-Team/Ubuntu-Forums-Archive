---
title: "HELP! atheros wireless still doesn't work! new to linux..."
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by mplinux on 2009-03-11
Hello,
It's my first time on here. I'm a complete newbie to linux. I just installed ubuntu 8.10 on my system set as dual boot with vista. Everything works like a charm, but my wireless does not work. I have read multiple threads and tried several fixes with no success, please HELP! I want don't want to go back to vista. 

System Description:
Toshiba Satellite L305d-S5893.
AMD 64-bit.
Wireless card: Atheros AR5007EG.

List of attempted fixes per forum recommendations:

1st ATTEMPT:
I Tried installing wcid (wireless connection manager) to see if anything changed and came up with wireless connection. NO FIX although I like the interface. :(

2nd ATTEMPT:
As instructed in instructions on installation guide on I ran ndisgtk and downloaded the 64 bit driver identified on this thread [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828). I ran ndisgtk and added the driver as instructed (64-bit). unactivated the atheros driver on SYSTEM>ADMINISTRATOR>HARDWARE DRIVER. This was done to ensure that only the new driver is running. Restarted the system. still no FIX. :(

3rd ATTEMPT:
I found another thread recommending to check out the release notes for 8.10 that discuss issues with the ath5k wireless drivers and recommended to download "linux-backports-modules-intrepid-generic" package. This supposedly has a updated version of ath5k which it does since under Hardware Driver list a new driver called "support for atheros 5xxx driver" appeared. I activated the driver and removed the other driver using ndisgtk,to ensure that only the new driver is running. RESTARTED the system. Still NO FIX!:(

what should i do next?! any help will be greatly appreciated I really want to learn all about linux and make it my new OS. 
 
FYI: I ran terminal: sudo lshw -c network ///this is what i still get:
 *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

I ran terminal: lspci 
OUTPUT:
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

any suggestions out there will be greatly appreciated?

---

