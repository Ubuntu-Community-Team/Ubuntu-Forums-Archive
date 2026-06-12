---
title: "ipod color 20GB not working w/ gtkpod, amaroK"
date: 2007-12-31
forum: Multimedia &amp; Video
---

### Post by mattismyname on 2007-12-31
Distribution is Ubuntu Hardy 8.04a2
Amarok is 1.4.8 using KDE 3.5.8
ipod is 20GB color

So, I restored the ipod with a windows box to get a fat filesystem.  I plug it into the linux box, automounter mounts it on /mnt/ipod no problem -- I can browse the files.  I run 'dcop kded mediamanager fullList' and the ipod is shown as:

```
/org/freedesktop/Hal/devices/volume_uuid_EFCB_4960
sdc2
IPOD

true
/dev/sdc2

vfat
false

media/removable_unmounted
ipod_unmount
false
```

I fire up amarok, Settings->Configure Amarok->Media Devices->Autodetect Devices and I get this error:  No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them. You can test this by running "dcop kded mediamanager fullList" in a Konsole window.

Anybody know how I can dig deeper into this?  Why is amarok not finding the ipod even though it is listed on the dbus?

Help much appreciated!

---

### Post by mattismyname on 2007-12-31
Oh, I should have mentioned, the manual configuration "Add device" item in amarok worked fine.  It's just the autodetection of the device that is not working.

---

