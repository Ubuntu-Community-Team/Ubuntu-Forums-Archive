---
title: "iwconfig no good"
date: 2005-02-24
forum: Networking &amp; Wireless
---

### Post by dusk-you-n-me on 2005-02-24
I'm relatively new to Linux but I've gotten from nothing installed to this point with the help google.

Old compaq laptop w/ a DWL-G630 Dlink pcmcia wireless card. I installed ndiswrapper, no problems. Installed the driver, no problems (net5211 present, hardware present).  I did modprobe ndiswrapper. When I do iwconfig I get: ```
lo no wireless extensions.
sit0 no wireless extensions.
``` I have a blinking power light on the card. I just don't have any interfaces showing up. Any ideas/links/etc is appreciated.

---

### Post by alastair on 2005-02-24
Looks like the wireless device is not present/found/initialised.

Your best bet is to look in the logs (as always) i.e. see if there are any errors reported in :

/var/log/syslog

e.g. when ndiswrapper loads.

---

### Post by dusk-you-n-me on 2005-02-24
I did modprobe ndiswrapper, then grep ndis syslog and took the last entries by the date and this is what I get:

 Feb 24 19:16:28 localhost kernel: ndiswrapper version 1.1rc2 loaded (preempt=yes,smp=no)
Feb 24 19:16:29 localhost kernel: ndiswrapper: driver net5211 (D-Link,7/7/2004,2.2.4.32) loaded
Feb 24 19:16:30 localhost kernel: ndiswrapper: using irq 11
Feb 24 19:16:30 localhost kernel: ndiswrapper (NdisWriteErrorLogEntry:253): log: C0001389, count: 4 (c5baa220), return address: c6a5f616, entry: c6a606d0 offset: 4294963014
Feb 24 19:16:30 localhost kernel: ndiswrapper (ndiswrapper_add_one_pci_dev:185): Windows driver couldn't initialize the device (C000009A)
Feb 24 19:16:30 localhost kernel: ndiswrapper: probe of 0000:01:00.0 failed with error -22
Feb 24 19:16:30 localhost udev[5429]: creating device node '/dev/ndiswrapper'


Could it be I don't have enough resources to run the card? I *think* when I had Windows on here I had to disable my infrared port to free up some resources/IRQ. I think.  Anyways, any help here is appreciated as I don't know what I'm looking at for the most part. I'm surprised at myself for getting to this point. Thanks for the help so far.

---

### Post by alastair on 2005-02-25
It looks like ndiswrapper doesn't work for you I'm afraid. Your best bet might be to go to the ndiswrapper sourceforge web site and see if others have the same device and similar problems. Perhaps someone has found a solution or a newer version of ndiswrapper fixes this.

---

### Post by acascianelli on 2005-02-26
did you do an insmod ndiswrapper?

---

### Post by alastair on 2005-02-26
Yes, the driver is getting loaded - look at the syslog entries posted.

---

### Post by dusk-you-n-me on 2005-02-27
I'm pretty sure it's just that I don't have enough resources. I found this on another forum:

> I looked it up in the ndiswrapper FAQ and it says the following, if the error code is present then it means that there is an irq problem. It recommends looking to see what is using what interrupts and stuff like that and then to free it up. ALso it mentions check your bios and acpi settings to see how irq are assigned. 

SO in my case i had to change the hardware detection at the beggining of boot to see that the irq are assigned properly.


My question is how to a do what he did? Not exactly persay, but what file or whatever do I edit or can I look at to see the boot/IRQ information?

---

