---
title: "[SOLVED] Acer Aspire One Wireless"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by Coder543 on 2008-12-24
Greetings, I have a newly acquired Acer Aspire One, the wireless on it after following the tutorial on the website appears now to be working. However, the wireless module does not seem to want to connect to protected wireless networks. What should I do?

followed:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

search for "wireless broken" to find what I followed.

The AAO is running latest 8.10.

This is the output from lspci -v

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 58480000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 60c0 [size=8]
    Memory at 40000000 (32-bit, prefetchable) [size=256M]
    Memory at 58500000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0
    Memory at 58400000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 58540000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 57300000-583fffff
    Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: 56300000-572fffff
    Prefetchable memory behind bridge: 0000000051000000-00000000520fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 55200000-562fffff
    Prefetchable memory behind bridge: 0000000052100000-00000000530fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 54100000-551fffff
    Prefetchable memory behind bridge: 0000000053100000-00000000540fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 6080 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 6060 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 6040 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 6020 [size=32]
    Kernel driver in use: uhci_hcd
    Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 58544400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd
    Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-rng, iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 60a0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix
    Kernel modules: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: medium devsel, IRQ 11
    I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 219
    I/O ports at 3000 [size=256]
    Memory at 51010000 (64-bit, prefetchable) [size=4K]
    Memory at 51000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 51020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Device e008
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 55200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k_pci
    Kernel modules: ath_pci, ath5k

```

---

### Post by Coder543 on 2008-12-24
:( It would appear that Ubuntu has completely stopped finding wireless networks on my AA1. PLEASE HELP ME!!!! :confused:

---

### Post by luks911 on 2008-12-24
You could try with madwifi instead ath5k.

```
echo "blacklist ath5k" | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get update && sudo aptitude install build-essential gcc binutils autoconf automake
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz
tar xzf madwifi-hal-0.10.5.6-r3879-20081204.tar.gz
cd madwifi-hal-0.10.5.6-r3879-20081204.tar.gz
make
sudo make install
sudo modprobe -a ath_pci wlan_scan_sta
sudo ifconfig ath0 up
echo "ath_pci" | sudo tee -a /etc/modules

```

If after this you still have problems finding networks, you can install Wicd instead of Network-manager:
Go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the f
following line: 
```
deb http://apt.wicd.net intrepid extras 
```
You'll also need to add the key used for signing Wicd:
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add - 
```
Then clik Reload in Synaptic, search for Wicd and install it.

---

### Post by Coder543 on 2008-12-25
Ok, so I apparently had flipped the wireless switch on my aspire one and could then see networks again (but still not connect to protected networks) so I executed the commands I was given. When it was complete I rebooted and could not see a wireless networks option in the gnome network manager applet so I installed Wicd and the wicd tray applet had not been installed so I reverted back to the gnome network manager. Any further ideas?

---

### Post by Coder543 on 2008-12-25
Thank you for the help, however my dad had accidentally not entered my mac address onto the filter for the network I was attempting to connect to. It works!!!!!

---

