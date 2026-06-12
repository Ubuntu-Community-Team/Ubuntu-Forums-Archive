---
title: "DVDs don't play"
date: 2010-06-27
forum: Multimedia Software
---

### Post by darkness_hacker on 2010-06-27
I have all of the necessary libraries installed already: libdvdcss2, libdvdread4, etc. When I try to play a dvd video with VLC I get:
```
 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/sr0".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/sr0'. Check the log for details.[/COLOR]
 

```Also when I put a dvd video in the drive the icon does not show up on my desktop like it does when I put a data dvd in.

---

### Post by NM5TF on 2010-07-24
I have a similar problem with VLC trying to play commercial DVDs, but get a slightly different error code as follows:

Playback failure:
DVDRead could not open the disc "&#65533;&#65533;&#65533;	&#65533;&#65533;&#65533;	 &#65533;&#65533;	&#65533;&#65533;	".
Your input can't be opened:
VLC is unable to open the MRL 'dvd://&#65533;&#65533;&#65533;	&#65533;&#65533;&#65533;	 &#65533;&#65533;	&#65533;&#65533;	'. Check the log for details.

dmesg | tail gives the following:


tommy@tommy-desktop:~$ dmesg | tail
[   26.230692] HDA Intel 0000:00:05.0: setting latency timer to 64
[   26.924017] hda_codec: ALC888: BIOS auto-probing.
[   27.121784] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   27.121788] apm: disabled - APM is not SMP safe.
[   27.148131] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:05.0/input/input5
[   35.124013] eth1: no IPv6 routers present
[   46.690376] ppdev: user-space parallel port driver
[   48.111308] usb 2-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[  167.513160] UDF-fs: No anchor found
[  167.513166] UDF-fs: No partition found (1)

the problem seems to be associated with UDF....the same thing happened
when upgrading from 8.10 to 9.10, but I have forgotten the fix for it...

it worked fine until I upgraded to Lucid Lynx LTS  :(

VLC works great for playing Audio CDs':p

any help will be appreciated

Tom

---

### Post by wojox on 2010-07-24
Have you tried

```
sudo apt-get install libdvdread4
```

```
 sudo /usr/share/doc/libdvdread4/install-css.sh
```

Reboot.

---

### Post by NM5TF on 2010-07-24
did the sudo apt-get install libdvdread4 and got this:

tommy@tommy-desktop:~$ sudo apt-get install libdvdread4
[sudo] password for tommy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-thread1.40.0 libboost-date-time1.40.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

then did sudo /usr/share/doc/libdvdread4/install-css.sh and got this:

tommy@tommy-desktop:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
--2010-07-24 20:50:34--  [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8068 (7.9K) [application/octet-stream]
Saving to: `/tmp/dvdcss-whxffV/Packages'

100%[======================================>] 8,068       32.7K/s   in 0.2s    

2010-07-24 20:50:35 (32.7 KB/s) - `/tmp/dvdcss-whxffV/Packages' saved [8068/8068]

--2010-07-24 20:50:35--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38036 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-whxffV/libdvdcss.deb'

100%[======================================>] 38,036      55.7K/s   in 0.7s    

2010-07-24 20:50:37 (55.7 KB/s) - `/tmp/dvdcss-whxffV/libdvdcss.deb' saved [38036/38036]

(Reading database ... 206922 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-whxffV/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

will reboot & see what happens....;)

---

### Post by NM5TF on 2010-07-24
stil a NO GO....VLC gives me this error:

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

any ideas???  :confused:

---

### Post by mc4man on 2010-07-25
> any ideas???
unfortunately nothing to say - 'this will fix it.'

Your problem seems to be that while your drive is being seen and that media is being detected on it, no filesystem is being found and mounted.

No player can play 'what isn't there', so this isn't a lib or codec issue whatsoever.

You can play audio cd's because they don't contain a mountable filesystem - they are accessed at a 'location', basically ~/.gvfs/cdda mount on sr[COLOR="Blue"]X[/COLOR] ( or scd[COLOR="Blue"]X[/COLOR]

Since you updated you still have an fstab entry, and should have the mountpoint (probably /media/cdrom0 ), otherwise there'd be a mount error.
(might as well d. ck. fstab and for /media/cdrom[COLOR="Blue"]X[/COLOR] (most likely 0

cat /etc/fstab

For info sake maybe leave the dvd in the drive and reboot, then post 
```
sudo lshw -C disk
```

and (maximize terminal first
```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by NM5TF on 2010-07-25
the mount point looks good as it shows /media/cdrom0

I then put the DVD in reader & rebooted as you asked, then ran the 3 commands as asked...here are the results:

tommy@tommy-desktop:~$ sudo lshw -C disk
[sudo] password for tommy: 
  *-disk                  
       description: ATA Disk
       product: ST3250820AS
       vendor: Seagate
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.AD
       serial: 9QE6BNNK
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=d8000000
  *-cdrom
       description: DVD reader
       product: CDRWDVD DH-48C2S
       vendor: PBDS
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: ND12
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
tommy@tommy-desktop:~$ cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
#  (pci-0000:00:08.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:08.0-scsi-1:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:08.0-scsi-1:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:08.0-scsi-1:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
tommy@tommy-desktop:~$ cat /etc/fstab
UUID=bdf019d6-cb10-4688-af02-e605ef77b8e7 / ext3 defaults 0 1
UUID=8ab28302-3d42-49ea-9a00-4d6101a3f1a1 swap swap sw 0 0

anything look odd to you???

---

### Post by mc4man on 2010-07-25
> anything look odd to you
Not really, other than it looks like upgrade to 10.04 is now creating a new fstab without a cdrom device entry.

The real issue is seen here in the lshw
> configuration: ansiversion=5 [COLOR="Blue"]status=ready[/COLOR]
status=ready means that media is in the drive, no filesystem detected
(you'd see the same if you had an audio cd or blank media in the drive.

you could try ading an fstab entry - may  not matter, may help. if so then go  
```
gksu gedit /etc/fstab
```

and add this directly below last line,  save and reboot
```
/dev/sr0     /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

If no go then likely cause is an issue with drive itself - but there are some where the drive will work in earlier than 10.04 but not in 10.04, you may fall into that category (udisks related

---

### Post by NM5TF on 2010-07-25
editing /etc/fstab and adding the command line as you suggested has 
FIXED the problem!!!

this is the same "fix" I had to do when upgrading from 8.10 to 9.10,
but I couldn't remember it....I have written it down for future reference
when next "upgrade" comes around....

is this a bug in Ubutunu that needs to be reported???

thanx so much mc4man, you certainly know your "stuff"!!!!;)

Tom

p.s. sounds like darkness_hacker might have the same prob......

---

### Post by mc4man on 2010-07-26
> editing /etc/fstab and adding the command line as you suggested has
FIXED the problem!!!

Glad it did so - for many adding the fstab line showed no improvement so consider yourself fortunate

> is this a bug in Ubutunu that needs to be reported???I'm sure there are various bug reports - you could ck.
The problem is the causes and solutions (if any), are varied

( personally, even tough I don't need fstab entries for my drives, I create them and mount directories any way - like having a consistent mountpoint with known mount options

---

