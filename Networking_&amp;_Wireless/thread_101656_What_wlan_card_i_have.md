---
title: "What wlan card i have ??"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by apix on 2005-12-10
Whenever i type lspci i get :

```

0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 740 Host (rev 01)
0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] (rev 25)
0000:00:02.1 SMBus: Silicon Integrated Systems [SiS]: Unknown device 0016
0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE]
0000:00:02.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)
0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter

```

Does anyone recognises a wlan card ? I am sure that the laptop has a card, because i used it with wins...

Thanks in advance.. :)

---

### Post by atoponce on 2005-12-10
There is no WLAN card listed in the above.  Is the card integrated into the laptop or is it a seperate PCMCIA card?  All I see is a 56K modem and a Gigabit Ethernet LAN (among the rest of your hardware).

---

### Post by apix on 2005-12-10
Its not pmcia. Its inside the pc.

---

### Post by Lambert on 2005-12-10
Sometimes internal devices don't show on the pci channels (which lspci shows)

Try this command

sudo lshw -businfo

And print that here. If you recognized the device in the list then notice what class the item is and run this command and post output here.

sudo lshw -C <class>

where <class> = the class of the device minus the <>

---

### Post by apix on 2005-12-10
```

apix@giraffe:~$ sudo lshw -businfo
Bus info     Device    Class          Description
=================================================
                       system         i-Buddie
                       bus            i_Buddie
                       memory         BIOS
cpu@0                  processor      mobile AMD Duron(tm)
                       memory         L1 cache
                       memory         L2 cache
                       memory         System memory
pci@00:00.0            bridge         740 Host
pci@00:01.0            bridge         Virtual PCI-to-PCI bridge (AGP)
pci@01:00.0            display        65x/M650/740 PCI/AGP VGA Display Adapter
pci@00:02.0            bridge         SiS962 [MuTIOL Media IO]
pci@00:02.1            bus            SiS961/2 SMBus Controller
pci@00:02.5            storage        5513 [IDE]
ide@0        ide0      bus            IDE Channel 0
ide@0.0      /dev/hda  disk           FUJITSU MHT2030AT
ide@1        ide1      bus            IDE Channel 1
ide@1.0      /dev/hdc  disk           PHILIPS CD-RW/DVD-ROM SCB5265
pci@00:02.6            communication  AC'97 Modem Controller
pci@00:02.7            multimedia     Sound Controller
pci@00:03.1            bus            USB 1.0 Controller
usb@2        usb2      bus            Silicon Integrated Systems [SiS] USB 1.0 Controller (#2)
usb@2:2                generic        IEEE 802.11b PRISM3 USB
pci@00:03.0            bus            USB 1.0 Controller
usb@1        usb1      bus            Silicon Integrated Systems [SiS] USB 1.0 Controller
usb@1:2                input          USB MOUSE
pci@00:03.3            bus            USB 2.0 Controller
usb@3        usb3      bus            Silicon Integrated Systems [SiS] USB 2.0 Controller
pci@00:07.0  eth0      network        RTL-8169 Gigabit Ethernet
             wlan0     network        Ethernet interface

```

I think that you need the wlan0.. :

```

apix@giraffe:~$ sudo lshw -C network
  *-network
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@00:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e6:be:7b:e8
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.0.2 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:cc00-ccff iomemory:cfff8f00-cfff8fff irq:5
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: wlan0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=p80211_prism2_usb driverversion=0.2.2 link=no multicast=yes

```

EDIT:I think that the DISABLED word is not ok. Does this means that the card is off or something like that ??

---

### Post by tonysathre on 2005-12-10
most likely, try removing DISABLED and see if that works, not sure if this will work or not tho, after that run this:   iwdown wlan0 && iwup wlan0 && dhclient

---

### Post by Lambert on 2005-12-10
Do you have an on/off button on the laptop for wireless? I've heard of problems with it working and some have had to change a setting in a config file to turn it on. 

The reason I ask is because there'e something missing. It should have a line like this in it. 

bus info: pci@03:00.0

It's recognized and has a driver assigned (configuration:) line tells this but besides the disabled part it should have the above businfo number.

If you have problems start a new thread with a subject of turning internal wireless on to see if anyone can help.

---

### Post by apix on 2005-12-11
@tonysathre :Iwill try what you said.
@Lambert : there is no on/off button. If the action that tony suggested fails, then i will make that new thread.

Thanks guys.. :)

---

