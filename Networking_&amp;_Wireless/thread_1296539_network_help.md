---
title: "network help"
date: 2009-10-20
forum: Networking &amp; Wireless
---

### Post by naught405 on 2009-10-20
Hi i'm relatively new to ubuntu and this is my first experience with UNR (9.04).
i just installed it and my wired connection wasn't working (i understand i have to install madwifi drivers for my atheros wireless card to work?)
this is an Asus Eee 1005HAB

here is the result of lshw -c network

  	 	 	 	 	 	    *-network UNCLAIMED      
        description: Network controller
        product: AR9285 Wireless Network Adapter (PCI-Express)
        vendor: Atheros Communications Inc.
        physical id: 0
        bus info: pci@0000:02:00.0
        version: 01
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress bus_master cap_list
        configuration: latency=0
   *-network UNCLAIMED
        description: Ethernet controller
        product: Attansic Technology Corp.
        vendor: Attansic Technology Corp.
        physical id: 0
        bus info: pci@0000:01:00.0
        version: c0
        width: 64 bits
        clock: 33MHz
        capabilities: pm msi pciexpress vpd bus_master cap_list
        configuration: latency=0
   *-network DISABLED
        description: Ethernet interface
        physical id: 1
        logical name: pan0
        serial: 56:8b:b1:3f:d9:1a
        capabilities: ethernet physical
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
 
it appears my ethernet interface is disabled. ifup pan0 returns
Ignoring unknown interface pan0=pan0

---

### Post by drpjkurian on 2009-10-21
Hi
Please visit my thread
[http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)
It might help you

With
Regards
Dr Kurian

---

### Post by naught405 on 2009-10-21
thanks for responding to my post.  My problem isn't with installing madwifi.  in order to use sudo-apt get i need an active internet connection.  as you can see from the readout above none of my connections are working.  i need to get the wired connection (pan0) from disabled to enabled so i can get online to install build-essentials and madwifi

---

### Post by naught405 on 2009-10-22
Whew! I found a fix for this particular problem on another forum.

from this [http://forum.eeebuntu.org/viewtopic.php?f=46&p=20931](http://forum.eeebuntu.org/viewtopic.php?f=46&p=20931)
link download the second file (linux-image) and run it then restart.
Worked perfectly for me with Uubuntu Netbook Remix on
Asus Eee 1005HAB.

Hope this is helpful to other people having networking trouble
with UNR and Asus Eee PCs.
[]("http://forum.eeebuntu.org/viewtopic.php?f=46&p=20931")

---

