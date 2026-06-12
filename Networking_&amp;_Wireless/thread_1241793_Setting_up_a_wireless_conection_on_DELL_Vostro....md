---
title: "Setting up a wireless conection on DELL Vostro..."
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by lexo22 on 2009-08-16
I am using  a DELL Vostro computer and I would like you to help me set up my wireless conection...

---

### Post by The Toxic Mite on 2009-08-16
Hehe! Welcome to Ubuntu! :D

Go to Applications > Accessories > Terminal, and enter the following commands please:

```

sudo lshw -c network
lspci
iwconfig
ifconfig

```

Post the outputs of them when you're done :)

---

### Post by lexo22 on 2009-08-16
[B]  *-network UNCLAIMED     
       description: Network controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:8e:db:c5
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.3 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 0a:22:e6:64:2d:d9
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

-----------------------------------------------------------------------------------------------------------------------------[/B]

This is all it says...:) Oh, I am currently conected to the net by cable

---

### Post by The Toxic Mite on 2009-08-16
> **lexo22 said:**
> [snip]
** --------------------------------------------------------------------------------------------------**

This is all it says...:)

What version of Ubuntu are you running?

---

### Post by lexo22 on 2009-08-16
The latest release **Ubuntu 9.04**...:P:):popcorn:

---

### Post by The Toxic Mite on 2009-08-16
> **lexo22 said:**
> The latest release **Ubuntu 9.04**...:P:):popcorn:

Strange - My laptop had an Atheros card and the wireless worked as soon as I installed it...

Go to System > Administration > Hardware Drivers and tell me if there is an alternate driver for it?

:-k

EDIT: Click on the icon that looks like 4 bars, and tell me if it detects any networks?

---

### Post by lexo22 on 2009-08-16
Alternate "madwifi" driver for Atheros wireless LAN cards.

Only activate this driver if you have problems with your wireless LAN connection.

The free "ath5k" driver should work with most Atheros cards nowadays, but on some computers this alternate (but proprietary) driver still works better, or at all.
[B]
Must I activate the driver?! If so, what then...[/B]:):P

---

### Post by The Toxic Mite on 2009-08-16
> **lexo22 said:**
> Alternate "madwifi" driver for Atheros wireless LAN cards.

Only activate this driver if you have problems with your wireless LAN connection.

The free "ath5k" driver should work with most Atheros cards nowadays, but on some computers this alternate (but proprietary) driver still works better, or at all.
[B]
Must I activate the driver?! If so, what then...[/B]:):P

Heh.

Have you clicked the icon that looks like 4 bars? A drop down menu comes up. Tell me if it detects any networks.

---

### Post by lexo22 on 2009-08-16
[IMG]http://golf4you.webs.com/Screenshot-Hardware%20Drivers.png[/IMG]

[SIZE=4]So, this is what it says under** Hardware Drivers...**

What now?![/SIZE] :)

---

### Post by The Toxic Mite on 2009-08-16
> **lexo22 said:**
> [IMG]http://golf4you.webs.com/Screenshot-Hardware%20Drivers.png[/IMG]

[SIZE=4]So, this is what it says under** Hardware Drivers...**

What now?![/SIZE] :)

Right....

Don't activate it yet

Have you clicked on the icon with 4 bars? It should look like this when you open it:

[img]http://upload.wikimedia.org/wikipedia/commons/c/c0/NetworkManager.png[/img]

---

### Post by lexo22 on 2009-08-16
[SIZE=5]But what now?! I don't see a drop box here...
[/SIZE]

---

### Post by lexo22 on 2009-08-16
Where can I find the "drop box"?!

[IMG]http://golf4you.webs.com/Screenshot.png[/IMG]

I've got the Wicd manager, but it finds no wireless conections...

---

### Post by The Toxic Mite on 2009-08-16
That explains it then...

Try enabling the Madwifi driver

---

### Post by lexo22 on 2009-08-16
So... I go here:
[IMG]http://golf4you.webs.com/Screenshot-Wicd%20Manager.png[/IMG]

And then do this... Right?!

[IMG]http://golf4you.webs.com/Screenshot-Preferences.png[/IMG]

Is this okay?!... Or what must I do?! :lolflag:

---

