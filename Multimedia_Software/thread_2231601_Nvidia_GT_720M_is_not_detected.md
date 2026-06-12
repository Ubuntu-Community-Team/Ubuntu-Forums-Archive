---
title: "Nvidia GT 720M is not detected"
date: 2014-06-26
forum: Multimedia Software
---

### Post by waffen on 2014-06-26
Hello,
I have a Lenovo Ideapad S410p with Nvidia Gt 720M with Optimus activate. I already install the nvidia-331 driver from officials repos and Bumblebee but my nvidia card is no loaded.

```
mario@mario-IdeaPad-S410p:~$ lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
	Subsystem: Lenovo Device 3978
	Kernel driver in use: i915
```

The card is present in the system:

```
mario@mario-IdeaPad-S410p:~$ lspci -k
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
	Subsystem: Lenovo Device 3978
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
	Subsystem: Lenovo Device 3978
	Kernel driver in use: i915
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
	Subsystem: Lenovo Device 3978
	Kernel driver in use: snd_hda_intel
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
	Subsystem: Lenovo Device 3978
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
	Subsystem: Lenovo Device 3978
	Kernel driver in use: mei_me
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
	Subsystem: Lenovo Device 3978
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
	Kernel driver in use: pcieport
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
	Kernel driver in use: pcieport
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
	Kernel driver in use: pcieport
00:1c.4 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 5 (rev e4)
	Kernel driver in use: pcieport
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
	Subsystem: Lenovo Device 3978
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
	Subsystem: Lenovo Device 3978
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
	Subsystem: Lenovo Device 3978
	Kernel driver in use: ahci
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
	Subsystem: Lenovo Device 3978
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
	Subsystem: Lenovo Device 3026
	Kernel driver in use: ath9k
03:00.0 Ethernet controller: Qualcomm Atheros QCA8172 Fast Ethernet (rev 10)
	Subsystem: Lenovo Device 3807
	Kernel driver in use: alx
04:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev ff)

```

```

mario@mario-IdeaPad-S410p:~$ sudo lshw -C display
[sudo] password for mario: 
  *-display               
       descripción: VGA compatible controller
       producto: Haswell-ULT Integrated Graphics Controller
       fabricante: Intel Corporation
       id físico: 2
       información del bus: pci@0000:00:02.0
       versión: 09
       anchura: 64 bits
       reloj: 33MHz
       capacidades: msi pm vga_controller bus_master cap_list rom
       configuración: driver=i915 latency=0
       recursos: irq:59 memoria:f3000000-f33fffff memoria:d0000000-dfffffff ioport:5000(size=64)

```

What can I do?

---

### Post by trivietnam on 2014-07-07
I also have s410p (G710M) +ubuntu-14.04 and it works well

I cannot remmember exactly what's I've done. Just remember vaguely as follows

```

$ sudo apt-get install nvidia-331 nvidia-settings bumblebee bumblebee-nvidia primus
$ sudo apt-get --reinstall install xserver-xorg-core xserver-xorg-video-intel
$ sudo dpkg-reconfigure xserver-xorg[COLOR=#545454][FONT=Sans]
[/FONT][/COLOR]
```

reboot and test with

```

$ sudo service bumblebeed start
$ glxinfo | grep -i vendor
$ primusrun glxinfo | grep -i vendor

```

---

### Post by waffen on 2014-07-07
HI,

thanks for the answer! I can manage the problem with a clean reinstall for the hole Ubuntu :( after that all works fine again.

---

