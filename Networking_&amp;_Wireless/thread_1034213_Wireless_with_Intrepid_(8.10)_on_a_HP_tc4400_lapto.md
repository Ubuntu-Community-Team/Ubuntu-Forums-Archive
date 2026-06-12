---
title: "Wireless with Intrepid (8.10) on a HP tc4400 laptop"
date: 2009-01-08
forum: Networking &amp; Wireless
---

### Post by dkeats on 2009-01-08
My computer is a HP tc4400 tablet PC. I installed Intrepid as a fresh install, reformatting the /partition but leaving the /home partition intact. I moved all .files and ./directories into a backup directory, so it is effectively a completely fresh install. As far as I can see, it has a Intel Corporation PRO/Wireless 3945ABG card, which according to the wiki is supported. However, wireless is greyed out on the network applet, and is not available for configuring. Any assistance with how to get wireless working would be greatly appreciated. If there is a post that is suitable for a dummy like me, please point me to it. I have spent hours googling and searching and have read a bewildering array of conflicting recommendations, none of which make any sense to me. 

The following information pertains to my system.....


The command 
  lspci | grep Wireless
gives the following output
  10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


The command
  iwconfig
gives the following output

  lo        no wireless extensions.
  eth0      no wireless extensions.
  wmaster0  no wireless extensions.
  wlan0     IEEE 802.11abg  ESSID:"Auto Components HS"  
            Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
            Tx-Power=15 dBm   
            Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
            Power Management:off
            Link Quality:0  Signal level:0  Noise level:0
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0

  pan0      no wireless extensions.


The command
  lsmod | grep "wlan_module_name"
produces no output.


The command 
 lshw -C network
produces the following output


  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 21
       serial: 00:16:d4:42:f8:86
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5753m-v3.56 ip=192.168.10.9 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:c3:8b:31
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: e2:59:6b:75:15:83
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



The Command 
  iwlist scan
produces the following:
  lo        Interface doesn't support scanning.
  eth0      Interface doesn't support scanning.
  wmaster0  Interface doesn't support scanning.
  wlan0     No scan results
  pan0      Interface doesn't support scanning.


The command 
  lsb_release -d
produces:
  Description:	Ubuntu 8.10

The command 
  uname -mr
produces:
  2.6.27-11-generic i686


The command
  sudo /etc/init.d/networking restart
produces 
  * Reconfiguring network interfaces...
  Ignoring unknown interface eth0=eth0.

Thanks for any assistance I can get.
regards
derek

---

### Post by dkeats on 2009-01-08
Somehow, after updating and rebooting, this became available again. I think it's probably related to the bug [https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/193970](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/193970)

Oddly, though, I can see my neighbour's network, but cannot see my own. All the other computers in my house (three of them) can see the network fine, and two are running Intrepid and one Hardy. These wireless woes are causing political problems for me at home...with pressure to go proprietary. Any further help would be appreciated if anyone has experienced this problem.

---

### Post by dkeats on 2009-01-08
deleted duplicate text. no idea how to remove the message though.

---

