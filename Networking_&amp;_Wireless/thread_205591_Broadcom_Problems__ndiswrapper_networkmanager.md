---
title: "Broadcom Problems  ndiswrapper networkmanager"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by exemplari on 2006-06-28
I've already been here:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

I blacklisted bcm43xx because it was conflicting with wpa_supplicant and opted to use ndiswrapper. Ndiswrapper seems to be working fine

> dmesg | grep ndis
[17179600.228000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179600.276000] ndiswrapper: driver bcmwl5 (Broadcom,05/26/2005, 3.120.27.0) loaded
[17179600.284000] ndiswrapper: using irq 5
[17179601.360000] wlan0: ndiswrapper ethernet device 00:90:4b:1a:ae:85 using driver bcmwl5, 14E4:4320.5.conf


I can use iwconfig, ifconfig, and dhclient to control the wlan0 device but when the nm-applet tries to use it there is always a time out and eventually it reverts back to eth0.

I think this has something to do with it... 

> 
tail /var/log/messages
Jun 28 13:56:12 achilles dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun 28 13:56:12 achilles dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 28 13:56:12 achilles dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jun 28 13:58:53 achilles kernel: [17180154.276000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 28 13:58:57 achilles kernel: [17180158.276000] b44: eth0: Link is up at 10 Mbps, half duplex.
Jun 28 13:58:57 achilles kernel: [17180158.276000] b44: eth0: Flow control is off for TX and off for RX.
Jun 28 13:58:57 achilles kernel: [17180158.276000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jun 28 13:59:04 achilles dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jun 28 13:59:04 achilles dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jun 28 13:59:04 achilles dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers


I have seen other people with this problem:
[https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/32275](https://launchpad.net/distros/ubuntu/+source/ndiswrapper/+bug/32275)

It may just be something to do with the /etc/network/interfaces file , not sure, anybody have any clues? and is this a bug? 

> 
sudo lspci -v

0000:02:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
        Subsystem: Dell TrueMobile 1300 WLAN Mini-PCI Card
        Flags: bus master, fast devsel, latency 32, IRQ 5
        Memory at faff6000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [40] Power Management version 2

I have gotten this card to work on several other distros including breezy with ndiswrapper and network manager. I think wpa_supplicant is the only difference.

---

### Post by hbweb500 on 2006-06-28
I too have a Broadcomm 4306, and I use the ndiswrapper driver for it. When I install, I first disable the NIC card in Network settings, and "sudo rmmod bcm43xx" "sudo ndiswrapper -m" "sudo modprobe ndiswrapper" and the card works. I also blacklist the bcm43xx module, as you have already done.

I get the timeout too sometimes, but I believe disabling the eth0 (or whatever your NIC card is) helps. Of course, this is only in my experience, so it may do nothing for you.

---

### Post by rfdeshon on 2006-08-31
I have this same problem with my laptop (Lenovo 3000 C100). Is there no one out there who has a fix for this? It is a real pain in the butt to not be able to use my wireless, so much so that I am considering going back to Windoze.

---

### Post by UrbenLegend on 2006-08-31
I have the same wireless, a Belkin 54g based on the broadcom 4306 chip. I've installed ndiswrapper properly and its working without encryption, however its listed as eth0 instead of wlan0. How did you get yours on wlan0?

Also the network manager didn't seem to work for me. Whenever I try to connect, the nm-applet just does its little animation and then after 5 minutes returns back to the icon with the computer and the exclaimation mark. Anyone know what's wrong? Any log files that I can check?

---

### Post by dkerlee on 2007-03-04
> **UrbenLegend said:**
> I have the same wireless, a Belkin 54g based on the broadcom 4306 chip. I've installed ndiswrapper properly and its working without encryption, however its listed as eth0 instead of wlan0. How did you get yours on wlan0?

Also the network manager didn't seem to work for me. Whenever I try to connect, the nm-applet just does its little animation and then after 5 minutes returns back to the icon with the computer and the exclaimation mark. Anyone know what's wrong? Any log files that I can check?

I found that updating to the latest ndiswrapper from [here]("http://ndiswrapper.sourceforge.net/"), and the driver for the specific chipset (lspci | grep Broadcom) from [here]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List") made it so that my wireless came up as wlan0 rather than eth1 or eth0 or something like it did with the default ndiswrapper version.

---

