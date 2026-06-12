---
title: "usb automount icons missing"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by mbradlcu on 2007-07-12
Hi all,
could someone explain how gnome-nautilus creates icons when a usb devices is inserted? reason I ask is after removing a usb device too quickly nautilus no longer displays the icons when any usb device is connect.. I can explicitly mount the device, eg:
```
sudo mount /dev/sdb1 /mnt
```
I've tried restarting nautilus, rmmod/modprobe - {ehci_hcd,usb_storage,uhci_hcd}
but I still don't have any mount icons on the desktop.
I suppose a reboot or even a gdm restart would correct this but I'd like to know what's actually going on "under the hood"

TIA!!!

---

### Post by mbradlcu on 2007-07-14
for my reference (and anyone else who cares) I think the following fixed the issue:
```
/etc/init.d/dbus restart
```

---

