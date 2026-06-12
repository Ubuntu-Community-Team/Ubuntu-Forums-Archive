---
title: "can't install Dapper, 8139 NIC not detected???"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by cirellinux on 2006-07-01
I've downloaded and burnt the DD606-server (20060531) iso, wanting to give a try to the LAMP installer.
I've installed and  run a Hoary, then a Breezy, on the same machine where i'm not able to install Dapper!
The installer can't detect a Ethernet network card.
It give me a list of network drivers to choose from, I take 8139too (as in Hoary and Breezy) with the same deadlock.
The installer give me a chance to get a console. I type:
```
~ # lspci | grep Eth
0000:05:06.0 Ethernet controller Realtek Semiconductors Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```
to see if the card is in the hardware list. Then
```
~ # lsmod | grep 8139
8139too    26880 0
8139cp     22528 0
mii           5888 2 8139too,8139cp

```
To find what's happening I typed dmesg and these are the lines I don't understand, somehow strange:
```

...
[] ohci_hcd 0000:00:02.0: init 0000:00:02.0 failed, -16
[] ohci_hcd probe of 0000:00:02.0: failed with error  -16
[] **** SET: misaligned resource pointer: c210b0c2 Type 07 Len 0
...
[] ehci_hcd 0000:00:02.1: init 0000:00:02.1 failed, -16
[] ehci_hcd probe of 0000:00:02.1: failed with error  -16
...
[] ohci1394 $Rev: 1313 $ Ben Collins <bcollins@debian.org>
[] **** SET: misaligned resource pointer: c22069c2 Type 07 Len 0
...
[] ohci1394 fw-host0: Unexpected PCI resource length of 0!
[] ohci1394 MMIO resource (0x0 - 0x800) unavailable
[] ohci1394 probe of 0000:05:0b.0: failed with error  -12
...
```

When asked to give parameter to improve CDROM performance, via hdparm, I left the empty string.
The dmsg:
```
[] ide-cd: cmd 0x28 timed out
[] hda: DMA interrupt recovery
[] hda: lost interrupt
[] hda: DMA disabled
[] hda: dma error: status=0x58 { DriveReady SeekComplete DataRequest }
[] ide: failed opcode was: unknown
```

Requested to add more installer components, i choose only the "rescue-mode" and continue.
It's time to detect the network card: the installer starts and after a while it says something like: "No Ethernet card was detected, but there is a Firewire Interface. Do you want to use it?"
and give me to a list of network drivers to choose from. Since there's the 8139too, i choose that.
But again the same question, and the same list: I exit the loop giving "no card installed".
dmesg:
```
[] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22 2004)
[] 8139cp: pci dev 0000:05:06.0 (id 10ec:8139 rev  10) is not an 8139C+ compatible chip
[] 8139cp: try the "8139too" driver instead.
[] 8139too: Fast Ethernet driver 0.9.27
[] ACPI: PCI Interrupt 0000:05:06.0[A] -> Link [LNK1] -> GSI 3 (level, low) -> IRQ 3
[] 8139too: 0000:05.06.0: region #1 not an MMIO resource, aborting.

```

So i cannot terminate the install process.

Some hints?
Thank you in advance 

Stefano

---

### Post by mips on 2006-07-02
Stefano,

Sorry, do a search for '8139' here as there are known problems with that chipset.

Maybe you can install a spare adapter in the machine then do the install, afterwards fix the problem and then remove the card.

---

### Post by cirellinux on 2006-07-03
[QUOTE=mips]Stefano,

Sorry, do a search for '8139' here as there are known problems with that chipset.

Maybe you can install a spare adapter in the machine then do the install, afterwards fix the problem and then remove the card.[/QUOTE]

Thank you for answering.
I've tried to search thru the forum, but it seems to me that all pothe sts about 8139 or other eth cards were about malfunctioning AFTER the install process.
Anyway, I have another nic, a usb D-Link one. The chipset seems to be te same...
Again no boot.
I give another try choosing the 'dummy' card, just to go on with the install process, but
this time the problem is with "Partitioning Disks": it start the task, then it stalls. Control-C to stop.

So i decided to go thru the breezy_2_dapper dist-upgrade process, I give up with LAMP server install.
The Breezy installer detect the pci-ethernet card and the usb one. no problems when partitioning.
Now I'm dist-upgrading. 
Thank you again for your advice.

Stefano

---

### Post by el3ktro on 2006-08-26
> **mips said:**
> Stefano,

Sorry, do a search for '8139' here as there are known problems with that chipset.

Maybe you can install a spare adapter in the machine then do the install, afterwards fix the problem and then remove the card.

Hello I have a similar problem. Trying to install Ubuntu 6.06.1 on a Centrino notebook. It first loads the 8139cp module, which says the chipset is not compatible and that the 8139too module should be tried. The Desktop CD load this other module, but then it hangs and I can't install Dapper! Is there a way to tell the Desktop CD or the Alternate CD to load ONLY the 8139too module or no module at all?

---

