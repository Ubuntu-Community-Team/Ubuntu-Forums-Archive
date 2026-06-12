---
title: "Network card not working: Address space collision ?!"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by misja on 2010-01-25
I have problems with a network card that I just bought: An Intel Pro 1000 T gigabit NIC.
After installing it into a PCI slot my OS (Ubuntu 9.10) did not create any network connection for it.
ifconfig showed only my onboard nic; lspci does list it however (see the output below).

I verified that I didn't need any drivers by putting the NIC into another pc with the same OS on it: There it worked right out of the box.

I also tried disabling my onboard NIC in the BIOS, I upgraded my motherboard (Asus M2N68-AM PLUS) with the latest BIOS version, but all to no avail.

I did find an error message in dmesg which I think points at the reason why the NIC is not working: Apparently an address space collision.

But now I'm wondering how I can fix this problem?

Here's my lspci output for the Intel NIC:

01:07.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev ff)

And here are the errors in dmesg:

[ 0.316134] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *11
[ 0.316306] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *11
[ 0.316507] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[ 0.316638] SCSI subsystem initialized
[ 0.316685] libata version 3.00 loaded.
[ 0.316685] usbcore: registered new interface driver usbfs
[ 0.316685] usbcore: registered new interface driver hub
[ 0.316685] usbcore: registered new device driver usb
[ 0.316685] ACPI: WMI: Mapper loaded
[ 0.316685] PCI: Using ACPI for IRQ routing
[ 0.316685] pci 0000:01:07.0: BAR 1: address space collision on of device [0xfc0000-0xfdffff]
[ 0.316685] pci 0000:01:07.0: BAR 1: can't allocate resource
[ 0.340024] Bluetooth: Core ver 2.15
[ 0.340066] NET: Registered protocol family 31
[ 0.340066] Bluetooth: HCI device and connection manager initialized
[ 0.340066] Bluetooth: HCI socket layer initialized
[ 0.340066] NetLabel: Initializing
[ 0.340066] NetLabel: domain hash size = 128
[ 0.340066] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.340066] NetLabel: unlabeled traffic allowed by default
[ 0.340180] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
--
[ 0.384971] system 00:09: ioport range 0x290-0x29f has been reserved
[ 0.384973] system 00:09: ioport range 0xa00-0xa0f has been reserved
[ 0.384976] system 00:09: ioport range 0xa10-0xa1f has been reserved
[ 0.384980] system 00:0b: iomem range 0xe0000000-0xefffffff has been reserved
[ 0.384983] system 00:0c: iomem range 0x0-0x9ffff could not be reserved
[ 0.384985] system 00:0c: iomem range 0xc0000-0xcffff has been reserved
[ 0.384987] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[ 0.384989] system 00:0c: iomem range 0x100000-0x6fffffff could not be reserved
[ 0.384991] system 00:0c: iomem range 0xfed45000-0xffffffff could not be reserved
[ 0.389626] AppArmor: AppArmor Filesystem Enabled
[ 0.389637] pci 0000:01:07.0: BAR 6: address space collision on of device [0xfa0000-0xfbffff]
[ 0.389654] pci 0000:01:07.0: BAR 1: error updating (0xdff00000 != 0xf00000)
[ 0.389657] pci 0000:00:04.0: PCI bridge, secondary bus 0000:01
[ 0.389659] pci 0000:00:04.0: IO window: 0xe000-0xefff
[ 0.389661] pci 0000:00:04.0: MEM window: 0xdff00000-0xdfffffff
[ 0.389664] pci 0000:00:04.0: PREFETCH window: 0x80000000-0x800fffff
[ 0.389667] pci 0000:00:09.0: PCI bridge, secondary bus 0000:02
[ 0.389668] pci 0000:00:09.0: IO window: disabled
[ 0.389670] pci 0000:00:09.0: MEM window: disabled
[ 0.389672] pci 0000:00:09.0: PREFETCH window: disabled

---

### Post by chili555 on 2010-01-25
I don't see a solution yet, but please see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/424142](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/424142) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/413419](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/413419)

There are suggestions in both of these that the latest kernel fixed the issue. Are you running the latest kernel, in my case, 2.6.31-17-generic?

---

### Post by misja on 2010-01-25
*Are you running the latest kernel, in my case, 2.6.31-17-generic?*

I'm even using 2.6.31-18-generic :D

I tried lspci again, this time with the -v option. This gave some new interesting output:
01:07.0 Ethernet controller: Intel Corporation 82541PI Gigabit Ethernet Controller (rev ff) (prog-if ff)
	!!! Unknown header type 7f
	Kernel modules: e1000

I don't know what this Unknown header type stuff means but it doesn't sound good ... I did some searching on Google and found some posts where the solution was to install a new driver.
So I downloaded the latest driver from Intel's site and followed their instructions, but no success.
I verified with modinfo e1000 that the latest driver was installed and it was.
So still no entry in ifconfig showing my second Nic, also dmesg still shows the address collision errors :(

---

