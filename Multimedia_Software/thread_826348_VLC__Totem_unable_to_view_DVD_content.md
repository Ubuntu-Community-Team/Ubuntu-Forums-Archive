---
title: "VLC / Totem unable to view DVD content"
date: 2008-06-11
forum: Multimedia Software
---

### Post by bluepowder7 on 2008-06-11
ok, so this is weird.  a week or two ago, VLC was working fine.  now, when i insert a DVD into a USB-connected DVD drive, it'll autoplay on Totem.  but if i close Totem and re-open it, or try to then use VLC, neither app is able to play the DVD.  at all.  nothing.

VLC error messages are:

```

Unable to open 'dvd:///dev/hdb'
dvdread error: DVDRead cannot open source: /dev/hdb
vcd error: could not read TOCHDR
vcd error: no movie tracks found
access_file error: file /dev/hdb is empty, aborting
cdda error: could not read TOCHDR
cdda error: no audio tracks found
main error: no suitable access module for `dvd:///dev/hdb'

```


Totem error messages are:

```

Totem cannot play this type of media (DVD) because it does not have the appropriate plugins to be able to read from the disc.

Please install the necessary plugins and restart Totem to be able to play this media.

```


wtf went wrong???  the only thing that i can recall that i did recently was install ubuntu-studio packages, and update some mplayer / mencoder stuff that's one or two revs higher than what is in the repos (by downloading deb packages from the ubuntu backports thingy).  i can use **vobcopy** just fine, and the DVD will play the FIRST time (autorun) only, but that's it.

did i perhaps somewhere along the way mistakenly uninstall a package that the system thought was unused?


**_Edit / update_**
ok, the problems are when using a USB-connected DVD drive.  seems to work fine if i shove the disc into the internal drive...

---

### Post by mc4man on 2008-06-11
What you might want to do is with the usb drive connected run 
```
sudo lshw -C disk 
``` that will show you the device and links. Then when you open vlc (file -> open disk)you can type in either the device or link in the device name box. 
for example here's mine 
```
*-cdrom
       description: DVD reader
       product: DVD/HD  X807616
       vendor: TOSHIBA
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/dvd2
       logical name: /dev/scd2
       logical name: /dev/sr2
       version: MC08
       capabilities: removable audio dvd
       configuration: status=ready

```
so I could choose /dev/dvd2 or /dev/scd2
For totem usually if you open it under movie it should show the mounted disk name or r. click on desktop icon
Why don't you make vlc the default instead of totem  (hardy only)
see here [http://ubuntuforums.org/showthread.php?p=4986640#post4986640](http://ubuntuforums.org/showthread.php?p=4986640#post4986640)

---

