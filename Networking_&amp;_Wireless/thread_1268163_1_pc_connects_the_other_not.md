---
title: "1 pc connects the other not"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by rastro123 on 2009-09-16
Hi, I got quite a strange problem here. My self and a friend have been using a connecion from a neighbour- with consent of course, we're all broke. I arrived a few days ago, connected with the wpa code on the box and all is good. So my friend who was using xp looked at my ubuntu and liked it, says to me ''ok install it for me'' I did so but he cannot connect with the wireless, only cable. I just looked at iwconfig on mine, and it looks like I'm not associated and maybe I shouldn't be connected- but I am. Here is what mine looks like:
boo@my-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:199  Noise level:164
          Rx invalid nwid:0  invalid crypt:5  invalid misc:0

pan0      no wireless extensions.

boo@my-laptop:~$ 


Now, here is what his looks like:
Ok- something else I just discovered, - on his pc I cannot copy from the termina. The right click does nothing. So here: I type the important info out:
wlan0 IEEE 802.11bg ESSID:''livebox-3268''
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated
Tx-Power=20 dBm
Retry min limit:7  RTS thr:off  Fragment thr=2352 B
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

Would love a little help. My mate is well pisssed at me for convincing him to change from xp to ubuntu. We also tried to re-install xp and got no connection at all, cable or wireless. Please can anyone give some pointers? I am wondering whether his pc is up the junction, its one of these little mini asus pc's Eee 900 Many thanks in advance.

---

### Post by spd106 on 2009-09-16
Have you seen the help wiki?

This page might be helpful.
[https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)

If not then can you please post the output of:
```

sudo lshw -class network
```

Ctrl + Shift + C, should allow you to copy from a terminal.

---

### Post by rastro123 on 2009-09-16
Thanks alot, its getting late here, but I'll try it out tomorrow and get back to you and let you know. Thanks again.

---

### Post by rastro123 on 2009-09-17
hi, I had a look at the page and Im fairly sure that is not the answer to the problem. You see, when I go to network tools on his pc, I see it is exchanging packets, so there must be some kind of connection going on. I looked in the bios and connection is not disabled. Ok so this is what you asked me to look at and send, I hope you have an idea! Cheers mate.
gg@gg-laptop:~$  sudo lshw -class network 
[sudo] password for gg: 
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: 00:23:54:38:d0:0b
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.2.3 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:37:cb:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: be:c4:76:f9:4b:ec
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
gg@gg-laptop:~$

---

### Post by Iowan on 2009-09-17
> **rastro123 said:**
> 
  *-network
       description: Wireless interface
       product: [COLOR="Red"]AR242x[/COLOR] 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:22:43:37:cb:9d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bgI found [this]("http://ubuntuforums.org/showpost.php?p=7438795&postcount=6") in the wireless workarounds.

---

