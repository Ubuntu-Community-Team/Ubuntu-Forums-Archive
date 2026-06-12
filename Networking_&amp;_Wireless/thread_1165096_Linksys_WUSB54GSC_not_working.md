---
title: "Linksys WUSB54GSC not working"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by jenkinbr on 2009-05-20
I recently purchased a Linksys USB adapter for use on my home wireless network, but am having trouble with the driver installation. I have been following the HowTo posted [here](http://ubuntuforums.org/showthread.php?t=225206)  and [this guide]("http://ubuntuforums.org/showthread.php?t=885847") as helps in installing this device.

Despite this, I am receiving the following output from the command ***cat /var/log/syslog*** immediately after connecting the device:

```

May 19 19:50:06 jenkinbr kernel: [  179.822163] usb 2-2.3: new full speed USB device using ohci_hcd and address 4
May 19 19:50:07 jenkinbr kernel: [  179.951744] usb 2-2.3: not running at top speed; connect to a high speed hub
May 19 19:50:07 jenkinbr kernel: [  180.035721] usb 2-2.3: configuration #1 chosen from 1 choice
May 19 19:50:07 jenkinbr kernel: [  180.151889] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
May 19 19:50:07 jenkinbr kernel: [  180.355174] usb 2-2.3: reset full speed USB device using ohci_hcd and address 4
May 19 19:50:07 jenkinbr kernel: [  180.498432] ndiswrapper: driver ndiswdm (Linksys, A Division of Cisco,10/09/2007,4.118.4.0) loaded
May 19 19:50:08 jenkinbr kernel: [  181.667265] ndiswrapper (wrap_submit_irp:1161): ioctl 0022001F NOT IMPLEMENTED
May 19 19:50:08 jenkinbr kernel: [  181.667285] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
May 19 19:50:08 jenkinbr kernel: [  181.667294] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
May 19 19:50:08 jenkinbr kernel: [  181.667308] ndiswrapper (mp_halt:262): device deedf500 is not initialized - not halting
May 19 19:50:08 jenkinbr kernel: [  181.667314] ndiswrapper: device eth%d removed
May 19 19:50:08 jenkinbr kernel: [  181.667343] ndiswrapper: probe of 2-2.3:1.0 failed with error -22
May 19 19:50:08 jenkinbr kernel: [  181.667388] usbcore: registered new interface driver ndiswrapper

```

My /etc/udev/rules.d/99-custom.rules file contains
```

BUS=="usb", SYSFS{idProduct}=="0075", SYSFS{idVendor}=="1737", RUN+="/bin/sh -c 'echo 1 > /sys/$devpath/device/bConfigurationValue'"

```

And the ***lsusb*** command prints the following:

```

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 046d:c225 Logitech, Inc. 
Bus 003 Device 004: ID 046d:c221 Logitech, Inc. G15 Keyboard / Keyboard
Bus 003 Device 003: ID 046d:c51b Logitech, Inc. 
Bus 003 Device 002: ID 046d:c223 Logitech, Inc. G15 Keyboard / USB Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 058f:6331 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 002 Device 004: ID 1737:0075 Linksys **
Bus 002 Device 003: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 002 Device 002: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

***lsmod*** shows that ndiswrapper IS being loaded by the kernel.

***dmsg | grep -e ndis -e wlan*** shows
```

[   15.114439] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   15.685684] ndiswrapper: driver ndiswdm (Linksys, A Division of Cisco,10/09/2007,4.118.4.0) loaded
[   17.243612] ndiswrapper (wrap_submit_irp:1161): ioctl 0022001F NOT IMPLEMENTED
[   17.243632] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   17.243641] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   17.243655] ndiswrapper (mp_halt:262): device dfa59500 is not initialized - not halting
[   17.243661] ndiswrapper: device eth%d removed
[   17.243692] ndiswrapper: probe of 2-2.3:1.0 failed with error -22
[   17.243752] usbcore: registered new interface driver ndiswrapper

```

I am using the ndiswrapper packages from the Ubuntu Repos. ***sudo dpkg --status ndiswrapper-common | grep Version*** shows:
```

Version: 1.53-2ubuntu1

```

If anyone could offer me any help on this problem, it would be appreciated much.

Thanks in advance to anyone who may help out.

---

### Post by GepettoBR on 2009-05-20
> **javaJake said:**
> **_[SIZE="4"]Ubuntu 8.10 (Intrepid) Deprecates This HOWTO![/SIZE]_**
That's right! This HOWTO is officially deprecated as of Ubuntu Intrepid. ndiswrapper is no longer needed. As soon as you plug in the WUSB54GS while running Ubuntu Intrepid, it should immediately function!

Jenny, I see you're using Jaunty, so according to the author you shouldn't really follow that guide at all. Did you attempt to use the device without ndiswrapper?

---

### Post by jenkinbr on 2009-05-20
Yes, I did.  Nothing.

---

### Post by GepettoBR on 2009-05-20
Well, then I guess ndiswrapper it is then. Are you on a 64-bit install?

>  zraffz,

Are you running a 64-bit machine? If so, finding drivers on the internet for this is near impossible.

If you're not running a 64-bit system, then follow the instructions laid out at
[http://www.ubuntuforums.org/printthread.php?t=225206](http://www.ubuntuforums.org/printthread.php?t=225206)

When you follow these instructions, make sure that you switch out anything that says "000e" or "0014" with "0026". I have gotten it to work successfully on my 32 bit machines, but not my x86_64 one. If you find any 64-bit drivers for this, let me know.

If you need to build 'ndiswrapper' from source and don't have access to the internet on your machine, but you have access to the installation disks, insert disk 1 after you've booted and install the packages called 'kernel-xen-devel' and 'kernel-headers' before installing ndiswrapper according to the instructions at the link above. Reading through the tutorial before doing anything helps a lot.
Reply With Quote
Source: [http://forums.fedoraforum.org/showthread.php?t=142665](http://forums.fedoraforum.org/showthread.php?t=142665)

---

### Post by jenkinbr on 2009-05-21
No.  My macine is i686, so I'm 32-bit.

The link that spledger pointed to on the other forum is the printable version of the one I posted above. I've never installed anything from source before, but I think that is my only option at this point, short of returning the device for a different adaptor.

So, I will update my (currently) offline install (I've already upgraded Jaunty using my method), install build-essential and everything else that is needed, and give the installation from source a shot.

---

### Post by GepettoBR on 2009-05-21
Good luck, and I'm sorry I couldn't be of any help.

---

### Post by jenkinbr on 2009-05-21
Thanks for at least trying to help.

I'll post back my results after I upgrade and install build-essential, and get the chance to build and install ndiswrapper.  I will do this after a reboot.

---

### Post by jenkinbr on 2009-05-22
I uninstalled ndiswrapper and it's components, then downloaded the souce for ndiswrapper version 1.54.  I ran make and make install, re-installed the drivers, then tried again.

The dmsg output was the same as before.

Any more suggestions from anyone?

---

### Post by lindsay7 on 2009-05-23
This may not help much, but I have this adapter and it works fine.  Here is the info on it from lsusb


I can not find the version number but the chip set or driver is Linksys WUSB54GC 802.11g Adapter [ralink rt73]

I have tried it on two different Ubuntu systems.


Sorry I noticed that my adapter is a WUSB54GC and the other model shown in GepettoBR's post is a WUSB54GS.

I guess you model has a different chip set.

---

### Post by crazyness003 on 2009-05-23
In all honesty, ndswrapper sucks. HAve you tried getting native drivers.
(sorry if I seem unfelpful, but last time I had trouble with wifi, it was solved with a whole kernel upgrade. NOTHING worked before that kernel upgrade. Kudos to the dev teams)

Anyway, I'd still report it in Launchpad. Maybe you can get more technical help there, about a specific devise/chip.

---

### Post by jenkinbr on 2009-05-23
Currently I'm trying to follow instructions found here --> [http://www.jooz.net/rndis/](http://www.jooz.net/rndis/)

Maybe I'll have luck, but I now need to download some additional packages before it will work for me.

---

### Post by crazyness003 on 2009-05-24
sorry man, cant help you. What kernel are you running?
Also, according your your article, Broadcom 4320 should be researched. I know there are a few members in the forums who, dare I say, specialize in Broadcom Chipsets. I know Ayuthia is one of those people.
Also, take a look at this: [http://ubuntuforums.org/showthread.php?t=1055078](http://ubuntuforums.org/showthread.php?t=1055078)
I just found it.

Anyway, good luck.

---

### Post by jenkinbr on 2009-05-25
Thanks, crazy - I'll take a look at that as well.

---

### Post by crazyness003 on 2009-05-26
well, what kernel you got? Is it most recent?

---

### Post by jenkinbr on 2009-05-27
2.6.28-11 on i686.

---

### Post by jenkinbr on 2009-05-29
I've given up on this adaptor for the time being.

Iwent and purchased a Belkin FSD7050 version 3125, which works out of the box.

---

