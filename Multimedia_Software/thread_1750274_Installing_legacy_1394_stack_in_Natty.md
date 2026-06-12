---
title: "Installing legacy 1394 stack in Natty ?"
date: 2011-05-05
forum: Multimedia Software
---

### Post by winspear on 2011-05-05
How do I install the legacy firewire 1394 stack in Natty. I need it to run some programs ? 
Is this even possible or should I revert back to Lucid to use these drivers ? 

Any help will be appreciated. 

Thanks

---

### Post by mikhartwell on 2011-06-06
I too am attempting this this but with no luck.

I'm running Ubuntu Studio Natty and want to capture DV with Kino (or cli dvgrab) but it can't find raw1394. I've tried unloading the juju stack and then loading the lagacy stack:

   [FONT=Courier New]sudo modprobe -r firewire-ohci[/FONT]

which goes fine, but I can't load legacy firewire:

   [FONT=Courier New]sudo modprobe ohci1394 && sudo modprobe raw1394
   FATAL: Module ohci1394 not found.[/FONT]

...can't find raw1394 either. They aren't in /dev

I've tried unblacklisting the legacy stack and blacklisting juju instead in

    [FONT=Courier New]/etc/modprobe.d/blacklist-firewire.conf[/FONT]

and then rebooting. No joy. juju stack loads. Checking the kernel log:

   [FONT=Courier New]grep firewire /var/log/kern.log

Jun  7 00:31:43 dellj kernel: [182395.856519] firewire_ohci: isochronous cycle inconsistent[/FONT] [FONT=Courier New]
Jun  7 00:31:43 dellj kernel: [182395.856604] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
Jun  7 00:31:44 dellj kernel: [182396.440530] firewire_core: created device fw1: GUID 0800460101046022, S100
Jun  7 00:31:59 dellj kernel: [182412.063210] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
Jun  7 00:31:59 dellj kernel: [182412.074030] firewire_ohci: node ID not valid, new bus reset in progress
Jun  7 00:31:59 dellj kernel: [182412.074404] firewire_core: skipped bus generations, destroying all nodes
Jun  7 00:32:00 dellj kernel: [182412.572093] firewire_core: rediscovered device fw0
Jun  7 00:32:00 dellj kernel: [182412.572106] firewire_core: phy config: card 0, new root=ffc0, gap_count=63
Jun  7 00:48:29 dellj kernel: [183401.980140] firewire_ohci 0000:03:01.0: PCI INT A disabled
Jun  7 00:48:29 dellj kernel: [183401.980149] firewire_ohci: Removed fw-ohci device.
Jun  7 00:48:47 dellj kernel: [183420.037256] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun  7 00:48:47 dellj kernel: [183420.100188] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
Jun  7 00:48:48 dellj kernel: [183420.600382] firewire_core: created device fw0: GUID 314fc00030babc50, S400
Jun  7 00:57:03 dellj kernel: [    1.464299] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun  7 00:57:03 dellj kernel: [    1.532175] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x1
Jun  7 00:57:03 dellj kernel: [    2.032132] firewire_core: created device fw0: GUID 314fc00030babc50, S400
Jun  7 01:12:56 dellj kernel: [  966.324175] firewire_ohci 0000:03:01.0: PCI INT A disabled
Jun  7 01:12:56 dellj kernel: [  966.324185] firewire_ohci: Removed fw-ohci device.[/FONT]

Any help in this would be greatly appreciated. Maybe some way of getting Kino to use the juju stack? Thanks :)

---

### Post by LonelyStar on 2011-06-08
I would also be very interested in how to get the old raw1394 kernel module, or /dev/raw1394 back. I need it for a phantom device.

---

### Post by mikhartwell on 2011-06-12
I finally got this to work (which I found here: [https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/779680](https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/779680))

I've since moved from Ubuntu Studio 11.04 to Ubuntu Desktop 11.04 where I had the same problem. the fix is simply to link /dev/fw0 to /dev/raw1394:

**[FONT=Courier New]sudo ln /dev/fw0 /dev/raw1394[/FONT]**

and you might need give yourself read/write permissions as well:

**[FONT=Courier New]sudo chmod 755 /dev/raw1394[/FONT]**

and Kino capture works just fine :)

---

### Post by openfly on 2011-06-24
I give up.  I am on the verge of rebuilding my kernel.  There's no supported work around here and it doesn't look like anyone plans on fixing this on the ubuntu side.

=/

---

### Post by scubasean on 2011-09-27
Hi,

I am pretty new to linux and have been trying to capture DV tapes with kino and a PCI firewire card with a Via chipset. I seem to be having the same problems.

I understand its because the old raw1394 stack is now obsolete. But how do you get kino to work without it?

Thank

Sean

---

### Post by BicyclerBoy on 2011-09-27
[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

note the last important step to rebuild the kernel boot image..

---

### Post by scubasean on 2011-09-29
[LEFT]I've seen this guide before but I keep falling down because I can't find the Ubuntustudiocontrols panel... I've search all the drop down menus and can't find it.

Do I have to install it?

Thanks

Sean
[/LEFT]

---

### Post by BicyclerBoy on 2011-09-29
You maybe be able to install it but if you are not running "studio" it could be pointless.
I think that studio controls is a GUI that does the same file editing that the previous link-->
```

"1. https://help.ubuntu.com/community/Firewire deals with 1394 video devices"
``` explains.

Post #4 is likely required.

---

### Post by scubasean on 2011-10-03
I have upgraded from 11.04 to Studio. Both the link:

[https://help.ubuntu.com/community/FireWire](https://help.ubuntu.com/community/FireWire)

you mention and the hyperlink containted in it about initialising the raw1394 via Ubuntustudiocontrol panel via drop down menus do not seem apply to me. I can't find any of the menus. Maybe my upgrade hasn't been complete for some reason?

Sean

---

### Post by Enfenion on 2011-11-23
OK, after a few days of banging my head into the wall and cursing over SensAble's "Open"Haptics library which is not open at all, I have finally found a solution on how to use the Phantom Omni in natty.

It is a rather ugly fix, but as I cannot modify "Open"Haptics it will have to do in my case. I've looked quite a lot around the web as well, and I can't find any other solution.

After installing "Open"Haptics and the device drivers which SensAble provides (using dpkg) you will have to work your way around the dependency of raw1394. I am not really sure which steps ultimately made it work for me, but the following steps are necessary.

1. Spoof the /dev/raw1394 device
2. Create a dummy kernel node

1. To spoof the /dev/raw1394 device, simply use ln and hard link the /dev/fw0 (or some other fwX) by typing the following commands:

```

sudo ln /dev/fw0 /dev/raw1394
sudo chmod 0777 /dev/raw1394
```

2. As I believe "Open"Haptics checks if the raw1394 module is present during launch (using lsmod or similar), I created a kernel module that doesn't do anything at all called raw1394. This can be done by making two files: Makefile and raw1394.c
These should be stored in the same folder and compiled using "make".
When this is done, you will have a file called raw1394.ko which can be loaded using insmod.

Makefile
```

obj-m += raw1394.o
all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
```

raw1394.c
```

#include <linux/module.h>
#include <linux/kernel.h>
 
int init_module(void)
{
  printk(KERN_INFO "Loaded dummy raw1394 module\n");
  return 0;
}

```

Commands to compile and load module:
```

make
sudo insmod raw1394.ko
```

(I'm sorry if I've posted this in the wrong place, but this seemed as the most likely place to look for a solution to this problem.)

---

