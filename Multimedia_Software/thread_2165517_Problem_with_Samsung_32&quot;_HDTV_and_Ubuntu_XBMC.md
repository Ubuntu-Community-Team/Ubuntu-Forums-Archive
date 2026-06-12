---
title: "Problem with Samsung 32&quot; HDTV and Ubuntu XBMC server (Mode Not Supported)"
date: 2013-08-05
forum: Multimedia Software
---

### Post by Panagiotis_Atmatzidis on 2013-08-05
Hello,

I have a 32" Samsung HD-ready TV along with a Giada islim-30 (HTPC) running an Ubuntu variant (XBMCbuntu) which launched XBMC by default. When I use my VGA monitor everything works fine. When I use the samsung HDMI I see a signal saying "**Mode Not Supported**". According to Samsung this happens when the device sends 480i instead of 480p and so forth.

I can access the machine via SSH so here are some machine specs:
```

atma@giada:~$ sudo lshw -C display; lsb_release -a; uname -a; sudo dmidecode -t 1
  *-display:0             
       description: VGA compatible controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:fe880000-fe8fffff ioport:dc00(size=8) memory:d0000000-dfffffff memory:fe900000-fe9fffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fe780000-fe7fffff
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10 - XBMCbuntu
Release:	12.10
Codename:	quantal
Linux giada 3.5.0-37-generic #58-Ubuntu SMP Mon Jul 8 22:10:28 UTC 2013 i686 i686 i686 GNU/Linux
# dmidecode 2.11
SMBIOS 2.6 present.


Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: To Be Filled By O.E.M.
	Product Name: To Be Filled By O.E.M.
	Version: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	UUID: 03000200-0400-0500-0006-000700080009
	Wake-up Type: Power Switch
	SKU Number: To Be Filled By O.E.M.
	Family: To Be Filled By O.E.M.
atma@giada:~$ lspci
00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```

Thing is, I'm not sure where to start. Some threads say edit xorg.conf but I'm not familiar with Ubuntu and I'm not sure how to proceed. Any hints would be welcomed.

Best Regards,

---

### Post by sioxs on 2013-08-06
This might be as simple as making sure XBMC Video setting are correct.
check to see if your refresh rate is right for the external LCD TV monitors this could be around the 60Hz range upto 120Hz depending on your TV. Check your TV's manual to find the correct settings before making changes.

PS. I had a similar error "Mode Not Supported" with a new Olivia LCD TV and it was the refresh rate settings within XBMC  that changed.
HOME > System > System > Video and change the refresh rate there and also check the default video device list for your output source it may need to be switched from your desktop monitor to the TV so it renders the correct resolution.

Hope that helps
sioxs

---

