---
title: "DVD and permissions problems"
date: 2009-12-05
forum: Multimedia Software
---

### Post by jfl on 2009-12-05
Running 9.04 on a Thinkpad R61.

When I try to play a commercial DVD (instruction manual for an appliance) with the usual players, I get a message that I don't have the appropriate permissions.
Checking the DVD files, they are owned by "root". Of course, I cannot chmod since it is a DVD !!!
If I copy the DVD to a USB stick, I have no problem, since I am the owner.

The DVD plays fine on a windoze machine (p... me off :cry: )

I could use some utility that allows me to run the session as "root", but I don't like to do that ............... and** I shouldn't have to !**

IMO this is typically one of these minor problems that slows the expansion of Ubuntu.  Playing a DVD should be a no brainer.

---

### Post by SuperSonic4 on 2009-12-05
Have you installed *libdvdcss2*?

---

### Post by phgregory on 2009-12-05
> **SuperSonic4 said:**
> Have you installed *libdvdcss2*?
I have similar problem (Ubuntu 9.10 koala on Compaq Presario 2200). Does not mount the DVD at all. Mounts CD's fine.

When I try to install libdvdcss2, I get an error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

---

### Post by jfl on 2009-12-05
> **SuperSonic4 said:**
> Have you installed *libdvdcss2*?

Yes, I have the latest version available from the repo.
The DVD mounts fine, I can see the contents in the file browser, it just don't play.

---

### Post by jfl on 2009-12-07
Any ideas ???????????????

---

### Post by xc3RnbFO8P on 2009-12-07
Codecs to play DVD, MP3, Flash, AVI.... formats

> sudo wget \
  --output-document=/etc/apt/sources.list.d/medibuntu.list \
  http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list &&
sudo apt-get --quiet update &&
sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring &&
sudo apt-get --quiet update
> sudo apt-get install libdvdcss2
> sudo apt-get install w32codecs
> sudo apt-get install libdvdread4
> sudo /usr/share/doc/libdvdread4/install-css.sh
> sudo apt-get install ubuntu-restricted-extras
Need more codecs, search in Synaptic Package Manager:
faad
flac
quicktime
avifile
gecko-mediaplayer

---

### Post by jfl on 2009-12-07
Thanks for the answer, but it was not really my question.

My DVD will not play because they are owned by "root" and don't have the permissions.

If I copy the files to a stick and **change the permissions**, it works fine.
If I log in as "root" it works fine.

I don't think it is a matter of CODECs and *libdvdcss2* is installed.

For some reason, the system sees the DVD as owned by "root" and since it is not writable, I cannot chmod or chown even as root.

---

### Post by zkriesse on 2009-12-07
> **jfl said:**
> Thanks for the answer, but it was not really my question.

My DVD will not play because they are owned by "root" and don't have the permissions.

If I copy the files to a stick and **change the permissions**, it works fine.
If I log in as "root" it works fine.

I don't think it is a matter of CODECs and *libdvdcss2* is installed.

For some reason, the system sees the DVD as owned by "root" and since it is not writable, I cannot chmod or chown even as root.

Here. [help.ubuntu.com/playingdvd's]("https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html")

---

### Post by Saprissa on 2009-12-07
For me, the files on a mounted DVD are owned by root and file permissions are set (automatically) to "Access Files"  and "Read Only".

My fstab file looks like this.

> /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Perhaps your permissions are set differently in fstab?

---

### Post by jfl on 2009-12-07
> **Saprissa said:**
> For me, the files on a mounted DVD are owned by root and file permissions are set (automatically) to "Access Files"  and "Read Only".

My fstab file looks like this.

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0 

Perhaps your permissions are set differently in fstab?

Thanks for the reply !

My fstab is pretty similar:

```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```

I don't think the "utf8" would make a difference ???

---

### Post by mc4man on 2009-12-07
Maybe start a player from the terminal and post output, doesn;t matter which one

totem dvd://

vlc dvd://

Has this laptop ever had windows installed** and** playing dvd's? (in other words has a region been set ever?

---

### Post by jfl on 2009-12-07
> **mc4man said:**
> Maybe start a player from the terminal and post output, doesn;t matter which one

totem dvd://

vlc dvd://

Has this laptop ever had windows installed** and** playing dvd's? (in other words has a region been set ever?

Here it is:

```
jf@lenovo:~$ totem dvd://
/var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
** Message: no file info
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /dev/dvd
No such file or directory
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdread: Can't stat /dev/dvd
No such file or directory
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(333): rsn_dvdsrc_start (): /GstPlayBin:play/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: No such file or directory
```

and:

```
jf@lenovo:~$ vlc dvd://
VLC media player 0.9.9a Grishenko
[00000001] main libvlc debug: VLC media player - version 0.9.9a Grishenko - (c) 1996-2009 the VideoLAN team
[00000001] main libvlc debug: libvlc was configured with ./configure  '--build=i486-linux-gnu' '--enable-maintainer-mode' '--enable-release' '--prefix=/usr' '--enable-libtool' '--enable-fast-install' '--with-binary-version=2ubuntu1' '--disable-update-check' '--disable-gnome' '--disable-gtk' '--disable-familiar' '--disable-fb' '--enable-ggi' '--enable-sdl' '--enable-esd' '--enable-mad' '--enable-jack' '--enable-pulse' '--enable-lirc' '--enable-a52' '--enable-aa' '--enable-dvbpsi' '--enable-mozilla' '--with-mozilla-pkg=libxul-plugin' '--disable-kde' '--enable-mp4' '--enable-dvb' '--disable-satellite' '--enable-ogg' '--enable-vorbis' '--enable-shout' '--enable-qt4' '--disable-slp' '--enable-flac' '--disable-skins' '--disable-basic-skins' '--enable-skins2' '--enable-freetype' '--enable-mkv' '--enable-speex' '--enable-caca' '--enable-live555' '--enable-libmpeg2' '--enable-fribidi' '--enable-cdio' '--enable-mod' '--enable-theora' '--enable-modplug' '--enable-dvdnav' '--enable-gnutls' '--enable-ffmpeg' '--enable-ncurses' '--enable-smb' '--disable-gnomevfs' '--enable-bonjour' '--enable-mpc' '--enable-vcd' '--enable-vcdx' '--enable-notify' '--enable-twolame' '--enable-faad' '--disable-zvbi' '--enable-telx' '--enable-mediacontrol-bindings' '--disable-atmo' '--enable-taglib' '--enable-libass' '--enable-libdca' '--enable-realrtsp' '--disable-dv' '--enable-x264' '--enable-alsa' '--enable-v4l' '--enable-v4l2' '--enable-pvr' '--enable-svgalib' '--enable-dvd' '--without-dvdcss' 'build_alias=i486-linux-gnu' 'CFLAGS=-g -O2' 'LDFLAGS=-Wl,--as-needed' 'CPPFLAGS=' 'CXXFLAGS=-g -O2'
[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Found old config file at /home/jf/.vlc/vlcrc. VLC will now use /home/jf/.config/vlc/vlcrc.
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title:  
libdvdnav: DVD Serial Number: 
libdvdnav: DVD Title (Alternative):    
libdvdnav: Unable to find map file '/home/jf/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[00000376] main access error: no access module matched "dvd"
[00000374] main input error: open of `dvd://' failed: could not create access: no access module matched "dvd"
[00000001] main libvlc: Found old config file at /home/jf/.vlc/vlcrc. VLC will now use /home/jf/.config/vlc/vlcrc.
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav: DVD Title:  
libdvdnav: DVD Serial Number: 
libdvdnav: DVD Title (Alternative):    
libdvdnav: Unable to find map file '/home/jf/.dvdnav/.map'
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdnav: vm: failed to read VIDEO_TS.IFO
libdvdread: Using libdvdcss version 1.2.10 for DVD access
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:DVDOpenFileUDF:UDFFindFile /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
[00000379] main access error: no access module matched "dvd"
[00000377] main input error: open of `dvd://' failed: could not create access: no access module matched "dvd"
jf@lenovo:~$ 
```

Yes, when I bought it, widoze XP was installed, now on dual boot.
I believe I have played DVD on this machine under Ubuntu, didn't really use XP at all.

Any clues ???
Thanks

---

### Post by mc4man on 2009-12-07
run and post this ( only need entry under *-cdrom   ( do it with your dvd inserted

```
sudo lshw -C disk
```

---

### Post by jfl on 2009-12-07
> **mc4man said:**
> run and post this ( only need entry under *-cdrom   ( do it with your dvd inserted

```
sudo lshw -C disk
```

Here you go:

```
 *-cdrom                 
       description: DVD reader
       product: DVD/CDRW UJDA770
       vendor: MATSHITA
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 1.04
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
```

---

### Post by mc4man on 2009-12-07
>  vendor: MATSHITA

Matshita drives strictly enforce region encoding, ( not required, but they do it anyway

If there is a region mismatch then access to the drive is refused, if no region is set then probably the same.

What's curious here is it's very possible the dvd has no encryption or region setting, being a "instruction manual for an appliance"

The best you can do is ck. whether the drive has a region set. ( only needs to be done once, use what region you're in 

There is no way to play **region mismatches** with most matshita laptop drives

to ck.
```
sudo apt-get install regionset
```

With a disk in the drive run
```
regionset
```

If the 4th line says type: NONE, then you need to set a region, if it says type: SET then answer n and exit ( but note what region is set ( line 7

Do you know your region? ( I'll edit in a list in a few


1 = North America (USA and Canada)
2 = Europe, Middle East, South Africa and Japan
3 = Southeast Asia, Taiwan, Korea
4 = Latin America, Australia, New Zealand
5 = Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
6 = China

---

### Post by jfl on 2009-12-07
Here is the output:

```
jf@lenovo:~$ sudo apt-get install regionset
[sudo] password for jf: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libpt-1.10.10-plugins-alsa libpt-1.10.10 libpt-1.10.10-plugins-v4l
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  regionset
0 upgraded, 1 newly installed, 0 to remove and 18 not upgraded.
Need to get 11.5kB of archives.
After this operation, 73.7kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com jaunty/universe regionset 0.1-3 [11.5kB]
Fetched 11.5kB in 0s (14.9kB/s)  
Selecting previously deselected package regionset.
(Reading database ... 155743 files and directories currently installed.)
Unpacking regionset (from .../regionset_0.1-3_i386.deb) ...
Processing triggers for man-db ...
Setting up regionset (0.1-3) ...
jf@lenovo:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.
```

---

### Post by mc4man on 2009-12-07
> Please ensure there is a readable CD or DVD in the drive.
You need to have a disc in the drive, doesn't matter what kind as long as it's not a blank disc.

If you had one and got that response then try another disk.

---

### Post by jfl on 2009-12-07
> **mc4man said:**
> You need to have a disc in the drive, doesn't matter what kind as long as it's not a blank disc.

If you had one and got that response then try another disk.

I have the "Appliance manual" DVD in the drive.
I tried it on a windoze machine and it works fine.
I can explore it in Nautilus, I just did it again.

BTW, I am in region 1 (South Florida)

---

### Post by jfl on 2009-12-07
Here is the output of ls -l  (partial), so the disk is read:

```
jf@lenovo:/cdrom/VIDEO_TS$ ls -l
total 1794782
-r-xr-xr-x 1 root root     53248 2007-12-14 18:06 VIDEO_TS.BUP
-r-xr-xr-x 1 root root     53248 2007-12-14 18:06 VIDEO_TS.IFO
-r-xr-xr-x 1 root root      8192 2007-12-14 18:06 VIDEO_TS.VOB
-r-xr-xr-x 1 root root     18432 2007-12-14 18:06 VTS_01_0.BUP
-r-xr-xr-x 1 root root     18432 2007-12-14 18:06 VTS_01_0.IFO
-r-xr-xr-x 1 root root      8192 2007-12-14 18:06 VTS_01_0.VOB
-r-xr-xr-x 1 root root  52445184 2007-12-14 18:06 VTS_01_1.VOB
-r-xr-xr-x 1 root root     34816 2007-12-14 18:06 VTS_02_0.BUP
-r-xr-xr-x 1 root root     34816 2007-12-14 18:06 VTS_02_0.IFO
-r-xr-xr-x 1 root root   7776256 2007-12-14 18:06 VTS_02_0.VOB
-r-xr-xr-x 1 root root  56086528 2007-12-14 18:06 VTS_02_1.VOB
-r-xr-xr-x 1 root root     18432 2007-12-14 18:06 VTS_03_0.BUP
-r-xr-xr-x 1 root root     18432 2007-12-14 18:06 VTS_03_0.IFO
-r-xr-xr-x 1 root root      8192 2007-12-14 18:06 VTS_03_0.VOB
-r-xr-xr-x 1 root root  73592832 2007-12-14 18:06 VTS_03_1.VOB
-r-xr-xr-x 1 root root     34816 2007-12-14 18:06 VTS_04_0.BUP
-r-xr-xr-x 1 root root     34816 2007-12-14 18:06 VTS_04_0.IFO
-r-xr-xr-x 1 root root  92227584 2007-12-14 18:06 VTS_04_0.VOB
-r-xr-xr-x 1 root root 107481088 2007-12-14 18:06 VTS_04_1.VOB
-r-xr-xr-x 1 root root     18432 2007-12-14 18:06 VTS_05_0.BUP
.....................
.....................

```

---

### Post by jfl on 2009-12-07
Getting really weird.

Put in a movie DVD.

In Movie Player I get an error pop-up: "Could not determine type of stream."

In VLC it plays normally for 20-30 seconds, then it crashes and I am logged out.  I have to enter my user ID and pw again  ](*,)

Going to bed now,thanks to all who responded, see you tomorrow.

---

### Post by jack frost on 2009-12-08
> **ZachK_ said:**
> Here. [help.ubuntu.com/playingdvd's]("https://help.ubuntu.com/9.10/musicvideophotos/C/video-dvd.html")

thanks i went to that link and dvd plays fine in totem..

---

### Post by afrodeity on 2011-01-13
> **Saprissa said:**
> For me, the files on a mounted DVD are owned by root and file permissions are set (automatically) to "Access Files"  and "Read Only".

My fstab file looks like this.



Perhaps your permissions are set differently in fstab?

my fstab is exactly the same, can only play the DVD if I am root.

Looks like it could be a problem of how the disk is being mounted. I tried acidrip, it gave this message:

```

AcidRip message - AcidRip 0.14, "Written" by C.Phillips <acid_kewpie@users.sf.net>
AcidRip message - Reading DVD / file(s)... please wait
AcidRip message - /dev/dvd does not exist!
AcidRip message - Reading DVD / file(s)... please wait
AcidRip message - /dev/dvd does not exist!

```

/dev only shows /dev/dvd1 and /dev/dvdrw1 also cdrom is cdrom1 however there is an scd0 as per the fstab, anyone know what's going on?

---

### Post by mc4man on 2011-01-13
> /dev only shows /dev/dvd1 and /dev/dvdrw1 also cdrom is cdrom1 however there is an scd0 as per the fstab, anyone know what's going on?

It's not uncommon for /dev/sr0 (scd0) to get /dev links of /dev/dvd1, /dev/cdrom1, ect.
Many apps will default to /dev/dvd and or /dev/cdrom

You can either adjust the default in the app or you can change the dev link(s)

For the latter run and post
```
sudo lshw -C disk
```
and from a maximized terminal
```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by afrodeity on 2011-01-14
```
sudo lshw -C disk
[sudo] password for afrodeity: 
  *-cdrom                 
       description: DVD-RAM writer
       product: CDDVDW SH-S202N
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: SB01
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,utf8 state=mounted
  *-disk:0
       description: ATA Disk
       product: SAMSUNG HD200HJ
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: KF10
       serial: S16KJDWPC00357
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=213e213e
  *-disk:1
       description: ATA Disk
       product: ST3500418AS
       vendor: Seagate
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: CC34
       serial: 5VM1BRMF
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0009fdb2

```

```


cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# CDDVDW_SH-S202N (pci-0000:00:0f.1-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"

# CDDVDW_SH-S202N (pci-0000:00:1f.1-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"

```

---

### Post by mc4man on 2011-01-14
As you can see the drive is duped in the rules file and lshw is showing it's getting the 1 links (/dev/dev1 ect.

run this and edit the rules files as shown below (in this case just removing both entries completely
Then do a re boot and the drive should be reset using the the default links /dev/dvd, ect.

```
gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
```

after rebooting you can ck. by either running the lshw or checking the rules file
If it isn't set to /dev/dvd ect. then post back and we'll just change the links directly (shouldn't be necessary

---

### Post by afrodeity on 2011-01-15
@mc4man sorry I am completely ignorant about edition the udev but which lines should I remove? Will the be regenerated or do I add something?

---

### Post by afrodeity on 2011-01-15
My eyes are rested and I noticed "in this case just removing both entries completely" which could only mean remove everything below the two comments:

# CDDVDW_SH-S202N (pci-0000:00:0f.1-scsi-0:0:0:0)

and 

# CDDVDW_SH-S202N (pci-0000:00:1f.1-scsi-0:0:0:0)

I removed both entries and rebooted, now there is only one entry and Acidrip works without a hitch. Drive permissions for the disk in question are still locked or only able to open with root. I was able to rip the disk to file which is useful.

---

