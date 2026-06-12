---
title: "Sony Vaio  VGN NR21E/S, wireless"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by cyberurchin on 2009-01-25
Dear Folks!

Does anybody have experience with the installation of the driver for the wireless adapter of a Sony VGN-NR21E/S under Ubuntu?

"lshw -C Network" tells me: 
[....]
*-network
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: driver=ndiswrapper latency=0 module=ndiswrapper
[....]

and "ndisgtk" claims that driver and hardware are present but refuses to configure with the message "Could not find a network configuration tool." But I guess I did something wrong in the beginning because my "iwconfig" looks like this:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

I did, however, change the "blacklist" file and removed "b43", "b44" and "ssb" from the kernel modules. Any ideas?
Another hint: Maybe I'm not using the perfect driver because for my model I could not find any confirmation about which one to use.

Cheers
cyberurchin

---

### Post by cyberurchin on 2009-01-31
Just for the record:

sudo apt-get install linux-backports-modules-intrepid-generic linux-backports-modules-2.6.27-7-generic
sudo modprobe ath5k

solved my problems. Of course, there is a new one now: I see all my neighbours networks but not mine ....

Cheers,
cyberurchin

---

