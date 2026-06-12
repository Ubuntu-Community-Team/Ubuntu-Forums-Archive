---
title: "Totem Autoplay DVD doesn't work"
date: 2009-08-30
forum: Multimedia Software
---

### Post by slovak57 on 2009-08-30
When a DVD is inserted into my COMPAQ EVo, totem opens up and gives the infamous "Could not open location.  You might not have permission to open the file" error.  Totem will play the DVD flawlessly when the application is opened from the desktop menu and the "Play Disk ..." menu item is selected from the Movie menu.  I am running Ubuntu 9.04.

I think something in the system configuration is assuming my DVD drive has a different name.  It is listed as CDROM0 in the media folder but totem is looking for /dev/sda1 instead of /dev/cdrom.  Here is the output from a "totem dvd://" terminal session:

mike@ubuntu:~$ totem dvd:/

** (totem:24028): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: no file info
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda1 with libdvdcss.
libdvdread: Can't open /dev/sda1 for reading
libdvdread: Device /dev/sda1 inaccessible, CSS authentication not available.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use device /dev/sda1 mounted on / for CSS authentication
libdvdread: Could not open /dev/sda1 with libdvdcss.
libdvdread: Can't open /dev/sda1 for reading
libdvdread: Device /dev/sda1 inaccessible, CSS authentication not available.
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(333): rsn_dvdsrc_start (): /GstPlayBin:play/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: No such file or directory


Any ideas?

---

### Post by mc4man on 2009-08-30
Did you install ubuntu from a usb drive? (usb memory stick, whatever

Anyway, post the output of this

```
 cat /etc/fstab
```

---

### Post by slovak57 on 2009-08-31
Pretty sure I installed off of a CD (in a different drive than the DVD).  Anyway, here's the output:

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=0cff3be0-4826-4a6b-b35f-b5309cc38948 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b5ce917d-6814-40ca-9b82-bba6c218e6ca none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by mc4man on 2009-08-31
Your fstab is fine ( and I now recollect when installing from a usb the cdrom device is usually given something like /dev/sd[COLOR="Blue"]b[/COLOR]1

I don't use totem-gstreamer at all, and certainly not for dvd's. Totem-xine is much better suited.

So here totem-xine works fine when set as the autoplay default. What's interesting is if started from the cli like you posted it will also first look to / for the device,(in my case sd5) but will then proceed to the proper location. (/dev/scd0

Maybe give totem-xine a try, needs libxine1-ffmpeg installed also. ( will not show up in menu, use edit menus to enable (alacarte in terminal
> 
doug@doug-laptop:~$ totem-xine dvd://
libdvdnav: Using dvdnav version 1.1.16.3 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Attempting to use d[COLOR="Blue"]evice /dev/sda5 mounted on /[/COLOR] for CSS authentication
libdvdread: C[COLOR="Blue"]ould not open /dev/sda5 with libdvdcss[/COLOR].
libdvdread: Can't open /dev/sda5 for reading
libdvdread: Device /dev/sda5 inaccessible, CSS authentication not available.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/doug/.dvdnav/.map'
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFilePath:findDVDFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
libdvdnav: Using dvdnav version 1.1.16.3 from [http://xine.sf.net](http://xine.sf.net)
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: [COLOR="Blue"]Attempting to use device /dev/scd0 mounted on /media/cdrom0 for CSS authentication[/COLOR]
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/doug/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x00007307
libdvdread: Elapsed time 0
ect., ect.

---

### Post by slovak57 on 2009-08-31
Thanks for the tip.

Once I changed the default to totem-xine with the appropriate libraries, it worked like a charm!

---

