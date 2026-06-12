---
title: "DGE-530T not detected under Dapper"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by velk on 2006-06-03
I have been using breezy for a while now without problems - the cd install detected the 530T and it worked fine from there.  Reinstalling on the same hardware, a clean install of dapper did not detect the card. It's an nforce2 motherboard, with onboard NIC, which is detected correctly. Disabling the onboard NIC makes no difference in the 530T being detected.

From the look of dmesg, it's trying to use the sky2 module to load the card, which isn't working :

sky2 0000:01:07.0: unsupported chip type 0xb1
sky: probe of  0000:01:07.0 failed with error -95

Loading either the skge module or the sk98lin module or both does nothing - no output in dmesg from either of them and neither of them create the expected eth1 interface.

lspci shows 

0000:01:07.0 Ethernet controller: D-Link System Inc: Unknown device 4b01 (rev 11)

Any suggestions on getting it going ? From what I can see, the device ID is hardcoded in the sky2.c source, which may be a mistake, although I am leery of manually editing the driver source.

---

### Post by thulsadoom on 2006-06-04
I have exactly the same problem and i haven't been able to find an answer (after endless googling). The card worked fine in breezy with the sk98lin driver.

Anyone else?

---

### Post by velk on 2006-06-05
Ok I have resolved this problem. It appears that the kernel included with dapper does not work for any DGE-530 revision, as a developer has inadverdantly moved the device IDs for these cards out of the SKGE driver and into the SKY2 driver.

I resolved it by cutting the D-Link 530T device id lines (0x4b00 and 0x4b01) out of SKY2's pci ID table and moving them into SKGE's pci ID table and then compiling and installing those modules.

static const struct pci_device_id sky2_id_table[] = {
 	{ PCI_DEVICE(PCI_VENDOR_ID_SYSKONNECT, 0x9000) },
 	{ PCI_DEVICE(PCI_VENDOR_ID_SYSKONNECT, 0x9E00) },
-	{ PCI_DEVICE(PCI_VENDOR_ID_DLINK, 0x4b00) },
-	{ PCI_DEVICE(PCI_VENDOR_ID_DLINK, 0x4b01) },
 	{ PCI_DEVICE(PCI_VENDOR_ID_MARVELL, 0x4340) },


static const struct pci_device_id skge_id_table[] = {
 	{ PCI_DEVICE(PCI_VENDOR_ID_SYSKONNECT, PCI_DEVICE_ID_SYSKONNECT_GE) },
 	{ PCI_DEVICE(PCI_VENDOR_ID_SYSKONNECT, PCI_DEVICE_ID_SYSKONNECT_YU) },
 	{ PCI_DEVICE(PCI_VENDOR_ID_DLINK, PCI_DEVICE_ID_DLINK_DGE510T), },
+	{ PCI_DEVICE(PCI_VENDOR_ID_DLINK, 0x4b00) },
+	{ PCI_DEVICE(PCI_VENDOR_ID_DLINK, 0x4b01) },

---

### Post by KingIndy on 2006-06-15
Is there going to be a patch to fix this or insructions to do this manually? Im having the same problem, brand spanking new card working fine in Breezy then upgrade and .... nothing .... :-({|=

---

### Post by DigitalXpert on 2006-06-30
I am also having troubles getting my DGE-530T working.  This is what I've tried so far...

Loaded the skge module with modprobe.  Did another lspci and it is still not detected.  

I'm using skge by recommendation from other *nix forums in addition to 2.6.17.1 kernel changelogs.  Go to [http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.17]("http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.17") and search for commit 2d2a387199bf38c6628adb9c6184d7ab6e306148 an you will see where I'm coming from.

I also put an entry in /etc/modules to make it load at boot thinking the card would get configured then.  After reboot lspci still shows the card as unknown (has always known it was dlink however).

The device is not listed in the file /proc/bus/pci/devices either.  I have also viewed dmesg and it mentions nothing about my card.  

I have tried this card, and other identical cards, in several pci slots with no luck.

I am running this kernel: 2.6.15.25-k7

Can anyone help?

UPDATE: 7/4/2006

Built the newst kernel 2.6.17.3 and installed it.  The card is still not recognized when booting with this kernel.

---

### Post by mholmes on 2006-07-11
Hi there,

I got this card to work fine on Dapper. This is what I did:

-Copied the linux driver folder off the CD that came with the card.

-Found the README file.

-Followed the instructions to unpack the stuff.

-Went and got the linux header files using Synaptic (never had to recompile my kernel before!)

-Tried to run the install.sh file for the driver.

-Got an error message to say it didn't know where the linux header files were, along with a really helpful example showing me how to make a symbolic link to where the header files actually are.

-Successfully ran install.sh, which recompiled the kernel and loaded the driver.

-Rebooted, then configured and activated the card (on eth1), and set it as default.

-Rebooted again, this time with the network cable connected to the new card instead of the old card.

-Bingo!

Hope this helps&#65294;I'll post a copy in a couple of other threads on the same topic -- sorry about the duplication but people may not find it if I leave it in just the one thread.

Cheers,
Martin

---

### Post by mholmes on 2006-11-06
After my unexpected success with Dapper, I installed Edgy, but now the same approach to installing the dge-530t fails. When I run install.sh, I get this:

./install.sh: 68: Syntax error: "(" unexpected

Line 68 is this:

function message_status ()

Anyone know what the problem might be?

Cheers,
Martin

---

### Post by JonCage on 2007-03-26
I'm having [url=http://ubuntuforums.org/showthread.php?t=393042]similar problems with a D-Link 528T[url]. My problem differs ever so slightly though as my card is based upon a Realtek chipset. I get this when I try and load the driver:

```
[42949388.340000] r8169 Gigabit Ethernet driver 2.2LK loaded
[42949388.340000] r8169: probe of 0000:01:06.0 failed with error -22
```

What's really frustrating is that I only bought this card because it was supposed to work fine (on Linux) straight out of the box! :roll:

---

### Post by lucianolinhares on 2007-05-03
I had the same problem. The problem was solved upgranding the last version of Ubuntu Drapper Linux Kernel. Now I´m using 2.6.15-28 version and the network card is working.

---

### Post by lemot66 on 2007-11-01
> **mholmes said:**
> After my unexpected success with Dapper, I installed Edgy, but now the same approach to installing the dge-530t fails. When I run install.sh, I get this:

./install.sh: 68: Syntax error: "(" unexpected

Line 68 is this:

function message_status ()

Anyone know what the problem might be?

Cheers,
Martin

I get this exact same problem and have no clue how to get around this.  Did anyone ever find an answer?  Thanks,
Thor

---

### Post by danielmncastro on 2007-12-06
> ./install.sh: 68: Syntax error: "(" unexpected

Line 68 is this:

function message_status ()

This is happening because the default shell of this version of Ubuntu is **dash**, a lighter shell and, of course, with less resources. And I guess they created this script in a RH box, which uses (or used to use) **bash** as default shell. Mine is 6.10 (Edgy) and it also uses **dash** as default. 

You can check it by: 

```
# ls -pla /bin/sh
```

So you have two choices:

1) Change the first line of the **install.sh** from 

```

#!/bin/sh
```

to 

```

#!/bin/bash
```

This change will make the script to be run by bash.

2) Change the default shell
```

# rm /bin/sh
# ln -s /bin/bash /bin/sh
```

By the way, the symbolic link from /usr/src/linux-headers-* to /usr/src/linux was necessary here too.

Regards,

- Daniel

---

### Post by Return Privacy on 2008-06-02
DGE-530T Dlink gigabit new card put in Ubuntu 7.10 and it is not seen and will not work.
Does anyone know how to make this thing work?
I don't know what "compile" or "source" mean. I just need to know how to move this "dge530t_driver_linux_610.tar" file to where the drivers are.
Anyone know how to do this?
I thought you didn't have to know any fancy command line stuff to use Ubuntu?

---

