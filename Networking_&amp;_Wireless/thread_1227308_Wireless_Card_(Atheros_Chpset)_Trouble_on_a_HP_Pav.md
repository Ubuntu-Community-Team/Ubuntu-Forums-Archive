---
title: "Wireless Card (Atheros Chpset) Trouble on a HP Pavilion dv6000"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by SoulMazer on 2009-07-30
Hi, so I've got a HP Pavilion dc6000 laptop and I am trying to get my wireless card to work. I have read a few other threads and they said that most every Atheros driver has been open-sourced in "madwifi". So, I downloaded the latest madwifi from Sourcefource and I am having trouble when building it. When I try a simple "sudo make" in the main directory, it starts to do things, then I get an error:

> 
  CC [M]  /home/foo/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o
/home/foo/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/foo/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/foo/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/foo/Desktop/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/foo/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-13-generic'
make: *** [modules] Error 2


Now, here is some more information about my wireless card.

Output from lspci:
> 
08:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)


If I do "ifconfig", it shows my "eth0" and "lo" network, neither of which are wireless. If I do "iwconfig", I get the following:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


"lsmod | grep "wlan_module_name"" returns nothing.
"dmesg | grep "wlan_module_name"" also returns nothing.

Here is the output of "sudo lshw -C network" that is relevant to my wireless card:
> 
*-network UNCLAIMED     
       description: Network controller
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0


And "iwlist scan" returns...
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


And finally, I am using 32 bit Ubuntu 9.04 with "2.6.28-13-generic i686" being my kernel type.

Well, sorry for the mass of information but I thought I would follow what the sticky said.

So, how can I solve my problem? Thanks very much in advance.

---

### Post by SoulMazer on 2009-08-03
Anybody? Please?

---

### Post by arjuntank on 2009-08-15
[http://ubuntuforums.org/showthread.php?t=1230823](http://ubuntuforums.org/showthread.php?t=1230823)

---

### Post by Cuba71 on 2009-08-17
The ath5k driver works with most Atheros wireless cards, but you can try the "madwifi" driver that you can install from System > Hardware Drives

---

