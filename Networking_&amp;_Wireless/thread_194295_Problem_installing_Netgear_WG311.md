---
title: "Problem installing Netgear WG311"
date: 2006-06-11
forum: Networking &amp; Wireless
---

### Post by Jie Bie on 2006-06-11
Hi there

Been trying to get my netgear wg311 PCI wireless adaptor working for the last hour or so on my new xubuntu installation with little success...

currently i am using the an ethernet cable so i have net access but want to move box to a location where cable isn't possible which is why i want to get the card working.

i have tried following some instructions on the forums and have used apt-get to install linux-restricted-modules-2.6.15-23-386

Based on other threads i have run some commands on my system that hopefully will allow someone to tell me what i need to do!

When i do **lspci** i get:

[FONT="Courier New"]jiebie@kryten:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01) /* I assume this is my wireless card... */
0000:01:01.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)
0000:01:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)[/FONT]

when i do **iwconfig** i get:

[FONT="Courier New"]jiebie@kryten:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

[/FONT]

and when i do **lshw** -C network i get:

[FONT="Courier New"]jiebie@kryten:~$ sudo lshw -C network
  *-network:0 UNCLAIMED  /* what does unclaimed mean?  why is there no logical name!? */
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:ec110000-ec11ffff irq:255
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 4
       bus info: pci@01:04.0
       logical name: eth0
       version: 78
       serial: 00:01:03:15:ad:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=full ip=192.168.1.3 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-207f iomemory:ec100000-ec10007f irq:10
[/FONT]

I have also tried the modprobe command with various options and it normally returns with a "module not found" error.

Hopefully someone can help me!

Cheers

jiebie

---

### Post by deadlycow21 on 2006-06-27
[QUOTE=Jie Bie]Hi there

Been trying to get my netgear wg311 PCI wireless adaptor working for the last hour or so on my new xubuntu installation with little success...

currently i am using the an ethernet cable so i have net access but want to move box to a location where cable isn't possible which is why i want to get the card working.

i have tried following some instructions on the forums and have used apt-get to install linux-restricted-modules-2.6.15-23-386

Based on other threads i have run some commands on my system that hopefully will allow someone to tell me what i need to do!

When i do **lspci** i get:

[FONT="Courier New"]jiebie@kryten:~$ lspci
0000:00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
0000:00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801AA SMBus (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
0000:01:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01) /* I assume this is my wireless card... */
0000:01:01.0 VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)
0000:01:04.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)[/FONT]

when i do **iwconfig** i get:

[FONT="Courier New"]jiebie@kryten:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

[/FONT]

and when i do **lshw** -C network i get:

[FONT="Courier New"]jiebie@kryten:~$ sudo lshw -C network
  *-network:0 UNCLAIMED  /* what does unclaimed mean?  why is there no logical name!? */
       description: Ethernet controller
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@01:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       resources: iomemory:ec110000-ec11ffff irq:255
  *-network:1
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 4
       bus info: pci@01:04.0
       logical name: eth0
       version: 78
       serial: 00:01:03:15:ad:1d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=3c59x driverversion=LK1.1.19 duplex=full ip=192.168.1.3 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:2000-207f iomemory:ec100000-ec10007f irq:10
[/FONT]

I have also tried the modprobe command with various options and it normally returns with a "module not found" error.

Hopefully someone can help me!

Cheers

jiebie[/QUOTE]

madwifi, because you have an athroes, go to freenode channel #madwifi , they can help you with install

---

### Post by stupidkid on 2006-06-27
sudo apt-get install madwifi-ng (I believe that's the package name)
sudo modprobe ath_pci

Then you're good to go. :p

---

### Post by apoth on 2006-10-08
Try something like ```
options acx firmware_ver=1.2.0.30
``` in /etc/modprobe.d/options

---

### Post by ruleboy on 2006-10-08
I used ndiswrapper to get that card working. Search on ndiswrapper and WG311v3, you should find the thread.

---

