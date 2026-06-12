---
title: "wrong symbolic link to DVD player?"
date: 2008-08-05
forum: Multimedia Software
---

### Post by bo_n_tulsa on 2008-08-05
Howdy from Tulsa.
Have tried for a month to get DVD's to play.  I followed all the instructions in the Multimedia how-to thread.
In any case, I saw where one person was asked to show their dvd names:
ls -l /dev/d*

Here's the result of when I do that.
```
crw-rw----+ 1 root audio 14, 3 2008-08-05 17:36 /dev/dsp
lrwxrwxrwx  1 root root      4 2008-08-05 17:36 /dev/dvd -> scd0
```

Is something incorrect there and if so, how can I correct it?

---

### Post by bo_n_tulsa on 2008-08-05
Here's some more info:
```
 *-cdrom
       description: DVD reader
       product: IDE5216CO
       vendor: COMBO
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 0K52
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open
```


and this:
after running this:
cat /etc/udev/rules.d/70-persistent-cd.rules

outputs this
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# IDE5216CO (pci-0000:00:0f.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
```

---

### Post by mc4man on 2008-08-06
> I followed all the instructions in the Multimedia how-to thread

 your setup is fine. 
If you have vlc start it from the terminal,try to play a disk and post terminal output

---

### Post by tuxxy on 2008-08-06
YOu have all the lib packages installed then yes. like libdvdread etc

---

### Post by bo_n_tulsa on 2008-08-06
> **mc4man said:**
> your setup is fine. 
If you have vlc start it from the terminal,try to play a disk and post terminal output

mc4man,
Here is the output:
```

VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/mee/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: faild to read VIDEO_TS.IFO
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/dvd
[00000297] vcd access error: could not read block 151 from disc
[00000297] vcd access error: could not read entry points sector
[00000297] vcd access error: could not read block 512 from disc
[00000297] vcd access error: cannot read sector 512
[00000297] vcd access error: could not read block 513 from disc
```
Then it continues with the access errors forever.


tuxxy,
yes, synaptic search "libdvd" shows that everything beside dev packages with "libdvd" to be installed and current.

I tried a different dvd and got this output from vlc:
```
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: faild to open/read the DVD
[00000294] dvdread demuxer error: DVDRead cannot open source: /dev/dvd
[00000297] vcd access error: could not read TOCHDR
[00000297] vcd access error: no movie tracks found
[00000297] access_file access error: file /dev/dvd is empty, aborting
[00000297] cdda access error: could not read TOCHDR
[00000297] cdda access error: no audio tracks found
[00000292] main input error: no suitable access module for `dvd:///dev/dvd'
[00000283] main playlist: nothing to play
```


Thanks for the help in figuring this out.  kiddos really want to watch their DVD movies!  :)

---

### Post by mc4man on 2008-08-06
Put a dvd movie in the drive, let it settle (light on dvd goes steady or off) and run this in a terminal
```
sudo lshw -C disk
```

Can you play or access cd media from that drive like an audio cd or data cd?

---

### Post by bo_n_tulsa on 2008-08-06
mc4man, yes, I can read cd's, write cd's, play music, rip, the whole nine yards.  

Here's the output after inserting a DVD, allowing it to come to rest and then typing in terminal: sudo lshw -C disk:

```
  *-disk                  
       description: ATA Disk
       product: HDS728080PLAT20
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: PF2O
       serial: PFD212S2SMLGKD
       size: 76GiB (82GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=c6e09f94
  *-cdrom
       description: DVD reader
       product: IDE5216CO
       vendor: COMBO
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 0K52
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open
  *-disk:0
       description: SCSI Disk
       product: USB SD Reader
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdb
       version: 1.00
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       product: USB CF Reader
       vendor: Generic
       physical id: 0.0.1
       bus info: scsi@4:0.0.1
       logical name: /dev/sdc
       version: 1.01
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:2
       description: SCSI Disk
       product: USB SM Reader
       vendor: Generic
       physical id: 0.0.2
       bus info: scsi@4:0.0.2
       logical name: /dev/sdd
       version: 1.02
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:3
       description: SCSI Disk
       product: USB MS Reader
       vendor: Generic
       physical id: 0.0.3
       bus info: scsi@4:0.0.3
       logical name: /dev/sde
       version: 1.03
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde
```

---

### Post by mc4man on 2008-08-06
You may pursue other 'possible' fixes but the odds are your dvd drive is on the way out. It uses 2 different lasers, one for cd's, one for dvd's.
It appears the drive can't read dvd's anymore

> capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=open

open means no media detected, even with somewhat scuffed disks it should show this (for dvd movie or data dvd)
```
 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.[COLOR="Red"]fstype=udf[/COLOR] mount.options=ro,nosuid,nodev,[COLOR="Red"]relatime state=mounted status=ready[/COLOR]
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: [COLOR="Red"]mount.fstype=udf[/COLOR] mount.options=ro,nosuid,nodev,relatime [COLOR="Red"]state=mounted[/COLOR]
``` red for emphasis

you could try a dvd disk in known good shape (if those tried are suspect)  or buy some canned air and blow the drive out (open the tray and shoot in
  Otherwise i'd think odds are you need a new drive

---

### Post by bo_n_tulsa on 2008-08-06
Wow.  Ok, then.  Thanks!
At least I know I did everything right and it's just the hardware!  (in theory at this point, of course).
I'll try and get another one in tomorrow or this weekend and will report back if\when all is well.  I'm an optimist.  :)

---

### Post by mc4man on 2008-08-07
When you put in the new drive run the lshw -C disk comm. and see what your device node and /dev/links are. They may been 1 up from present, /dev/dvd1, /dev/cdrom1 ect.
You'll probably get /dev/scd0 so fstab isn't an issue
Most media players default to /dev/dvd or /dev/cdrom so easier to change your links than change in the app's preferences if they got 1 upped.

If so, remove old drive from ....70....cd.rules or better yet just delete the entries and reboot. Edit it back to this -
> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.


If you only have the new drive listed with dvd1 links ect. you can just remove the 1 in ...70...cd.rules from here - SYMLINK+="dvd1" ect.

Many new drives need or will work better on an 80 wire ide cable, you should ck. what you have now. (a 40 wire has obvious wires, 80 is fairly smooth. (not normally included in retail box of cd/dvd drives

---

