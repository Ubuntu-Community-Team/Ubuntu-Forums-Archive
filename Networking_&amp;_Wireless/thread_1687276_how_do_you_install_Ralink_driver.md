---
title: "how do you install Ralink driver?"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by noelissa on 2011-02-13
I downloaded a ralink driver for my wireless usb adapter and just need a bit of help installing the driver (RT3572USB)

---

### Post by chili555 on 2011-02-13
Here is a tutorial. I know it's a different device, but the driver is the same. This step may not be needed in the latest 2.5.0.0 driver. Try it *without*:> Change lines 1161 and 1162 as noted. The remainder of the file is unchanged:
Code:

#define RTUSB_URB_ALLOC_BUFFER(_dev, _size, _dma)		usb_alloc_coherent(_dev, _size, GFP_ATOMIC, _dma)
#define RTUSB_URB_FREE_BUFFER(_dev, _size, _addr, _dma)	usb_free_coherent(_dev, _size, _addr, _dma)

Post back if you need more help.

---

### Post by noelissa on 2011-02-14
> **chili555 said:**
> Here is a tutorial. I know it's a different device, but the driver is the same. This step may not be needed in the latest 2.5.0.0 driver. Try it *without*:Post back if you need more help.

Hey sorry but where is the tutorial?

---

### Post by chili555 on 2011-02-14
Sorry, I hate when that happens!

[http://ubuntuforums.org/showthread.php?t=1659230&highlight=rt3572sta](http://ubuntuforums.org/showthread.php?t=1659230&highlight=rt3572sta)

---

### Post by VernonA on 2011-02-14
There is also a longer tutorial on this topic at:
[http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/linksys-wusb600n-driver-and-dlink-dwl-ag132-driver-622449/")
which is harder to follow but contains more details of some of the processes involved. Between the two you should be able to get the new driver compiled and installed.

---

### Post by noelissa on 2011-02-15
> **chili555 said:**
> Sorry, I hate when that happens!

[http://ubuntuforums.org/showthread.php?t=1659230&highlight=rt3572sta](http://ubuntuforums.org/showthread.php?t=1659230&highlight=rt3572sta)

Hey thanks a lot. Now I'm pretty sure I did it right up to the last step. When I do "modprobe rt3572usb" it says:
FATAL: Module rt3572usb not found.

---

### Post by noelissa on 2011-02-15
btw I don't know if this makes a difference or not but I'm using the 64-bit OS

---

### Post by chili555 on 2011-02-15
> **noelissa said:**
> Hey thanks a lot. Now I'm pretty sure I did it right up to the last step. When I do "modprobe rt3572usb" it says:
FATAL: Module rt3572usb not found.I think it says:```
modprobe rt3572[COLOR="Red"]sta[/COLOR]
```Did you try that?

---

### Post by noelissa on 2011-02-15
Alright yeah I just tried that and it didn't really do anything just went to the next line. So I restarted my computer and it's still not working? Should I just try to do all the steps one more time?

EDIT: I just went through all the steps again and used rt3572sta at the end and still nothing..

---

### Post by chili555 on 2011-02-15
When you load a module and the cursor just comes back to the command prompt, it means the command was accepted and executed and there are no errors to report. Now does this show a wireless interface, ra0 perhaps?```
iwconfig
```What does this say?```
sudo iwlist ra0 scan
```When you click the Network Manager icon, are there networks listed? Can you click one and connect?

After you have built and installed the module, you shouldn't have to do all the steps again; at most, you might need:```
sudo modprobe rt3572sta
```

---

