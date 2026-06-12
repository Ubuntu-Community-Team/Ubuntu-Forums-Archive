---
title: "Getting Wireless N mode to work Ath9k, 11.04 64-bit"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by Captain Easypants on 2011-08-25
Sorry in advance if this has been answered elsewhere, I can't seem to find an answer anywhere. As is probably obvious Ubuntu noob here (Windows competent and loving having made the switch except for the usual troubles, but they're fun to try and solve)
I have a built in wireless card that is capable of connecting to my network on the Wireless N protocols. However it will only work at G speeds. It shows it's connection speed at 54mbps and when i set the network at N only mode it could not even connect. How do I  get it to connect at the faster wireless speeds?
I need the faster speeds as I have a media server on my network. I don't really want to go back to windows but these speeds are bugging me
This is the hopefully relevant information you'll need from my network

sudo lshw -C network
*-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:5f:a6:b6:22
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.38-11-generic firmware=N/A ip=192.168.1.123 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:d1200000-d120ffff

---

### Post by praseodym on 2011-08-25
Hi,

try a module parameter for ath9k:

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rf ath9k
sudo modprobe -v ath9k
sudo service network-manager restart
```
Controls:

```
iwconfig
sudo iwlist scan
dmesg | grep ath
```

---

### Post by Captain Easypants on 2011-08-25
Did that. It chucks up a lot of info. The sudo iwlist scan pulled down all the wireless networks available but the bitrates only went up too 54mbps. don't know anything else I'm supposed to be looking for though...

---

### Post by praseodym on 2011-08-25
Try:
```

sudo iwconfig wlan0 rate auto

```
Which channel do you use?

---

