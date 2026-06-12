---
title: "Wireless connection gone Ubuntu 9.10."
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by gordon33 on 2010-06-06
Hello All  

I have  a HP laptop with Ubuntu 9.10 and the router is a Netgear.  The wireless connection worked before I down loaded the last Ubuntu updates a few days ago.  

Another lab top was able to connect to the wireless router.  At least it did until I Went to [http://www.routerlogin.net](http://www.routerlogin.net) to change the settings.

I went to change the settings because I thought the latest downloads eliminated the WEP Encrypition Key Size I had picked over a year ago (WEP 64).  

So I went to [http://www.routerlogin.net](http://www.routerlogin.net) to change the  Encrypition Key Size to one seen on the pull down menu (WEP 128).  Now nether computer can connect to the router.  Now the WEP Key is 26 characters.

My experience is minimal.  So I do not even know the what Terminal commands to use to trouble shoot this.

Thank you for any help.

Gordon33

---

### Post by gordon33 on 2010-06-06
Hello All  

Following other post I got the following from my terminal.

lshw -C network

Gordon33gordon@gordon-laptop:~$ sudo lshw -C network 

[sudo] password for gordon: 

  *-network               

       description: Ethernet interface

       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:01:00.0

       logical name: eth0

       version: 02

       serial: 00:1f:16:76:dc:4b

       size: 100MB/s

       capacity: 100MB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s

       resources: irq:27 ioport:3000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)

  *-network

       description: Wireless interface

       product: AR5001 Wireless Network Adapter

       vendor: Atheros Communications Inc.

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: wmaster0

       version: 01

       serial: 00:24:2b:af:c5:33

       width: 64 bits

       clock: 33MHz

       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless

       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg

       resources: irq:17 memory:d2600000-d260ffff

gordon@gordon-laptop:~$ ^C



lspci
gordon@gordon-laptop:~$ lspci

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

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)

00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)

00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)

00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

gordon@gordon-laptop:~$ ^C

---

### Post by gordon33 on 2010-06-23
Hello All

A few weeks ago my HP lap top's wireless connection was fine with Ubuntu 9.10.  I installed updates a few days before Ubuntu 10.4 came out.  Thats when the different routers ( mine and the 3 or 4 others in the neighborhood disappeared form the wireless pull down menu.  I have not been able to connect to my Netgear router since.  (I could and can connect with a wire.)

I tried a reinstall of the router.  (Reinstalling the WEB Key)  No luck.

So I installed Ubuntu 10.4 hoping that would recognize the routers again.  No luck.

One of the local Linux experts at wlug said I should report the bug.  Sadly I was unsuccessful in navigating the web site he suggested.  But I thought others would make the report any way.  I did see similar post at the Ubuntu web site for bugs.  I thought the next update would include the fix.  2 or 3 updates later my computer does not recognize the router.

I have very limited experience with computers.  Please help.


gordon33

---

### Post by gordon33 on 2010-06-23
Hello all

I installed another update just before posting the note above.  Now the wire less icon on the panel is gone.  For got to mention that in the first post.

Gordonee

---

### Post by gordon33 on 2010-06-29
Hello All

Have not been able to connect to wireless since the update about May27.  At that time I was running 9.10 Updated to 10.04 but it did not help.

I have been going through the Ubuntu "WifiDocs Wireless Trouble Shooting Guide"  I got to section 4.3.5 and Code: "rfkill list" said "Hard blocked: yes".  So how do you rectify this?  Maybe someone else has the same laptop and knows the work around.

HP G6OT laptop with an Atheros Communications Inc. 
AR5001 Wireless Network Adapter
.

Use to connect to my Netgear WGR614 

The laptop does not recognize any wireless routers now.

Gordon

---

### Post by gordon33 on 2010-06-29
Hello All

Happy but why did it start to work?

I have posed several request for help for no wifi on HP laptop.  I used the trouble shooting page and found there was a hard block by running code:  rfkill list 

I read some other sites and decided to look at the BIOS.  Never got to the BIOS but  I got to this list of about 15 different options starting with 10.04.  I went through the list looking for a BIOS option.  None were found.  Went back to the top and hit enter.  The laptop booted up and the wifi started to work?  Happy but why did it start to work?

---

### Post by gordon33 on 2010-06-29
SEE

[http://ubuntuforums.org/showthread.php?t=1520352](http://ubuntuforums.org/showthread.php?t=1520352)

---

### Post by gordon33 on 2010-06-29
SEE 

[http://ubuntuforums.org/showthread.php?t=1520352](http://ubuntuforums.org/showthread.php?t=1520352)

---

### Post by Iowan on 2010-06-29
Threads merged - glad you got it working.

---

