---
title: "All networking capabilities lost after major update (I think)"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by Sims12345 on 2009-02-02
Hi,

I just updated my Ubuntu 8.10 with the latest kernel updates and such (it said like 60 updates are available even though this wasnt the first time I have updated)last night, and now, I boot up into Ubuntu and I have no networking capabilities at all. I have tried wireless using wifi radar as well as plugging in an ethernet cord and still nothing.

Any help would be appreciated,

Thanks!

---

### Post by basketcase on 2009-02-02
I may have something similar.  Just did a fresh install of Ubuntu 8.10 on an MSI U100 Wind.  Then did an apt-get update with all the latest packages. 

After reboot, I can't get an address on ethernet.  I can connect to Wifi.  

Here is /var/log/syslog

```
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0' 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  (eth0): device state change: 3 -> 4 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled... 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started... 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled... 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete. 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting... 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  (eth0): device state change: 4 -> 5 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful. 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled. 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete. 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started... 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  (eth0): device state change: 5 -> 7 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction. 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  dhclient started with pid 5714 
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete. 
Feb  2 16:37:56 ubuntu-wind dhclient: Internet Systems Consortium DHCP Client V3.1.1
Feb  2 16:37:56 ubuntu-wind dhclient: Copyright 2004-2008 Internet Systems Consortium.
Feb  2 16:37:56 ubuntu-wind dhclient: All rights reserved.
Feb  2 16:37:56 ubuntu-wind dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Feb  2 16:37:56 ubuntu-wind dhclient: 
Feb  2 16:37:56 ubuntu-wind dhclient: wifi0: unknown hardware address type 801
Feb  2 16:37:56 ubuntu-wind NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit 
Feb  2 16:37:56 ubuntu-wind dhclient: wifi0: unknown hardware address type 801
Feb  2 16:37:56 ubuntu-wind dhclient: Listening on LPF/eth0/00:21:85:e0:4d:f3
Feb  2 16:37:56 ubuntu-wind dhclient: Sending on   LPF/eth0/00:21:85:e0:4d:f3
Feb  2 16:37:56 ubuntu-wind dhclient: Sending on   Socket/fallback
Feb  2 16:38:00 ubuntu-wind dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Feb  2 16:38:08 ubuntu-wind dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Feb  2 16:38:14 ubuntu-wind NetworkManager: <info>  (ath0): supplicant connection state change: 7 -> 0 
Feb  2 16:38:14 ubuntu-wind NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4 
Feb  2 16:38:14 ubuntu-wind NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 7 
Feb  2 16:38:20 ubuntu-wind dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Feb  2 16:38:33 ubuntu-wind dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Feb  2 16:38:41 ubuntu-wind NetworkManager: <info>  Device 'eth0' DHCP transaction took too long (>45s), stopping it. 
Feb  2 16:38:42 ubuntu-wind NetworkManager: <info>  eth0: canceled DHCP transaction, dhcp client pid 5714 
Feb  2 16:38:42 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Feb  2 16:38:42 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) started... 
Feb  2 16:38:42 ubuntu-wind NetworkManager: <info>  (eth0): device state change: 7 -> 9 
Feb  2 16:38:42 ubuntu-wind NetworkManager: <info>  Marking connection 'Auto eth0' invalid. 
Feb  2 16:38:42 ubuntu-wind NetworkManager: <info>  Activation (eth0) failed. 
Feb  2 16:38:42 ubuntu-wind NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Timeout) complete. 
Feb  2 16:38:42 ubuntu-wind NetworkManager: <info>  (eth0): device state change: 9 -> 3 
Feb  2 16:38:42 ubuntu-wind NetworkManager: <info>  (eth0): deactivating device (reason: 0). 
Feb  2 16:39:14 ubuntu-wind NetworkManager: <info>  (ath0): supplicant connection state change: 7 -> 0 
Feb  2 16:39:14 ubuntu-wind NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4 
Feb  2 16:39:14 ubuntu-wind NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 7 
Feb  2 16:42:14 ubuntu-wind NetworkManager: <info>  (ath0): supplicant connection state change: 7 -> 0 
Feb  2 16:42:14 ubuntu-wind NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 4 
Feb  2 16:42:14 ubuntu-wind NetworkManager: <info>  (ath0): supplicant connection state change: 4 -> 7 

```If more information is needed, let me know.

Thanks!

---

### Post by Sims12345 on 2009-02-02
I cant connect to either :(

---

### Post by basketcase on 2009-02-02
Not sure if any of this helps:

```
:~$ sudo lshw -c network
  *-generic               
       description: Ethernet interface
       product: Illegal Vendor ID
       vendor: Illegal Vendor ID
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: ff
       serial: 00:21:85:e0:4d:f3
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master vga_palette cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=255 link=yes maxlatency=255 mingnt=255 module=r8169 multicast=yes port=MII speed=100MB/s
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:1d:7d:78:2c:f8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=10.11.103.119 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:43:46:d8:39:c6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by yeats on 2009-02-02
This happened with the kernel update.  If you can boot into the previous kernel, see if that allows networking.  I'm looking into what needs to be done with madwifi to work with the newer kernel.  (I read about this as I got madwifi working, but I was so excited to see a connection that I didn't write it down :oops:

---

### Post by yeats on 2009-02-02
Try this:

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html")

---

### Post by basketcase on 2009-02-02
> **chrissharp123 said:**
> Try this:

[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

My Atheros works with the latest Kernel...it's my wired connection that doesn't work.

Booting into:
Linux ubuntu-wind 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux


I have both wired and wireless.

---

### Post by Ingenium on 2009-02-03
I'm having the same problem with the latest kernel update. Reverting to an older kernel for some reason doesn't fix the problem. Best solution I've found was disabling network manager and manually running wpa_supplicant for wireless and dhclient for wired and wireless to get a connection.

---

### Post by basketcase on 2009-02-03
Well here is some interesting info...if I come up cold, my wired connection doesn't work.  

If I do 'sudo shutdown -r now' my wired connection is available.

I upgraded to the latest build of 9.04...will report back. I wanted to try and grab 2.6.28-5 in intrepid proposed, but for whatever reason, couldn't seem to 'see' it.

---

### Post by MattParkins on 2009-02-03
Ditto, mine hasn't worked since the kernel update either (Dell Mini 9 on Ubuntu 8.10). Doing a "sudo shutdown -r now" does nothing for me.

I really hope they fix this ASAP.  I do have wireless but it crashes the machine every few hours (regardless of encryption protocol).  I just want a stable internet connection.  Its enough to make me want to go back to XP (and I hate XP).  Maybe Fedora 10?

---

### Post by Carlomagno07 on 2009-02-03
I had the same problem. Did "sudo shutdown -r now", rebooted into 2.6.27-7-generic and had my wired network back. This is on Acer AspireOne 150XP with 8.10 installed using Wubi.

---

### Post by basketcase on 2009-02-03
> **Carlomagno07 said:**
> I had the same problem. Did "sudo shutdown -r now", rebooted into 2.6.27-7-generic and had my wired network back. This is on Acer AspireOne 150XP with 8.10 installed using Wubi.

When I had 8.10 installed through Wubi, everything was fine.  It was when I blew it out and put Ubuntu on it w/o anything else did wired-networking break.

---

### Post by basketcase on 2009-02-03
FWIW,
I installed the latest 9.04 build with 2.6.28-6 and it works from a cold start.  Both wired and wireless.

---

### Post by Dark_vampel on 2009-02-03
I have Hardy Heron and how do you repeal a update? I'm have the same network issues...

---

### Post by Carlomagno07 on 2009-02-03
Thanks. On my main laptop I have 8.04 LTS, so no problems. On the Acer AspireOne with 8.10, I just boot into the older kernel. I can't be asked to install a non-production release. I'm sure the issue with the new kernel will get fixed soon.

---

### Post by basketcase on 2009-02-03
It probably will be fixed.  You could add the intrepid proposed, but that's like updating to an unreleased version I guess.  I've had success with pre-releases, so I'm fairly confident and this isn't my only computer, so I'm not too worried.

---

### Post by fervor on 2009-02-13
I also had this problem. After installing the latest updates I lost both wired and wireless networking connections. On a whim I tried my USB NIC and it worked (I'm posting with it)! It's details are:

Bus 002 Device 002: ID 0bda:8150 Realtek Semiconductor Corp. RTL8150 Fast Ethernet Adapter

.

---

### Post by Sims12345 on 2009-02-13
If you are using madwifi, just reinstall and it should work. Thats what I did and I got everything back

---

### Post by kevdog on 2009-02-13
Custom kernel modules are never included in stock kernel updates -- hence the reason they are called custom kernel modules.  These customs include: madwifi, broadcom (b43, wl/STA, bcm43xx), and ndiswrapper.  If you were using any of these modules you need to either reinstall the module(s), or simply boot into the old kernel.

---

