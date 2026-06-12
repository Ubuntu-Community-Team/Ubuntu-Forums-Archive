---
title: "'Device not ready' after update?"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by Rave Gloves on 2009-09-02
I have had 9.04 for a month now and i love it but when i did an update today it was still working fine, i turned off my computer and when i switched it on i find that im not connected to the wireless. I clicked on it and it says 'wireless Networks' Device not ready.    Im using a Samsung R610, could someone please help me, this is a massive setback and one of the reasons i was unsure of redownloading it!

Edit: I think i have a AR242x  802.11abg wireless PCI Express adapter 
I have looked in my hardware area and checked my drivers, i activated the 'Alternate Atheros "madwifi" Driver, nothing happend. Im sure it will have something to do with the drivers. If anymore info is needed just ask!

---

### Post by Rave Gloves on 2009-09-02
Come on guys, i need to get this sorted soon! ]:

---

### Post by Rave Gloves on 2009-09-02
> **Rave Gloves said:**
> Come on guys, i need to get this sorted soon! ]:

Shameless bumb again, keeping this to the front page

---

### Post by Rave Gloves on 2009-09-03
Another bump to the front page, can someone please answer this for me?

---

### Post by cariboo on 2009-09-03
Could you open a terminal and type:

```
sudo lshw -C network > network.txt
```

The above command will output all the details of your network devices to a text file called network.txt. Could post the output in  your next post.

---

### Post by Rave Gloves on 2009-09-03
> **cariboo907 said:**
> Could you open a terminal and type:

```
sudo lshw -C network > network.txt
```

The above command will output all the details of your network devices to a text file called network.txt. Could post the output in  your next post.

This will prove a small problem, im on a back-up laptop at the moment, give me 5mins to get a memory pen and transfere it over!

---

### Post by Rave Gloves on 2009-09-03
*-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 13
       serial: 00:13:77:d0:16:bc
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: fa:d7:cf:44:2a:70
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by cariboo on 2009-09-03
Open a terminal and type:

```
lsmod | grep ath
```

to see if the ath5k_pci, ATL1E and ath5k drivers have been loaded. If they are present you need to add them to /etc/modprobe.d/blacklist.conf, once you have added the drivers to the blacklist and reboot.

---

### Post by Rave Gloves on 2009-09-03
> **cariboo907 said:**
> Open a terminal and type:

```
lsmod | grep ath
```

to see if the ath5k_pci, ATL1E and ath5k drivers have been loaded. If they are present you need to add them to /etc/modprobe.d/blacklist.conf, once you have added the drivers to the blacklist and reboot.

I have, 

ath_pci        99224 0
wlan           210544 1 ath_pci
ath_hal        198864 1 ath_pci

---

### Post by cariboo on 2009-09-03
> ath_pci 99224 0
wlan 210544 1 ath_pci
ath_hal 198864 1 ath_pci

The above qouted driver is a conflicting driver. Press ALt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

and add the three drivers in my pervious post to the file, then reboot.

---

### Post by Rave Gloves on 2009-09-03
> **cariboo907 said:**
> The above qouted driver is a conflicting driver. Press ALt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

and add the three drivers in my pervious post to the file, then reboot.

Do i just type the name of the driver into the blacklist?

---

### Post by cariboo on 2009-09-03
Yes add the drivers to the bottom of the file.

---

### Post by Rave Gloves on 2009-09-03
> **cariboo907 said:**
> Open a terminal and type:

```
lsmod | grep ath
```

to see if the ath5k_pci, ATL1E and ath5k drivers have been loaded. If they are present you need to add them to /etc/modprobe.d/blacklist.conf, once you have added the drivers to the blacklist and reboot.

When i type in the ATL1E file it is highlighted yellow, and wont let me save any idea why?

---

### Post by cariboo on 2009-09-03
Try it in lower case:

```
atl1e
```

---

### Post by Rave Gloves on 2009-09-03
i think the problem is, i dont think i even have the drivers you suggested, when i do the lsmod | grep atm code i only get 3 codes, ath_pci
wlan
ath_hal

You think this could be the problem?

---

### Post by cariboo on 2009-09-03
> **Rave Gloves said:**
> I have, 

ath_pci        99224 0
wlan           210544 1 ath_pci
ath_hal        198864 1 ath_pci

You have the ath_pci, once you blacklist it, it won't load. The other two you have, but they may load if you just blacklist the ath_pci.

---

### Post by Rave Gloves on 2009-09-03
> **cariboo907 said:**
> You have the ath_pci, once you blacklist it, it won't load. The other two you have, but they may load if you just blacklist the ath_pci.

I have never used the blacklist before!, right, i wont let mesave on the one that first opens, it tells me the modprobe.d thing isnt found, but if i click new and then type it in it lets me save, will i need to go to the terminal now and blacklist it from there now or what~?

---

