---
title: "No wireless/messed up /etc/network/interfaces"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by nimonika on 2009-01-23
I am having a very serious problem with regards to wireless. I moved house however kept my ISP provider and all the network configuration same as it was earlier. Now when the broadband was activated at the new place, my laptop which used to seamlessly connect earlier, does not recognise the same username/password. The worst part is it works under windows absolutely fine.

To top it up, I have messed up my /etc/network/interfaces so now I am completely helpless. Please could someone tell me if there is a way to automatically generate the interface file.

I need help urgently!!!

---

### Post by bgerlich on 2009-01-23
Clean the interfaces file and insert two lines
auto lo
iface lo inet loopback

---

### Post by nimonika on 2009-01-23
I did exactly that, but no wireless and for some reason the NFS Start daemon takes forever to come back up after booting - to add to my woes.. Here is the output from lshw

*-network               
       description: Ethernet interface
       product: 88E8036 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:13:a9:60:97:05
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=143.210.72.252 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:ad:46:07
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11abg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:e9:8f:80:7e:8a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

How can I enable the wireless again?

Thanks

---

### Post by bgerlich on 2009-01-23
check if you have wlan0 in iwconfig, if yes, try sudo ifconfig wlan0 up , if not, sudo modprobe -r iwl3945 and sudo modprobe iwl3945 and dmesg | tail afterwards to see what's wrong.

---

### Post by nimonika on 2009-01-23
output from iwconfig:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"uol"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


Output from dmesg |tail

[  589.798475] Registered led device: iwl-phy0:TX
[  589.826580] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  590.566502] eth1: authenticate with AP 00:0f:34:46:c9:70
[  590.568360] eth1: authenticated
[  590.568373] eth1: associate with AP 00:0f:34:46:c9:70
[  590.579653] eth1: RX AssocResp from 00:0f:34:46:c9:70 (capab=0x421 status=0 aid=1)
[  590.579664] eth1: associated
[  590.585867] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  590.586431] eth1: disassociating by local choice (reason=3)
[  600.809077] eth1: no IPv6 routers present


Thanks

---

### Post by bgerlich on 2009-01-23
Are you using WPA on your router by any chance ? 

The wifi card itself seems to work fine.

Could it be that your system is riddled by this bug? [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272185](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272185)

---

### Post by nimonika on 2009-01-23
Yes, i am using WPA, but it used to work fine till 1 week ago!!!...

---

