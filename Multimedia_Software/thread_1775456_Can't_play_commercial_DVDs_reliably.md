---
title: "Can't play commercial DVDs reliably"
date: 2011-06-04
forum: Multimedia Software
---

### Post by Jaguarandine on 2011-06-04
Hi, I recently installed Lubuntu 11.04 on my aunt's old computer (Sony PCV-LX800); I had it running Ubuntu for a few years but the latest releases are too much for it to bear. Anyway, a while back I installed a DVD-ROM drive in her computer in order to play DVD movies. It plays CDs and non-commercial DVDs fine, but with the commercial DVDs, it doesn't work 80% of the time. The 20% it does work, everything is fine. 

I've installed all the necessary packages with every new release. Currently using the following: libdvdcss, libdvdnav4, and libdvdread4 (via the Medibuntu repository).

Here's some info from this system while trying to play the DVD LotR: Return of the King Extended Edition:
```
gloria@gloria-PCV-LX800-U:~$ mplayer dvd://1
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
Couldn't open DVD device: /dev/dvd (No medium found)
No stream found to handle url dvd://1


Exiting... (End of file)
--------------------------------
(pasted relevant info from lshw command)
*-cdrom
                description: DVD reader
                product: DVD-ROM DVD-115
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.11
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc
--------------------------------------
gloria@gloria-PCV-LX800-U:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d546be64-a900-4234-bf51-d725c9d0316a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=cf9c0090-ef49-454d-bd60-95f822fac920 none            swap    sw              0       0
-------------------------------------------
gloria@gloria-PCV-LX800-U:~$ vlc /dev/dvd
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x9d16914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setenv("ORBIT_SOCKETDIR", "/tmp/orbit-gloria", 1)
Warning: call to srand(1307110691)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:2824): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Could not open /dev/dvd with libdvdcss.
libdvdread: Can't open /dev/dvd for reading
libdvdnav: vm: failed to open/read the DVD
[0xa03ed94] filesystem access error: failed to read (Input/output error)
[0xa03ee74] main stream error: cannot pre fill buffer

```

This drive worked fine in my old Windows 2000 PC, so I'm at a lost with why there is a problem. Thanks for your help!

---

### Post by whatthefunk on 2011-06-04
I have the exact same problem and Im also running Lubuntu.

---

### Post by mc4man on 2011-06-04
> **Jaguarandine said:**
>  It plays CDs and non-commercial DVDs fine, but with the commercial DVDs, it doesn't work 80% of the time. The 20% it does work, everything is fine. 

I've installed all the necessary packages with every new release. Currently using the following: libdvdcss, libdvdnav4, and libdvdread4 (via the Medibuntu repository).

Here's some info from this system while trying to play the DVD LotR: Return of the King Extended Edition:

(pasted relevant info from lshw command)
*-cdrom
                description: DVD reader
                product: DVD-ROM DVD-115
                vendor: PIONEER
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.11
                capabilities: removable audio dvd
                configuration: ansiversion=5 [COLOR="Red"]status=nodisc[/COLOR]


If the dvd was in the drive when you ran the lshw then the red is a bit of a problem. While ideally the media is detected and the udf file system mounted, the latter isn't critical, the former is.
So normally you'd see something like this, (the blue you may not see, not really important - 
>  configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,[COLOR="Blue"]uid=1000,gid=1000,umask=77,dmode=500,iocharset=[/COLOR]utf8 state=mounted


but even just this would allow playback of DVD Video disks - 
> configuration: ansiversion=5 status=ready

Was the disk in the drive when doing the lshw?

---

### Post by Jaguarandine on 2011-06-04
Yup, that's right.

---

### Post by whatthefunk on 2011-06-06
Bump

Anybody?

---

### Post by mahmoodkamal on 2011-06-06
have you tried VLC?

---

### Post by whatthefunk on 2011-06-06
I dont know about the OP, but Ive tried VLC, MPlayer, and Totem-xine.  All gave similar error messages.

---

### Post by Jaguarandine on 2011-06-06
> **mahmoodkamal said:**
> have you tried VLC?

Yes, I did. Check the terminal output that I posted.

---

### Post by mc4man on 2011-06-06
> **Jaguarandine said:**
> Yup, that's right.

Honestly - there isn't any generic solution here. There have been a number of threads over the last year or so with basically the same. In some cases the Op has gotten lucky and found a way to get the media recognized, in many cases nothing worked short of a drive replacement.

I could dig up some threads if you'd like, you never know, though certainly a longshot.

If the media isn't found then there is no way to play, has nothing to do with the players used or playback related libs/codecs installed.

Edit: some thing that shouldn't matter - but..
Check that a region is set on drive - with any 'readable'  disc in drive
regionset
line 4 will show

check that the drive isn't duped or a non xistent one listed in 
gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules

if more than one entry for current drive than delete all the entries and restart
(delete all below this line
add the ENV{GENERATED}=1 flag to your own rules as well.

Try booting up with problem dvd in drive 
 ck. /var/log/syslog and dmesg after inserting problem disk and or above

grep CD-ROM /var/log/syslog
dmesg |tail

Create a  mountpoint (sudo mkdir /media/cdrom0) and add a typical fstab entry for the drive

```
/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0      0
```

---

### Post by Jaguarandine on 2011-06-08
Well, thanks for the advice. I'll be checking this tonight after work.

---

### Post by Jaguarandine on 2011-06-09
I don't quite understand the output from the file so I'll post it here along with everythinng else.

```
gloria@gloria-PCV-LX800-U:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
--------------------------------
gloria@gloria-PCV-LX800-U:~$ gksudo leafpad /etc/udev/rules.d/70-persistent-cd.rules

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# Pioneer_DVD-ROM_ATAPIModel_DVD-115_0111 (pci-0000:00:00.1-scsi-1:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:00.1-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:00.1-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
---------------------------------
(I've left the DVD in the drive the whole time so I didn't reboot)
gloria@gloria-PCV-LX800-U:~$ grep CD-ROM /var/log/syslog
Jun  9 05:48:11 gloria-PCV-LX800-U kernel: [    1.502149] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-ROM DVD-115  1.11 PQ: 0 ANSI: 5
Jun  9 05:48:11 gloria-PCV-LX800-U kernel: [    1.504906] cdrom: Uniform CD-ROM driver Revision: 3.20
Jun  9 05:48:11 gloria-PCV-LX800-U kernel: [    1.505458] sr 1:0:0:0: Attached scsi CD-ROM sr0
------
gloria@gloria-PCV-LX800-U:~$  dmesg |tail
[   40.952879] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   43.109694] wlan0: authenticate with 00:24:01:72:aa:b3 (try 1)
[   43.112767] wlan0: authenticated
[   43.112899] wlan0: associate with 00:24:01:72:aa:b3 (try 1)
[   43.115433] wlan0: RX AssocResp from 00:24:01:72:aa:b3 (capab=0x431 status=0 aid=1)
[   43.115450] wlan0: associated
[   43.117854] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   46.238387] Intel AES-NI instructions are not detected.
[   46.261241] padlock_aes: VIA PadLock not detected.
[   53.952105] wlan0: no IPv6 routers present

```

Do I need to restart after creating the mountpoint? How does this work exactly? Also, in my previous searches, I saw reference to the "all_generic_ide" parameter. How would this work with grub 2 and is this a possible solution? 

Thank you for all your help so far.

---

### Post by mc4man on 2011-06-09
Unfortunately everything you posted looks fine, odds where that they would.

As far as regionset, it failed because you either had no media in the drive or one or your problem discs,
"Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive."

Odds are it won't matter, but to retry make sure you have any disc that is recognized (audio, data cd, data dvd, ect.

If trying the static mount then yes, after creating mount dir. and adding fstab entry you need to restart.

Likely are no matter what you try those disks will remain undetected with that drive

---

### Post by coldraven on 2011-06-10
Try cleaning the CD lens, recently I had three brand new DVDs and only one would play.
I cleaned the lens then two would play, I had to clean again to get all three working.
I used a cotton bud and meths to get the nicotine off! *cough*

I don't know if this would help, in my case the lens looked clean to start with.

---

