---
title: "Digital camera: no access to photos"
date: 2008-05-31
forum: Multimedia Software
---

### Post by LeBurt on 2008-05-31
Hi all,

I just plugged in a digital camera (Canon PowerShot A530) into my PC's USB port running Hardy Heron, and... nothing. It doesn't appear anywhere: I can't see it if I go to Computer, I can't see it under /media. I tried launching f-spot but it doesn't even start (I get the notification in the task bar that it's starting and then poof! gone). I tried both options in System, Preferences, Removable Drives and Media menu but nothing changes whether the Digital Camera checkbox is selected or not.

I get this in syslog when I connect the camera:

May 31 14:44:46 ciabata NetworkManager: <debug> [1212259486.670773] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3126_noserial'). 
May 31 14:44:46 ciabata NetworkManager: <debug> [1212259486.822258] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_4a9_3126_noserial_if0'). 

Similarly, in the message log:

May 31 14:44:46 ciabata kernel: [  442.063210] usb 6-7: new high speed USB device using ehci_hcd and address 6
May 31 14:44:46 ciabata kernel: [  442.132092] usb 6-7: configuration #1 chosen from 1 choice

This would indicate that the camera does indeed get recognized somehow. Then how come I don't get either f-spot or a folder in the file browser?

---

### Post by cariboo on 2008-05-31
Could you show us the output of dmesg:

There seems to be a bug in F-spot see this

[https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/37694](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/37694)

Have you tried any other programs eg: digikam or gtkcam? Also check /media directory to see if it shows up there.

Jim

---

### Post by LeBurt on 2008-05-31
The above two lines (second set) are from the message log (dmesg). Also, there is nothing in the /media directory other than the usual suspects (cdrom, floppy, other removable USB devices).

I can't find either digicam or gtkcam packages under Synaptic, what are they?

---

### Post by LeBurt on 2008-06-01
Anyone?

---

