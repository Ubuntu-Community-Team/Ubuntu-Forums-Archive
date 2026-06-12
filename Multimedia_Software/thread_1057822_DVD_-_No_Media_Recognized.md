---
title: "DVD - No Media Recognized"
date: 2009-02-02
forum: Multimedia Software
---

### Post by timmil on 2009-02-02
Hi, been having a problem with my cd/dvd combo drive not recognizing DVD media since I installed 8.10. Everything on the machine works well, audio, video, webcam, etc... But for some reason the system will not recognize DVD when I place them in the drive. (Should note data and audio cd's work fine). At first I thought this might be an issue with the dvd but all the DVD's work fine on another system (Windoze) but for what ever reason 8.1- will not mount the dvd. I try to mount the drive manually and I get:

sudo mount /dev/dvd /media/dvd
mount: No medium found

I ran the lshw -C disk (dvd in drive) and I get the following info

  *-cdrom
       description: DVD reader
       physical id: 0.1.0
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       capabilities: audio dvd
       configuration: status=nodisc

I am stumped at this point. I have installed all of the codecs, dvd libraries and it won't recognize the media in the drive. If I open file browser for My Computer it shows it as a CD-ROM/DVD-ROM Drive, it just doesn't recognize when a dvd is inserted.

If anyone has any ideas, please let me know.

Thanks!
- Tim

---

### Post by redroad55 on 2009-02-02
Just wondered if this may apply..

> DVD PLAYBACK


ZERO DVD PLAYBACK

Installed the necessary applications and packages but still cannot play/rip commercial DVDs? Perhaps you should make sure the DVD drive has been set to the correct region. If you have never successfully played DVDs in Ubuntu or Windows, install the following command line based application:

sudo apt-get install regionset

Please be aware that most drives limit you to about 5 changes (regionset should tell you how many you have left), so if you plan to watch foreign DVDs, it would be best to have a secondary external DVD drive, and have it set to a different region to the one in your machine. To set or change your DVD drives region, put any disc into your drive, and type "sudo regionset" into the terminal, then simply select the relevant region code. Here is the list of region codes and which countries they cover:

RC1 = North America (USA and Canada)
RC2 = Europe, Middle East, South Africa and Japan
RC3 = Southeast Asia, Taiwan, Korea
RC4 = Latin America, Australia, New Zealand
RC5 = Former Soviet Union (Russia, Ukraine, etc.), rest of Africa, India
RC6 = China

For those of you who previously played DVDs in GNU/Linux or Windows, but for some reason are unable to now, it could be related to faulty leads/connectors, but give this one last software-related method a try:

sudo apt-get install build-essential debhelper fakeroot

then:

sudo /usr/share/doc/libdvdread3/install-css.sh

or if you get an error with that command:

sudo /usr/share/doc/libdvdread3/examples/install-css.sh


Post back with results and or further questions .. Best to you

---

### Post by timmil on 2009-02-02
Intalled regionset but it will not allow me to set the region unless I have a readable CD or DVD in the drive. ( I will admit have not tried with a cd in there). I ran the install-css.sh script and got the following output:

--2009-02-02 07:58:32--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.2medibuntu1_i386.deb)
Resolving packages.medibuntu.org... 88.191.79.39, 88.191.82.11
Connecting to packages.medibuntu.org|88.191.79.39|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 36812 (36K) [application/x-debian-package]
Saving to: `/tmp/dvdcss-T10419/libdvdcss.deb'

100%[======================================>] 36,812      73.5K/s   in 0.5s    

2009-02-02 07:58:33 (73.5 KB/s) - `/tmp/dvdcss-T10419/libdvdcss.deb' saved [36812/36812]

(Reading database ... 181159 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.2medibuntu1 (using .../dvdcss-T10419/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.2medibuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Then I tried playing a dvd using vlc /dev/dvd and got

libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: vm: failed to open/read the DVD
[00000414] vcd access error: could not read TOCHDR
[00000414] vcd access error: no movie tracks found
[00000414] access_file access error: read failed (Input/output error)
[00000418] main stream error: cannot pre fill buffer
^C[00000402] signals interface error: Caught Interrupt signal, exiting...

---

### Post by redroad55 on 2009-02-02
Just to make sure go to software sorces and make sure under third party tab Medibuntu is there and under updates tab check "unsupported updates (backports)" .. Then post back with results and or questions..

---

### Post by timmil on 2009-02-02
I want to enable the backports, but the last time I did that it failed installation on some packages and hosed up my machine, so I am very leary of doing that again.

---

### Post by redroad55 on 2009-02-02
I understand hosing baaad .. Is Medibuntu repository available in software sources ? .. Also what version of Ubuntu are you currently running .. This link will make Medibuntu Repository available if you don't have it there..
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

as to the backports hosing if you run into the instance where certain pkgs. don't install back track removing the ones that did and figure out why or write down the recommended installations and install through synaptic..I personally have never had a problem with backports ofcorse I'm not saying they don't exist .. one more thing I think there is a conflict on your machine between xine and VLC ..Will try to work that out later .. but for now medibuntu or not?..Post back

---

### Post by Cscoundrel on 2009-02-02
i ran  into the same  problem  with  8.04 and then  my friend installed 8.10 and it  helped  him out when  he ran into this  problem  download vlc media player and the  codec  pack  could  quiet  possibly  fix  your problem 

 % sudo apt-get update
% sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

---

### Post by timmil on 2009-02-05
Ok, things got crazy and I have been unable to update on to what has happened....

The issue with backports... My bad. They are enabled it was pre-released that I was thinking of.

Installation if vlc and related plugins... Installed them first thing. VLC is up and works fine.

So still at a stand still. Insert an audio CD and it works, insert a DVD and still no media found.

I am at a loss

---

### Post by redroad55 on 2009-02-06
Follow this thread it gives you all you need:[http://ubuntuforums.org/showthread.php?t=1052799]("http://ubuntuforums.org/showthread.php?t=1052799")

Best to you

---

### Post by mc4man on 2009-02-06
That link above is more for hardy and in that case lshw is showing dvd media in the drive.

If running sudo lshw -C disk with a dvd in the drive returns 
> configuration: status=nodisc
then no codec, lib, or mount command is going to make a bit of difference. (you can't mount, play, or read what in essence doesn't exist.

Try again with inserting a dvd and running the lshw. (preferably with dvd in good condition and with a known file system, like a commercial dvd movie.
If no change you may want to get some canned air and blow out the drive and see if that helps.
It's certainly possible that a drive that's failing or dirty can read cd's and not dvd's.

---

### Post by jaqrah on 2009-02-06
Hello, I am having the same issue as Timmil. 

mc4man I have run ...sudo lshw -C disk

Here is my output for both dvd drives:

 *-cdrom:0               
       description: DVD reader
       product: DVD-ROM TS-H352C
       vendor: TSSTcorp
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: DE02
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc
  *-cdrom:1
       description: DVD writer
       product: DVD+-RW ND-3530A
       vendor: _NEC
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/cdrom0
       version: 103C
       serial: [_NEC    DVD+-RW ND-3530A103C05062200
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted

As you can see cdrom0 (with no disc)= no disc
cdrom1 (with commercial dvd)= ready,  yet both Totem & VLC freeze up and refuse to play.

---

### Post by jaqrah on 2009-02-06
I cliked on the dvd image on the desktop and clicked properties.  I noticed it has the wrong mount point for the drive.  Even though dvd is in cdrom1, it is mounted to cdrom0.  This could be the reason why it isn't playing.

Matter of fact, as I try the dvd in both drives here is the issue:

cdrom0 mountpoint: /media/I_Sleep_When_Im_Dead
cdrom1 mountpoint: /media/cdrom0

Dvd image: Properties: Drive: there is a settings option where I can change the mount point.  Is this a good idea?

---

### Post by mc4man on 2009-02-06
@jaqrah
first don't confuse 
> *-cdrom:0 
with 
 > logical name: /dev/cdrom1
> logical name: /media/cdrom0
The reason vlc and totem are freezing isn't caused by the mount points or /dev links.

It may be better to square some things up first though. ( or skip to "Otherwise"

I don't know if your comfortable opening up your pc box and taking a look at some things but if so.. 

The dvd reader, DVD-ROM TS-H352C, is in the master position (*-cdrom:0 , /dev/scd0) and the dvd writer, DVD+-RW ND-3530A, is in a slave position.(*-cdrom:1 /dev/scd1 

That is fine if they are on separate ide cables (probably not so in your case

If they're on the same ide cable then you would switch positions, the nec should be on the end connector and jumpered to master.
The reader would then go on the middle connector and be jumpered to slave.

If you do open up the case it would also be good to know what type of ide cables you have
80 wire - very smooth, wires hard to see
40 wire - distinct wires
cable select - horizontal 'splits' in the cable

Your probably missing an fstab entry so post this
```

cat /etc/fstab
```

also would like to see this

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

As far as the lshw, ect. for some understanding,
*-cdrom:0  is the first drive (master position) and is always assigned /dev/scd0

/dev/dvd, /dvd/cdrom, ect. are just links to the device and always assigned to the mastered drive on the secondary ide

/dev/dvd1, /dev/cdrom1 ect. are assigned to the slave drive (except when you have drives on separate ide cables, then these links go to the drive mastered on the primary ide (which will be /dev/scd0

/media/cdrom0, /media/<volume name> are the mount points

When there is no fstab entry the media will mount by default to /media/<volume name>

You may also wish to post this

```
grep ' UDMA' /var/log/dmesg
```

Otherwise

Put a dvd in the nec, start vlc from the terminal with (if your using vlc 0.8.6 )
```
vlc
```  or (if your using vlc 0.9.x
```
vlc-vv 
```
Go file or media 'open disc' and point vlc to /dev/scd1

Or ( with media in either drive) open vlc from terminal as above
Browse to /media/..., grab the VIDEO_TS and drag onto vlc

---

### Post by jaqrah on 2009-02-06
mc4man..thanks for your lengthy reply.  As I was looking through things later, I realized I had posted my "epiphany" a little too hastily. I was confusing the cdrom.

I opened up my box.  The dvd drives are not on separate cables, as you thought.  There are two set of cable connected to the drives, the red/white/black going to the power supply and the grey ribbon which appears to be 40 wire  Is it the grey ribbon cable you are suggesting to swap around ? I am not sure that I can given how the cable is jumped from one drive to the other.  Also, if I switch the ribbon cable, do I have to switch the power supply cables?  Since I am dualbooting with XP, will this cause problems with the XP os?  And finally, would it be easier to just swap the physical positions of the drives?

Here is the output from: cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=e331a042-ffa4-4f27-bd56-ca3189493fd3 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=ee7abee8-dec0-40bb-b2fd-84cfcd7da114 /home           ext3    relatime        0       2
# /dev/sda7
UUID=cfb62042-4f98-4d47-ad81-8077c8279e35 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


Here is the output from:  cat /etc/udev/rules.d/70-persistent-cd-rules

# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
#  (pci-0000:00:1f.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
#  (pci-0000:00:1f.1-scsi-0:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:1:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.1-scsi-0:0:1:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"


Here is the output from:  grep ' UDMA' /var/log/dmesg


[    4.528868] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    4.528875] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    4.724511] ata1.00: ATAPI: TSSTcorpDVD-ROM TS-H352C, DE02, max UDMA/33
[    4.724552] ata1.01: ATAPI: _NEC DVD+/-RW ND-3530A, 103C, max UDMA/33
[    4.760452] ata1.00: configured for UDMA/33
[    4.780483] ata1.01: configured for UDMA/33
[    4.952755] ata3: SATA max UDMA/133 cmd 0xfe00 ctl 0xfe10 bmdma 0xfea0 irq 20
[    4.952762] ata4: SATA max UDMA/133 cmd 0xfe20 ctl 0xfe30 bmdma 0xfea8 irq 20
[    5.236865] ata3.00: ATA-7: ST3160828AS, 8.04, max UDMA/133
[    5.237315] ata3.01: ATA-8: ST31000340AS, SD15, max UDMA/133
[    5.252368] ata3.00: configured for UDMA/133
[    5.269163] ata3.01: configured for UDMA/133


Lastly, I opened Vlc from terminal.  I browsed Media and pointed vlc to /dev/scd1.  The terminal window was still open so I thought I would post result.

[00000001] main libvlc debug: translation test: code is "C"
[00000001] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: I_SLEEP_WHEN_IM_DEAD
libdvdnav: DVD Serial Number: 31346BDA
libdvdnav: DVD Title (Alternative): I_SLEEP_WHEN_IM_DEAD
libdvdnav: Unable to find map file '/home/jaq/.dvdnav/I_SLEEP_WHEN_IM_DEAD.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Using dvdnav version 4.1.2 from [http://dvd.sf.net](http://dvd.sf.net)
libdvdnav: DVD Title: I_SLEEP_WHEN_IM_DEAD
libdvdnav: DVD Serial Number: 31346BDA
libdvdnav: DVD Title (Alternative): I_SLEEP_WHEN_IM_DEAD
libdvdnav: Unable to find map file '/home/jaq/.dvdnav/I_SLEEP_WHEN_IM_DEAD.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1
libdvdnav: Suspected RCE Region Protection!!!

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***
*** for info_length % sizeof(uint32_t) == 0 ***

libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!


I also tried opening VLC from terminal and dragging the Video_Ts folder into VLC.  There were many pages of this:

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1678 ***

And at the very end this:

libdvdnav: Suspected RCE Region Protection!!!

Thanks Jack

---

### Post by jaqrah on 2009-02-06
Just a bit of additional information

After seeing:

libdvdnav: Suspected RCE Region Protection!!!
libdvdnav: Suspected RCE Region Protection!!!

I popped in a region free disc.  VLC played it without any problems.  So it appears I have region issue.

---

### Post by jaqrah on 2009-02-06
mc4man...thanks for all of your assistance.  Your help pointed me in the right direction for solving my problem.

I neglected to install the libdvdcss2 package.

After doing so, everything works fine.

Chalk it up to Ubuntu newbness.

---

### Post by mc4man on 2009-02-06
Everything but your fstab looks fine (and that's not why you can't playback, give me a bit to look thru.

As far as the drives it's not an issue as yet with their positions (may be for burning, for the moment leave as is. If you were to switch you'd need to switch the positions in the case, the ide cable is designed for your top drive to use the end connector, the below drive the middle (just leave alone

Why don't you add a line to your fstab for the other drive, makes life easier.

first do this, if it says already exists good, if not it'll be created

```
sudo mkdir /media/cdrom1
```
then
```
gksudo gedit /etc/fstab
```

To make it a little more logical do like this ( changing the existing one to /dev/scd0, and adding the 2nd line.


```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
```


Have you ever played a commercial dvd in these drives in windows?

Do you have libdvdcss2 installed?

---

### Post by mc4man on 2009-02-06
If your running 8.10 it's easy to set vlc to autorun your dvd's. if 8.04 it takes a few steps.( let me know

If you ever have burning issues then switch the drives around.
good luck

---

### Post by timmil on 2009-02-08
Hey, the my original problem is still occuring. Put a DVD in the drive and it will not mount. I have done everything that has been suggested in this thread and still nothing.

Anyone?

---

### Post by Sionide on 2009-02-14
I'm all out of ideas too... A DVD drive is recognised in the BIOS, but when a DVD or Data/Audio CD is put in on Ubuntu, it spins up and no icon appears on the desktop. /media/cdrom0 etc. is empty.

Have attached the outputs of lshw/lspci/cat etc/fstab in the outputs.txt file.

---

