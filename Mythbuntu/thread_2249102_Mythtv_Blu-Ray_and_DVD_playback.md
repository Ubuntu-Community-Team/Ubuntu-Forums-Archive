---
title: "Mythtv Blu-Ray and DVD playback"
date: 2014-10-19
forum: Mythbuntu
---

### Post by gilson585 on 2014-10-19
Running mythtv on mythbuntu 14.04 lts with mythtv 0.27 fixes I was experiencing some issues using optical disk playback in myth.

First off myth had no idea where the dvd's were being mounted. Installed udisks fixed that.
Next they didn't automount, changing options in thunar "Removable drives and media" solved that.
Then I couldn't eject, added line ```
ENV{ID_FS_USAGE}=="filesystem", ENV{UDISKS_FILESYSTEM_SHARED}="1"
```
to /etc/udev/rules.d/99-udisks2.rules fixed that.

Now on to bluray support, oh boy ;-)
For the longest time I would rip blurays with makemkv but knew mythtv should be able to play them natively.
Uninstalled [COLOR=#006600][FONT=Monaco]libaacs0
[/FONT][/COLOR]Then symlinked libraries from makemkv with the following 3 lines (need makemkv compiled and installed for this)
```
[COLOR=#006600][FONT=Monaco]cd /usr/lib[/FONT][/COLOR]
[COLOR=#006600][FONT=Monaco]sudo ln -s libmmbd.so.0 libaacs.so.0[/FONT][/COLOR]
[COLOR=#006600][FONT=Monaco]sudo ln -s libmmbd.so.0 libbdplus.so.0
[/FONT][/COLOR]
```At this point VLC could play blurays natively but udisks2 would always mount them according to the disc title and myth for w/e reason needs an absolute path unlike dvd's which can just be set to "default" (assuming you already installed udisks otherwise it too needs an absolute path)
Thus in /etc/udev/rules.d/70-persistent-cd.rules I added the following line so my bluray drive always mounts to /media/bluray1 (don't know why it appends the 1) so i can specify that path in mythtv for bluray playback. Yay!!!
```
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{DEVNAME}=="/dev/sr0", ENV{ID_FS_TYPE}=="udf", SYMLINK+="bd1", ENV{GENERATED}="1", ENV{ID_FS_LABEL_ENC}="bluray"
```
Obviously ENV{DEVNAME} has to be your bluray drives logical block path and not just /dev/sr0 as in my secenario

Hopefully this is helpful for other users out there as I spent a good few hours figuring this out.

---

### Post by one30nav on 2014-10-20
Great post.

With my setup I didn't have to use a UDEV tweak to get Mythtv to eject. It just worked with udisks installed.

In Xubuntu: Applications -> Settings -> Removable Drives and Media -> Storage Tab; then checked the box next to "Mount removable media when inserted"

However, in Mythtv Setup I changed the DVD mountpoint from "/dev/dvd" to "default"

Also, for my UDEV version I instead used:

```
ENV{ID_CDROM}=="1", ENV{ID_FS_TYPE}=="udf", ENV{ID_FS_LABEL_ENC}="dvd"
```

... and this resulted in a bluray mountpoint to "/media/username/dvd" (for use in Mythtv Setup)

For me, this worked for DVDs and Bluray disks.

---

### Post by gilson585 on 2014-10-20
Eject may have been an issue of groups my user is a part of but im pretty sure if media was mounted mythtv would not eject but mine isn't a fresh install either. Hopefully my post helped you with something as it seems most of this info is scattered when it should work otb

---

### Post by one30nav on 2014-10-21
Consolidated everything in one place! Again, great post.

---

### Post by blm-ubunet on 2015-06-12
FWIW.. 
The simple trick of renaming {ID_FS_LABEL_ENC} to get a fixed mounting point & automounting stopped working here along time back. Possibly due to running a very minimal install & not std mythbuntu.

A simple udev rule calling a script using udisks has been reliable with mythtv & libmmbd.

/etc/udev/rules.d/72-autobdmount.rules
```
SUBSYSTEM=="block", ENV{ID_CDROM_MEDIA_BD}=="1", ENV{DEVNAME}=="/dev/sr1", ENV{ID_FS_TYPE}=="udf", SYMLINK+="bd1", ENV{GENERATED}="1", ACTION=="change", RUN+="/usr/local/bin/autobdmount"
# , ENV{ID_FS_LABEL_ENC}="bd-dvd"

```
/usr/local/bin/autobdmount
```
#!/bin/bash

{
  if [ $ID_CDROM_MEDIA_BD == 1 ]; then
    mkdir -p /media/bd-dvd
    mount -t $ID_FS_TYPE -o ro /dev/sr1 /media/bd-dvd
  else
    umount -l /media/bd-dvd
    rm -rf /media/bd-dvd
  fi
} &>> "/var/log/autobdmount.log" &
```
This script assumes BD optical drive is /dev/sr1 & required mountpoint is "/media/bd-dvd".
HTH.

---

