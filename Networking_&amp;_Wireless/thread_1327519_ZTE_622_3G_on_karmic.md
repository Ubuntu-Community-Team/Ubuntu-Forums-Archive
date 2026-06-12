---
title: "ZTE 622 3G on karmic"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by Amenotep on 2009-11-15
Hello, i have a USB modem, ZTE 622, and i'm having trouble running it on karmic. Can anyone point me to a tutorial explaining how to install it? So far google hasn't given me much to work, all the tutorials out there aren't related to karmic.

Thank you

---

### Post by Amenotep on 2009-11-15
Any1? i really need help with this one.

---

### Post by Amenotep on 2009-11-15
really need help on this one =/

---

### Post by pdc on 2009-11-15
this device is a zeroCD device; 

ie you need zero CDs to install it to a windows computer, as it is secretly loaded with windows drivers;

so when you plug it in, it is recognised in windows and the software auto-installs;

linux sees it as a CD-ROM; so you need to "flip" the device; so it is now unveiled to linux as a USB modem ...

you need a programme called usb_modeswitch ... that ... switches .. the mode ... of the usb ... modem .........

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

this is the explanation page:

If you go down to devices, your device is listed; recognised and just needs to be "flipped"

the kind folks have now made available an automated version; 1.0.5 and you would be best to download the debian version, that can be easily installed

go here

[http://packages.debian.org/search?keywords=usb-modeswitch](http://packages.debian.org/search?keywords=usb-modeswitch)

click on sid (unstable) to select the 1.0.5.1 version: unstable just means leading edge programmes are there; fear not;

install the programme; with luck, the process should be automatic; after install and a reboot: your system should now recognise your modem;

let us know how you get along

---

### Post by Amenotep on 2009-11-16
I'm trying it now, thanks a bunch!

---

### Post by Amenotep on 2009-11-16
It is no longer recognized as a storage device, but network-manager still isn't giving any signs of life.

 This is what i added in usb_modeswitch.conf:
```

DefaultVendor=  0x19d2
DefaultProduct= 0x2000

TargetVendor=   0x19d2
TargetProduct=  0x0001
DetachStorageOnly=1

```

And the file called 15-zte-mf622.rules in  **/etc/udev/rules.d/15-zte-mf622.rules **with the following code:

```

ACTION!="add", GOTO="ZTE_End"
# Is this the ZeroCD device?
SUBSYSTEM=="usb", SYSFS{idProduct}=="2000",
SYSFS{idVendor}=="19d2", GOTO="ZTE_ZeroCD"
# Is this the actual modem?
SUBSYSTEM=="usb", SYSFS{idProduct}=="0001",
SYSFS{idVendor}=="19d2", GOTO="ZTE_Modem"
LABEL="ZTE_ZeroCD"
# This is the ZeroCD part of the card, remove
# the usb_storage kernel module so
# it does not get treated like a storage device
#RUN+="/sbin/rmmod usb_storage"
RUN+="/usr/local/sbin/usb_modeswitch -d 1 -v 0x19d2 -p 0x2000 -V 0x19d2 -P 0x0001"
LABEL="ZTE_Modem"
# This is the Modem part of the card, let's
# load usbserial with the correct vendor
# and product ID's so we get our usb serial devices
RUN+="/sbin/modprobe usbserial vendor=0x19d2 product=0x0001",
# Make users belonging to the dialout group
# able to use the usb serial devices.
MODE="660", GROUP="dialout"
#MODE="660", GROUP="tty"
LABEL="ZTE_End"

```

What do you think?

---

### Post by Amenotep on 2009-11-16
It shows up as 19d2x001, but i still don't know how to connect... Network manager isn't helping.

---

### Post by pdc on 2009-11-16
so you installed the 1.0.5 version (that should automate the process?)

Most successful usb_modeswitch messages have a

Message Content section with lots of numbers: I see yours just says Detach Storage: do you know why that is?

the guys at the usb_modeswitch forum offer help

[http://www.draisberghof.de/usb_modeswitch/bb/](http://www.draisberghof.de/usb_modeswitch/bb/)

sign up

---

### Post by nyarnon on 2009-11-17
I don't think the modeswitch is the way to go. Had it working fine on jaunty without and my other zte modem uses eject in the the filemenu to switch to modem status. But 622 seems to have a problem there. Is there anybody out there who has it actually running with karmic?

---

### Post by pdc on 2009-11-17
tell us why you don't think usb_modeswitch is the way to go, nyarnon;

the usb_modeswitch home page lists the ZTE 622

---

### Post by nyarnon on 2009-11-17
I did, my English that bad?

---

### Post by lusephur on 2009-11-18
it's rather strange, the zte mf622 modem worked quite well on jaunty- only now when i need to use the device do i have an issue myself, gotta use my phone loaded with the sim to seek out an answer

---

### Post by lusephur on 2009-11-18
and the usbswitch mentioned earlier has sorted my issue, cheers.

---

### Post by nyarnon on 2009-11-18
Isn't that nice. Doesn't really solve anything here till now. What did you do after installing the sid .deb?

---

