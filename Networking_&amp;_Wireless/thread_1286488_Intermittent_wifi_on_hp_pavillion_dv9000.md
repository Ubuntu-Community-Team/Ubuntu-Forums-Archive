---
title: "Intermittent wifi on hp pavillion dv9000"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by cespinal on 2009-10-09
I have been trying to find a solution for this, but it seems there are specific possible causes for this common issue...

I have an HP dv9000, Broadcom wireless card has not showed any issue since I installed Jaunty, however, my wifi connectivity has turned jumpy a couple of weeks ago. Network manager shows me full signal, wifi switch is blue lit as it should, in fact, I can browse the web with relatively no problems, but Im am not able to use any apps needing for constant data transfer such as Thunderbird, Deluge, Pidgin, etc.

System monitor shows me 60 second long peaks, followed by other 60 seconds of no data transfer, then within a couple of minutes, data transfer just shows as short peaks every 30 seconds or so.

At first, I suspected my wifi network at home was becoming faulty, but I have been able to use more networks over the last couple of days just to see the problems persists.

lspci shows me this.... I hope tou can help me find the way trough this. Thank you as always!.

Code: Select all
    00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
    00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
    00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
    00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
    00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
    00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
    00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
    00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
    00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
    00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
    00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
    00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
    00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
    00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
    00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
    00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
    00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
    00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
    00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
    00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
    02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
    02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
    03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)



Adding dmesg output:

[code[ 4921.001017] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[ 4923.184442] forcedeth 0000:00:0a.0: irq 2300 for MSI/MSI-X
[ 4923.184668] eth0: no link during initialization.
[ 4923.185189] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 4924.168038] eth1: no IPv6 routers present
[ 4927.485287] VFS: busy inodes on changed media or resized disk sr0
[ 4927.643101] VFS: busy inodes on changed media or resized disk sr0
[ 4927.909209] VFS: busy inodes on changed media or resized disk sr0
[ 4928.206046] VFS: busy inodes on changed media or resized disk sr0
[ 4928.333309] VFS: busy inodes on changed media or resized disk sr0
[ 4928.502860] VFS: busy inodes on changed media or resized disk sr0
[ 4928.651353] VFS: busy inodes on changed media or resized disk sr0
[ 4928.778569] VFS: busy inodes on changed media or resized disk sr0
[ 4928.948260] VFS: busy inodes on changed media or resized disk sr0
[ 4932.786330] VFS: busy inodes on changed media or resized disk sr0
[ 4932.913474] VFS: busy inodes on changed media or resized disk sr0
[ 4934.666815] VFS: busy inodes on changed media or resized disk sr0
[ 6491.624047] CE: hpet increasing min_delta_ns to 22500 nsec
][/code]

---

### Post by kreggz on 2009-10-10
run a ping over an hour and see how many packets you lose

---

### Post by cespinal on 2009-10-11
how do I do that? :P

---

### Post by kreggz on 2009-10-11
Open a terminal session and type:

ping google.com

let it go for an hour and then stop it by pressing control c. it will tell you how much packet loss you experienced.

---

### Post by darthfruitloop on 2009-11-23
This happened to me a while back, I fixed it by plugging it in to a wired connection, and then from there go to your synaptic and reinstall your network manager :)

---

