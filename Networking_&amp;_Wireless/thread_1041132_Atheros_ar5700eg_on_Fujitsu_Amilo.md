---
title: "Atheros ar5700eg on Fujitsu Amilo"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by nettirb on 2009-01-16
I know millions of people have trouble with this card and i spent the last couple of days thinking i hadnt installed the drivers correctly. I followed a tutorial and now when i look at the network manager it shows a wireless networks title which was not there before i installed the drivers. So i guess the card is now detected by ubuntu, using ifconfig i get wlan0 and wmmaster and they have the same mac as my wireless card so i know it is now there.

The problem is that no wireless networks are detected and i am assuming this is because the wireless switch is not active, normally i have to press fn + f1 to switch it on, but this doesnt work. I have also looked in the wireless and it says enabled.

Any ideas? thanks.

---

### Post by superprash2003 on 2009-01-16
post output of the following from the terminal
1)lshw -C network
2)iwlist scanning
3)iwconfig

---

### Post by nettirb on 2009-01-16
loz@nero-zero:~$ sudo su
root@nero-zero:/home/loz# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:12:02:c6:cc
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 04
       serial: 00:13:42:c1:93:c6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d6:df:0c:03:34:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
root@nero-zero:/home/loz# iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.

root@nero-zero:/home/loz# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

root@nero-zero:/home/loz# 

thanks

---

### Post by nettirb on 2009-01-16
any  help?

---

### Post by superprash2003 on 2009-01-18
are you sure you have a wifi network around? cause output says that no networks found!!

---

