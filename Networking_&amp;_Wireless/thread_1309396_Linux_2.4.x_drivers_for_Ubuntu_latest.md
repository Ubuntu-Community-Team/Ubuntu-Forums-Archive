---
title: "Linux 2.4.x drivers for Ubuntu latest?"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by user1119 on 2009-11-01
I have a NIC card that is:TP-LINK 10/100M Fast Ethernet Adapter  (desktop pci NIC)
Its model number: TF-3239D/TF-3239DL/TF-5239

The drivers are for linux 2.4.x ? (yeah it's old).  When I put the drivers CD in nothing happens, I tried navigating to the CD to see the linux files on it, but the folder is empty, so I assume ubuntu can't read them?  It can see the Windows drivers.

Can anyone help?

---

### Post by user1119 on 2009-11-01
bump

---

### Post by user1119 on 2009-11-01
bump

---

### Post by chili555 on 2009-11-01
I think this card works with a module that's already a part of Ubuntu. Please open a terminal and do:```
sudo modprobe 8139cp
ifconfig
```Do you now have an interface, *eth0*, perhaps? Can you click the Network Manager icon and connect? If not, please run:```
lshw -C network
```and post the result. Thanks.

---

### Post by user1119 on 2009-11-08
> **chili555 said:**
> I think this card works with a module that's already a part of Ubuntu. Please open a terminal and do:```
sudo modprobe 8139cp
ifconfig
```Do you now have an interface, *eth0*, perhaps? Can you click the Network Manager icon and connect? If not, please run:```
lshw -C network
```and post the result. Thanks.

I have *etho0* because I think I installed ubuntu with an ethernet cord plugged in.  
I'll try what you posted above that though.

Still open for suggestions please!:KS

---

### Post by chili555 on 2009-11-08
If you have *eth0* then you are all set! Your ethernet card has grabbed the correct driver already.

---

### Post by user1119 on 2009-11-08
Scratch that. I have Auto eth0 under wired connections. Under wireless it's empty :(

---

### Post by chili555 on 2009-11-08
> **user1119 said:**
> Scratch that. I have Auto eth0 under wired connections. Under wireless it's empty :(> TP-LINK 10/100M Fast [COLOR="Red"]Ethernet[/COLOR] AdapterWe thought you were looking to get your ethernet going. No?

---

### Post by user1119 on 2009-11-08
No, trying to get it setup for: TP-LINK 10/100M Fast Ethernet Adapter  (desktop pci NIC)
Its model number: TF-3239D/TF-3239DL/TF-5239

---

### Post by snowpine on 2009-11-08
> **user1119 said:**
> No, trying to get it setup for: TP-LINK 10/100M Fast Ethernet Adapter  (desktop pci NIC)
Its model number: TF-3239D/TF-3239DL/TF-5239

Ubuntu is pretty cool, but even Linux can't turn an Ethernet card into a wireless card. :(

---

### Post by chili555 on 2009-11-08
> No, trying to get it setup for: TP-LINK 10/100M Fast Ethernet AdapterThat's an ethernet device, that is, wired. If you have a wireless device, we need to identify it to help you set it up. If it's a USB device, open a terminal and do:```
lsusb -v
```If it's a PCI device, please do:```
sudo lshw -C network
```Post the result and we'll be glad to help.

---

