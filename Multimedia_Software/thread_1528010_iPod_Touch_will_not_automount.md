---
title: "iPod Touch will not automount"
date: 2010-07-10
forum: Multimedia Software
---

### Post by denham2010 on 2010-07-10
Hi, using Xubuntu 10.4 and following this guide [how-to-finally-sync-your-iphone-or-ipod]("http://u-bunted.blogspot.com/2010/03/how-to-finally-sync-your-iphone-or-ipod.html") my iPod Touch will not automount.

I can mount it manually using ifuse, but it is not recognised as a media device so I am unable to use Rhythmbox or Gtkpod.

Not getting any errors either.

lsusb recognises the device
```
Bus 001 Device 007: ID 05ac:1291 Apple, Inc. iPod Touch 1.Gen
```

No errors in dmesg when I plug it in either
```
[   67.370046] usb 1-1: new high speed USB device using ehci_hcd and address 7
[   67.525425] usb 1-1: configuration #1 chosen from 3 choices
```

Any and all help greatly appreciated.

Cheers.

---

### Post by chris-man on 2010-08-01
I'm seeing exactly the same problem. Under Jaunty it at least appeared as a camera I think. But under Lucid it doesn't appear as a drive. I see exactly the same as the OP when running dmesg or lsusb

Additionally, the iPod is detected correctly under GNOME, so my guess would be a service is starting under a GNOME session that isn't under XFCE

---

### Post by charding on 2010-10-07
I can also manually mount using ifuse.

I would also like to find out how to do this, but to do this with my iphone instead. I know thunar has it's own volume manager and there is a thunar-volman command where you can add devices using that script if you know the UID of the device. I'm trying to find out my UID using the ifuse binaries (idevice_id, ideviceinfo,...) but so far I can't figure it out.

---

### Post by mr_luksom on 2010-10-08
Since switching from ubuntu lucid to xubuntu lucid I can't auto mount either.

I use ifuse and gtkpod - this should work with the latest libimobiledevice. An update to the ppa has just come through in the past couple of days (libimobiledevice1.0.3 is the latest).

So I assume you get no errors from ifuse? Where are you mounting it?

Have you created an iPod repository in gtkpod? I had to do this sometimes when I was messing around with the best way to mount it (Edit -> Repository Prefs).

---

### Post by gwoodruff on 2011-03-14
In Xubuntu Try Gigolo, My touch shows up when plugged in and 1 click to connect, not auto but pretty easy! We may be auto mounting when Natty is release as it uses the next release of xfce.

---

