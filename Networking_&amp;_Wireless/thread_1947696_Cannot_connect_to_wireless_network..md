---
title: "Cannot connect to wireless network."
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by lastsexygeek on 2012-03-27
i had recently installed ubuntu on both my laptop and desktop,my acer aspire 5738g laptop is working awesome with ubuntu and can connect to D-link d24 wireless router but the problem is with my desktop computer. It is unable to detect d-link dwa 123 usb dongle and even flash drives. Am very disappointed with this because i've to do several job on my desktop. Please assist me!!:confused:
on using dmesg | tail -n 20 command i found this:[ 1320.772245]  [<c13e87af>] usb_disable_interface+0x3f/0x50
[ 1320.772258]  [<c13ea8e4>] usb_unbind_interface+0x134/0x140
[ 1320.772268]  [<c13614cb>] __device_release_driver+0x5b/0xb0
[ 1320.772276]  [<c1361544>] device_release_driver+0x24/0x40
[ 1320.772284]  [<c13610ba>] bus_remove_device+0x5a/0x80
[ 1320.772291]  [<c135edd7>] device_del+0xe7/0x150
[ 1320.772300]  [<c13e8851>] usb_disable_device+0x91/0x1a0
[ 1320.772308]  [<c13e24da>] usb_disconnect+0x9a/0x120
[ 1320.772316]  [<c13e25af>] hub_quiesce+0x4f/0x90
[ 1320.772324]  [<c13e3741>] hub_events+0x21/0x550
[ 1320.772331]  [<c102df58>] ? default_spin_lock_flags+0x8/0x10
[ 1320.772340]  [<c106f87d>] ? finish_wait+0x4d/0x70
[ 1320.772348]  [<c13e3c70>] ? hub_events+0x550/0x550
[ 1320.772355]  [<c13e3c95>] hub_thread+0x25/0x140
[ 1320.772363]  [<c106f780>] ? add_wait_queue+0x50/0x50
[ 1320.772371]  [<c106ef7d>] kthread+0x6d/0x80
[ 1320.772380]  [<c106ef10>] ? flush_kthread_worker+0x80/0x80
[ 1320.772389]  [<c15650be>] kernel_thread_helper+0x6/0x10
[ 2553.763981] autorun.exe: sending ioctl 5305 to a partition!
[ 2553.763992] autorun.exe: sending ioctl 5305 to a partition!

on using lsusb command i found this:

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0c45:6340 Microdia


on using lspci command i found this:

00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB7x0 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc 760G [Radeon 3000]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

---

