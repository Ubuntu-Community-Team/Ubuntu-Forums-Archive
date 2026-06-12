---
title: "Automount, Unmount, and UDEV for CD/DVD and USB Storage"
date: 2008-06-19
forum: Mythbuntu
---

### Post by RTucker on 2008-06-19
Hi,
 
I'm wondering if anyone can tell me how to set up UDEV to always mount any USB device plugged in to a certain port to the same place. (ie. /dev/USBSTORE or /media/USBSTORE, or something) Which I understand is the best/only way to have all "USB Mass Storage" devices mounted to the same path automatically. Correct me if I'm mistaken.
 
And also, if someone can explain how I can get the same USB drives and more importantly inserted CD/DVDs to unmount automatically after a period of inactivity (so I can eject them), and automatically mount themselves as required.
 
I know that this can be done as I've seen guides on a few different sites for it. But I think these guides are targeted at much older distributions and they don't seem to match up with 8.04 very well.
 
The purpose of this is to have USB and CD/DVD 'folders' in the media library/videos gallery.
 
Thanks in advance for any info.

---

### Post by ian dobson on 2008-06-19
> **RTucker said:**
> Hi,
 
I'm wondering if anyone can tell me how to set up UDEV to always mount any USB device plugged in to a certain port to the same place. (ie. /dev/USBSTORE or /media/USBSTORE, or something) Which I understand is the best/only way to have all "USB Mass Storage" devices mounted to the same path automatically. Correct me if I'm mistaken.
 
Thanks in advance for any info.

You should be able to use the PLACE="" option in udev rules to force an USB attached device to always have the same mount point. Something long the lines of :-
SUBSYSTEMS=="usb", PLACE=="5.4", NAME="stickRight".

Sorry I can't test at the moment I'm too far away from my Linux box.

EDIT: Just tried a LiveCD and it looks as if PLACE isn't supported in udev on kernel 2.6.x
 
Regards
Ian Dobson

---

### Post by RTucker on 2008-06-20
Thanks for the reply (Again :-)),

I really surprised that there isn't more interest in this. Especially considering its a fairly common feature that almost any DVD player has these days.

Does anyone have any suggestions as to how else I might be able to achieve this?

It doesn't have to be symlinks in the library, I just want to be able to play files from CD/DVD's and USB drives.

---

### Post by ian dobson on 2008-06-20
Hi,

Could you try creating an UDEV rule using the ID option for the USB Bus/port. Something like:-

BUS=="usb", ID=="2.3", NAME="USBstick%b"

Regards
Ian Dobson

---

### Post by RTucker on 2008-06-20
OK,


In /etc/udev/rules.d/04-custom.rules I've tried

BUS=="usb", ID=="5.8", NAME="usbstore%b"

and

BUS=="usb", ID=="5.8", NAME="usbstore"

Both of which had no effect, it still mounts as /media/*devicelabel* and /dev/usbstore doesn't exist. I rebooted after each change to 04-custom.rules, and the 5.8 I got from tail -F /var/log/messages when I connected the HDD to the USB port.

---

### Post by ian dobson on 2008-06-20
Hi,

The ID value should be the bus/device number from lsusb.

Regards
Ian Dobson

---

### Post by RTucker on 2008-06-21
lsusb says its connected at 5.3

I've tried

BUS=="usb", ID=="5.3", NAME="usbstore%b"

and

SUBSYSTEM=="usb", ID=="5.3", NAME="usbstore%b"

both of which had no effect.

Do you know what is responsible for mounting USB devices in mythbuntu? It doesn't seem to be gnome-volume-manager as most places suggest (I guess because theres no gnome). Either way, it mounts all cds to /media/cdrom0, so maybe its possible to change it to mount all usb storage in a similar way, ie /media/usb0.

EDIT: Was a little unclear

---

### Post by RTucker on 2008-06-23
*bump*

Sorry, it just seems like this is such a basic feature of almost any dvd player, let alone PVR, has no one got this working?

---

