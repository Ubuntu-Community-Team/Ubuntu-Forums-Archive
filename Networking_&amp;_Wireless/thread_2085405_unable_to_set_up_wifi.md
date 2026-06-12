---
title: "unable to set up wifi"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by siddharthchauhan44 on 2012-11-18
hi 
 i have been using ubuntu since a month 
ubuntu 12.04 lts 
i am facing a little problem with the wifi connectivity
wen i plug in my ethernet wire it connects by itself but wen i unplug it 
my laptop does not detect any wireless network 
laptop : dell ispiron 15 r 
wifi router :netgear WGR614V10

plz resolve this problem a.s.a.p

---

### Post by amahi on 2012-11-18
ok.what is output

```
sudo lshw -c network
```

and

```
iwconfig
```

> iwlist scan

---

### Post by siddharthchauhan44 on 2012-11-18
sudo lshw -c network

siddharth@siddharth-Inspiron-5520:~$ sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 05
       serial: d4:be:d9:28:c8:3e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
resources: irq:43 ioport:2000(size=256) memory:c1404000-c1404fff memory:c1400000-c1403fff
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c1500000-c1507fff

---

### Post by siddharthchauhan44 on 2012-11-18
siddharth@siddharth-Inspiron-5520:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by siddharthchauhan44 on 2012-11-18
siddharth@siddharth-Inspiron-5520:~$ iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by siddharthchauhan44 on 2012-11-18
can anyone help??

---

### Post by siddharthchauhan44 on 2012-11-18
no wireless connection 
laptop unable to scan for wireless networks 
ethernet auto connected 
laptop:dell inspiron 5525
wifi router :WGR64V10

---

### Post by westie457 on 2012-11-18
> *-network UNCLAIMED
description: Network controller
product: Broadcom Corporation
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:08:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory:c1500000-c1507fff

Cannot see any drivers loaded or installed.
Please post the output of ```
lspci -vnn
```
Select all the output then copy & paste into a new reply, then highlight what you pasted in and click on the # symbol at the top of the message area. This will place [code] brackets around it and make things easier to read.

Thank you

---

### Post by siddharthchauhan44 on 2012-11-18
```
siddharth@siddharth-Inspiron-5520:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)
    Subsystem: Dell Device [1028:056a]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:01.0 PCI bridge [0604]: Intel Corporation Ivy Bridge PCI Express Root Port [8086:0151] (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=06, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: c0000000-c0ffffff
    Prefetchable memory behind bridge: 00000000a0000000-00000000afffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:056a]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at c1000000 (64-bit, non-prefetchable) [size=4M]
    Memory at b0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: Dell Device [1028:056a]
    Flags: bus master, medium devsel, latency 0, IRQ 42
    Memory at c1600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Dell Device [1028:056a]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at c1614000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:056a]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at c1619000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Dell Device [1028:056a]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at c1610000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Prefetchable memory behind bridge: 00000000c1400000-00000000c14fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 2 [8086:1e12] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
    Memory behind bridge: c1500000-c15fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Dell Device [1028:056a]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at c1618000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e57] (rev 04)
    Subsystem: Dell Device [1028:056a]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Dell Device [1028:056a]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 41
    I/O ports at 4088 [size=8]
    I/O ports at 4094 [size=4]
    I/O ports at 4080 [size=8]
    I/O ports at 4090 [size=4]
    I/O ports at 4060 [size=32]
    Memory at c1617000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Dell Device [1028:056a]
    Flags: medium devsel, IRQ 10
    Memory at c1615000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 4040 [size=32]
    Kernel modules: i2c-i801

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Thames XT/GL [Radeon HD 7600M Series] [1002:6840] (prog-if 00 [VGA controller])
    Subsystem: Dell Device [1028:056a]
    Flags: fast devsel, IRQ 7
    Memory at a0000000 (64-bit, prefetchable) [disabled] [size=256M]
    Memory at c0000000 (64-bit, non-prefetchable) [disabled] [size=128K]
    I/O ports at 3000 [disabled] [size=256]
    Expansion ROM at c0020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel modules: radeon

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:056a]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    I/O ports at 2000 [size=256]
    Memory at c1404000 (64-bit, prefetchable) [size=4K]
    Memory at c1400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

08:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4365] (rev 01)
    Subsystem: Dell Device [1028:0016]
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at c1500000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>


```

---

### Post by westie457 on 2012-11-18
Congratulations, you have an unsupported device. All is not lost though. Clicking on this link will download the driver for you.

[http://ubuntuone.com/0bB9zdFZW9TK9m0PWITKBz](http://ubuntuone.com/0bB9zdFZW9TK9m0PWITKBz)

Once that is done go to here for the instructions on how to install. Do not worry that this is for a Dell Vostro, the important part is that this is for the same chip.

[http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560](http://askubuntu.com/questions/175104/how-do-i-install-bcm43142-wireless-drivers-for-dell-vostro-3460-3560)

Report back here with the news.

Thank you

---

### Post by coffeecat on 2012-11-18
Threads merged. Please do not start new threads for the same issue.

---

### Post by siddharthchauhan44 on 2012-11-18
```
@westie
problem still not resolved
i applied the sudo commands both of them but wen i was 
applying 

siddharth@siddharth-Inspiron-5520:~$ sudo dpkg -i
dpkg: error: --install needs at least one package archive file argument

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
siddharth@siddharth-Inspiron-5520:~$ 


```

pls see the screenshot

---

### Post by westie457 on 2012-11-18
Progress of some kind.

Open a terminal and run ```
sudo apt-get remove bcmwl-kernel-source
``` do not reboot yet.

Still in the terminal navigate to where you downloaded the file (make sure there is only one in there and that one must match the architecture of your machine - eg x64)
I am guessing ```
cd ~/Downloads
```

Then run ```
sudo dpkg -i *.deb
```

Wait about 5 minutes for things to settle and see if your wireless comes up. If nothing then reboot and check again remembering to remove the cable.

Thank you

---

### Post by siddharthchauhan44 on 2012-11-18
@westie
u r a dude 
thanx a lot 
finally wifi iz working

---

