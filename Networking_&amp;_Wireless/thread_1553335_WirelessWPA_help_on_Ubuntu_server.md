---
title: "Wireless/WPA help on Ubuntu server"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by thaddicus on 2010-08-14
Greetings all,

I've been having issues setting up the wireless interface on my Ubuntu server (command-line only, no GUI) and I can't seem to get it working.  It seems as though the card is recognized, the drivers are installed and the interface is up, but it fails to connect.  I have no idea where I'm going wrong.  I have WPA and a MAC filtering setup on my wireless router.  An exception has been made for this PC's MAC address and I've manually entered the connection details into /etc/network/interfaces.

lshw -C Network produces the following results:
*-Network
     description: Wireless interface
     product: RT2561/RT61 802.11g PCI
     vendor: RaLink
     physical id: 9
     bus info: pci@0000:01:09.0
     logical name: wlan0
     version 00
     serial: 00:1a:ef:0d:f7:b5
     width: 32 buts
     clock: 33MHz
     capabilities: pm bus_master cap_list ethernet physical wireless
     configuration: broadcast=yes driver=rt61pci latency=32 multicast=yes wireless=IEEE 802.11bg
     resources: irq:5 memory:fdff8000-fdffffff

Below is the /etc/network/interfaces config:
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
netmask 255.255.255.192
gateway 10.40.0.1
wpa-proto WPA
wpa-key-mgmt WPA-PSK
wireless-essid nightshade
wireless-key <my preshared key>
wireless-channel 10
wireless-mode managed
#auto eth0
#iface eth0 inet dhcp

If I do a sudo invoke-rc.d networking restart, I get:

DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
...
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

One thing I noticed is that the subnet mask here is different from the one I entered in /etc/network/interfaces.  Not sure if that's relevant or not.  At any rate, I've been banging my head against a wall for the last week so any assistance would be greatly appreciated.  Thanks.

---

### Post by thaddicus on 2010-08-15
I also noticed that when running a few commands that require entering the WPA preshared key (mine is a 63-character key with ascii characters), I'm getting the same errors.  I always get a bash error "event not found" that lists the characters between the ! and the > symbols.  Can you not use these two characters for a preshared key?

I googled the error and found:

When you type a word preceeded by an "!", bash thinks you want to recall a previous command or "event".

---

### Post by thaddicus on 2010-08-17
*bump*

---

