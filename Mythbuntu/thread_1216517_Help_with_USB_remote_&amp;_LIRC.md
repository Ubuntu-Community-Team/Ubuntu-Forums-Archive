---
title: "Help with USB remote &amp; LIRC"
date: 2009-07-18
forum: Mythbuntu
---

### Post by sraasch on 2009-07-18
I'm trying to get a USB remote receiver to work with a "normal" IR (non-learning) universal remote (the DirectTV RC-64R). 

I can't use a serial receiver because my platform is an AppleTV. I don't want to use the apple remote because 6 buttons is just not enough.

lsusb reports:
```

Bus 002 Device 002: ID 05ac:8241 Apple, Inc.
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 06b4:1c70
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```So, the kernel sees the receiver (Vendor=0x06b4, Product=0x1c70)... Yes, it's that same cheap MCE remote from ebay.

I've used the quirk to keep the usbhid device from attaching the device.

In /etc/modprobe.d/options:

```

options usbhid quirks=0x06b4:0x1c70:0x04

```I've seen suggesttions that this sometimes doesn't work, but I believe it has for me, since before the addition of the quirk, I had some keystrokes showing up with the original MCE remote, and afterwards, I have none.

What I'm having trouble with now is getting *anything* from the receiver...

/proc/bus/usb/device reports:

```

 ...
 T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=01 Dev#=  4 Spd=1.5 MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=06b4 ProdID=1c70 Rev= 2.00
C:* #Ifs= 1 Cfg#= 1 Atr=60 MxPwr=100mA
I:* If#= 0 Alt= 0 #EPs= 2 Cls=03(HID  ) Sub=01 Prot=02 Driver=(none)
E:  Ad=81(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
E:  Ad=01(O) Atr=03(Int.) MxPS=   8 Ivl=10ms
 ...
 
```I've checked that the modules are installed...

```

Module                  Size  Used by
lirc_mceusb2           20228  0
lirc_mceusb            16992  0
lirc_dev               20020  2 lirc_mceusb2,lirc_mceusb

```my /etc/lirc/hardware.conf is:

```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (old version MicroSoft USB ID)"
REMOTE_MODULES="lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

```(I've also tried lirc_mceusb on the modules line)

lirc fails to start with "/etc/intit.d/lirc restart" 

I'm not sure where to go from here... shouldn't one of the two lirc_mceusb* modules attach to that remote device?

thanks for the help!

---

### Post by Frances on 2009-07-19
I too am having problems with a USB remote - a remotec dw6130 - it is being seen by the hp2133 netbook and 'mounted' in /dev/usb as /dev/usb/hiddev0 but the error message from daemon.log states initialising /dev/usb/hid/hiddev0 followed by unable to open this file - has the naming of devices in /dec/usb changed in Jaunty - if so can someone please suggest a fix to this newbie

---

### Post by sraasch on 2009-07-19
[EDIT] Hmmm... that's not right... 

I do have a /dev/usb/hiddev0, but it's the AppleTV built-in IR receiver (which is not really useful).

So I still don't see where my external IR receiver is getting attached to _anything_

I could really use some help here...





[Original Message]
Interesting... so _**there's**_ a clue...

Checking my daemon.log, I see that lirc has tried to use /dev/usb/hiddev0

With lircd not running, I do get output from that device, so I guess that all I have to do is get lircd to look at that for it's input... One step closer... :D

Thanks Frances!

---

### Post by Frances on 2009-07-20
There would appear to be major problems with some kernel mods introduced end of 2007 re hiddev - there would appear to be many reports of failures but I'm out of my depth here - I suspect LIRC is completely non-functional using USB devices under 9.04 ubuntu

---

### Post by sraasch on 2009-07-20
Well, I haven't seen evidence of that...
 
Looking at /var/log/udev, I see that my device is reported by the kernel.
 
At least as best as I can tell... I'm new to udev. I see that there is a device at /dev/bus/usb/001/004, which is where my remote is connected (bus 1, device 4). 
 
cat /dev/bus/usb/001/004 returns a constant string of "garbage" chars that is about 30+ chars long. It's the same each time I cat the device, even with no remote operating, so I'm not holding my breath that this is right.
 
Still hoping some kind soul out there has done this kind of thing before... I don't really want to spend $50+ on a "name-brand" IR recceiver...
 
-Steve

---

### Post by netromdk on 2009-08-16
Hi, I have the same problem.

> **sraasch said:**
> 
I'm not sure where to go from here... shouldn't one of the two lirc_mceusb* modules attach to that remote device?
  

I think you are right, and looking at the source here: [http://lirc.cvs.sourceforge.net/viewvc/lirc/lirc/drivers/lirc_mceusb/](http://lirc.cvs.sourceforge.net/viewvc/lirc/lirc/drivers/lirc_mceusb/) 
it looks as if lirc_mceusb simply does not support this vendor/product id.

Maybe you can just grab the source, add the vendor/product id and recompile the module?

- netromdk

---

