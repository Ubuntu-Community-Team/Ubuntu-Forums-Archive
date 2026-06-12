---
title: "Cant connect to my LAN"
date: 2013-02-01
forum: Networking &amp; Wireless
---

### Post by rveroo on 2013-02-01
Hi sort of new to linux been messing around with it for a while on my old pc, but i have been trying to install it on my new gaming computer to boot along side windows 7 and 8(just a note i can connect to my router fine in windows. im using a wierd connection by the way. as far as i can tell its some sort of firmware problem. i have also done a reinstall of ubuntu and have tried 3 other distros by booting of a live cd. those being: puppy, arch and zorin. just wondering if any one has any idea why im using a Gigabyte GA-z77-DH3 as my mother bored which has a Atheros GbE LAN chip. thanks for any help in advance.

---

### Post by praseodym on 2013-02-01
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of the commands:
```

uname -a
lspci -nnk
cat /etc/network/interfaces
```

---

### Post by rveroo on 2013-02-01
ok 

```
uname -a
Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
brandon@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller [8086:0150] (rev 09)
	Subsystem: Giga-byte Technology Device [1458:5000]
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port [8086:0151] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
	Subsystem: Giga-byte Technology Device [1458:5007]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
	Subsystem: Giga-byte Technology Device [1458:1c3a]
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
	Subsystem: Giga-byte Technology Device [1458:5006]
	Kernel driver in use: ehci_hcd
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.5 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c4)
00:1c.6 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 7 [8086:1e1c] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.7 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 8 [8086:1e1e] (rev c4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
	Subsystem: Giga-byte Technology Device [1458:5006]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation Z77 Express Chipset LPC Controller [8086:1e44] (rev 04)
	Subsystem: Giga-byte Technology Device [1458:5001]
	Kernel modules: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e02] (rev 04)
	Subsystem: Giga-byte Technology Device [1458:b005]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
	Subsystem: Giga-byte Technology Device [1458:5001]
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK104 [GeForce GTX 670] [10de:1189] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:2670]
	Kernel driver in use: nouveau
	Kernel modules: nouveau, nvidiafb
01:00.1 Audio device [0403]: NVIDIA Corporation GK104 HDMI Audio Controller [10de:0e0a] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:2670]
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd-hda-intel
03:00.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 41)
04:00.0 Multimedia audio controller [0401]: C-Media Electronics Inc CMI8788 [Oxygen HD Audio] [13f6:8788]
	Subsystem: ASUSTeK Computer Inc. CMI8786 (Xonar DG) [1043:8467]
	Kernel driver in use: snd_oxygen
	Kernel modules: snd-oxygen
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
	Subsystem: Giga-byte Technology Device [1458:e000]
06:00.0 USB controller [0c03]: Etron Technology, Inc. EJ168 USB 3.0 Host Controller [1b6f:7023] (rev 01)
	Subsystem: Giga-byte Technology Device [1458:5007]
	Kernel driver in use: xhci_hcd
brandon@ubuntu:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

---

### Post by praseodym on 2013-02-01
Download these packages:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.23.29_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.23.29_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-23-generic_3.5.0-23.35_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-23-generic_3.5.0-23.35_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23_3.5.0-23.35_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23_3.5.0-23.35_all.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.5.0.23.29_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.5.0.23.29_amd64.deb)

Save them in Downloads and install via:

```
sudo dpkg -i ~/Downloads/*.deb
```
Reboot and check the connection. If it works install these packages afterwards:

```
sudo apt-get install build-essential dkms
```

---

### Post by rveroo on 2013-02-01
Ok that worked for the lan problem but now i have no usb driver support all usb diveces are dead in ubuntu. e.g. lights turn on on keyboard but cant turn caps lock on. same with mouse had to get out a old keyboard with a old input to try the second command give me a error something like cannot find package build-essential and cannot find package dkms

---

### Post by praseodym on 2013-02-01
Obviously still no connection. Check:

```
sudo modprobe -v alx
```

---

### Post by Yellow Pasque on 2013-02-03
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782)

---

