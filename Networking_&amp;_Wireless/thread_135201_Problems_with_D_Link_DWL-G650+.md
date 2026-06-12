---
title: "Problems with D Link DWL-G650+"
date: 2006-02-23
forum: Networking &amp; Wireless
---

### Post by loki on 2006-02-23
I have a Toshiba A60 laptop & D link DWL G650+ (not the 650+ or the G650) pcmcia card (ubuntu 5.10). Since installed the card it has never worked (does in XP so isn't HW related), not even the power light activates when its plugged in. 

After researching the card I read that I needed to update the madwifi drivers which is what I did. I have followed the HowTo down to the letter but when I came to do the wlanconfig command I just get the message wlanconfig: ioctl: No such device. (this is the same after a reboot too). 

At this point I wondered if it was a problem with pcmcia itself but then other PCMCIA storage cards I have work fine. Also after running cardctl status it does report the the card is inserted and ready. I have tried adding map eth0 and map wifi0 in the network/interfaces file but with no change.

I have also tried using NDISWRAPPER but this also does not detect any hardware.

See below the responce from 'sudo lshw -C network' & 'lspci -v | grep -A 4 Eth'

  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:da:d5:13
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 1                                                              00bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driververs                                                              ion=0.9.27 duplex=full ip=192.168.10.5 link=yes multicast=yes port=MII speed=100                                                              MB/s
       resources: ioport:a000-a0ff iomemory:d0008000-d00080ff irq:18
andrew@odin:~$ lspci -v | grep -A 4 Eth
0000:02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C                                                              /8139C+ (rev 10)
        Subsystem: Toshiba America Info Systems: Unknown device ff10
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at a000 [size=256]
        Memory at d0008000 (32-bit, non-prefetchable) [size=256]


Any help or ideas would be greatly appriciated.

---

### Post by Lambert on 2006-02-23
Ok, try this.

we're going to add a boot option. OPen terminal and add this to the kernel you boot.

```
sudo gedit /boot/grub/menu.lst
```

If you use kubuntu replace gedit with kedit.

Page down until you see the section with the kernl you boot into. at the end of the kernel boot line add this phrase.

```
pci=assign-busses
```

Save the file then reboot. Rerun the lshw command to see if you can see your card now.

---

### Post by loki on 2006-02-23
Thanks Lambert,

Results of lshw

  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@02:07.0
       logical name: eth0
       version: 10
       serial: 00:a0:d1:da:d5:13
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=8139too driverversion=0.9.27 duplex=full ip=192.168.10.5 link=yes multicast=yes port=MII speed=100MB/s
       resources: ioport:a000-a0ff iomemory:d0008000-d00080ff irq:18
  *-network DISABLED
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 3
       bus info: pci@03:00.0
       logical name: wlan0
       version: 00
       serial: 00:11:95:15:07:7f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci multicast=yes wireless=IEEE 802.11b+/g+
       resources: iomemory:c820000-c821fff iomemory:c800000-c81ffff irq:19


Seems a little more promising....

---

### Post by Lambert on 2006-02-23
So you have a TI acx chipset and you need the acx111 driver. It's installed with breezy and if you notice the configuration line, it's bound to the device and probably loaded. You can check with 

lsmod | grep acx

You do need firmware though to get it working. See this link and the breezy section.

[http://doc.gwos.org/index.php/ACXDriver](http://doc.gwos.org/index.php/ACXDriver)

---

### Post by loki on 2006-02-26
Nice one for that.

Managed to sort it at last, I also had to follow the last section of HouseofCraigs instructions but it has worked.

I still have to run the start_net script to activate the card tho. I can cope with this for now tho :).

---

### Post by bako on 2006-02-26
I've used that card in fedora4 with ndiswrapper and winxp driver and worked!
but now i don't remind me what i have done.

---

### Post by Lambert on 2006-02-26
You just need to follow instructions for ndiswrapper

[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper)

Depending on the chipset, make sure the native linux driver doesn't load if there is one.
If you have a TI chipset then you would open the /etc/hotplug/blacklist file and add a line like this.

blacklist acx

where acx=the driver name

---

