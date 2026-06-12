---
title: "DVD playback"
date: 2008-06-28
forum: Multimedia Software
---

### Post by martinkun167 on 2008-06-28
Hi, i have Hardy and tried to play a dvd movie on vlc, totem, ogle, but none of them are able to play the video properly. I just get a pixelated green screen with choppy sound. I have nvidia 8600GT and ubuntu seemed to have installed its drivers from the very beginning...what is the problem???

---

### Post by Bakon Jarser on 2008-06-28
Hopefully you can find an answer here.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by pcjunkie on 2008-06-28
I followed the guide but I still can't mount the commercial dvd's on 3 different computers. 

Its driving me to over consumption of coffee. I think I will have an head exploded soon.
With or without a media player the drive should at least "mount" the volume to be able to read its contents. Its not doing that.

---

### Post by Bakon Jarser on 2008-06-28
> **pcjunkie said:**
> I followed the guide but I still can't mount the commercial dvd's on 3 different computers. 

Its driving me to over consumption of coffee. I think I will have an head exploded soon.
With or without a media player the drive should at least "mount" the volume to be able to read its contents. Its not doing that.

Yes it should mount and play them after following the guide.  Just to verify, you have libdvdcss2, libdvdnav4, and libdvdread3 installed right?  And your computers will read all cd/dvd media except commercial dvd movies?

---

### Post by pcjunkie on 2008-06-29
Yes I have all those libraries and others for making backups of DVDs I own where added before I started using Hardy. 

I have 3 pc's here and none of them play or open commercial DVD's. When booting to 7.10 it works fine. I can read the disk directories and copy and play just not in Hardy. Same setup fairly much.

---

### Post by Bakon Jarser on 2008-06-29
> **pcjunkie said:**
> Yes I have all those libraries and others for making backups of DVDs I own where added before I started using Hardy. 

I have 3 pc's here and none of them play or open commercial DVD's. When booting to 7.10 it works fine. I can read the disk directories and copy and play just not in Hardy. Same setup fairly much.

When you say they were added before using Hardy do you mean that you upgraded all three computers from feisty?  If so have you tried a clean install of hardy to see if that helps?

---

### Post by pcjunkie on 2008-06-29
Ah no all three are clean installs. I meant before using as in actually using not just loading data, libraries, user files.

I ran all those scripts in the guide, it was only missing one library, I picked out all the other anyway and installed them already on all 3 pc's. 

All drives are different to so its not the actual drive. 2 are pioneer, one is 2 years old the other a recent model. The other is a sony.

---

### Post by Bakon Jarser on 2008-06-29
hmmmm.......very strange.  I noticed in the guide he doesn't install the w32codecs.  not sure if it will make a difference for you but it's worth a shot.

```
sudo apt-get install w32codecs
```

---

### Post by Bakon Jarser on 2008-06-29
My last suggestion would be to read this page.

[https://help.ubuntu.com/8.04/musicvideophotos/C/video.html](https://help.ubuntu.com/8.04/musicvideophotos/C/video.html)

---

### Post by mc4man on 2008-06-29
If after inserting a dvd movie in the drive it shows up on the desktop or in places than open vlc from the terminal, file -> open disk and post the terminal output

And dmesg | tail would be useful too.

---

### Post by pcjunkie on 2008-06-29
It doesn't open...response is no media in drive.


dmesg | tail 
[   86.601535] Bluetooth: HCI socket layer initialized
[   86.705130] Bluetooth: L2CAP ver 2.9
[   86.705139] Bluetooth: L2CAP socket layer initialized
[   86.784757] Bluetooth: RFCOMM socket layer initialized
[   86.784784] Bluetooth: RFCOMM TTY layer initialized
[   86.784787] Bluetooth: RFCOMM ver 1.8
[   90.405172] NET: Registered protocol family 17
[   92.293463] NET: Registered protocol family 10
[   92.294777] lo: Disabled Privacy Extensions
[  102.432626] eth0: no IPv6 routers present


What does that do?

I have been messing around here some more, installed a fresh copy on a partition. added a few libraries for totem still nothing.

All pc's are AMD


EDIT

I just ran another clean install inserted the DVD and it worked. I had not "jumped the gun" by pre-installing everything like I do. What the hell is that?
Is this thing not working because I changed some kind of default by installing codecs already?

Ok So now what? How does one point the system to a DVD and open it regardless of what is "potentially" going to play it?

 sudo lshw -C disk

 description: DVD reader
       product: LITE-ON COMBO SOHC-4836K
       physical id: 0
       bus info: ide@1.0
       logical name: /dev/hdc
       version: SPJ2
       serial: 2005120800004573
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd
       configuration: mode=udma2 status=nodisc

> configuration: mode=udma2 status=nodisc

a DVD is in the drive...



/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Totem could not play 'Unable to open 'dvd:///dev/hdc'
Unable to open 'dvdsimple:///dev/hdc

---

### Post by pcjunkie on 2008-07-01
Repeated guide. 1 PC is working though choppy as hell.

VLC outputs

 access_file error: unknown file type for `/media/cdrom1'
vcdx error: fread (): Is a directory
ts error: cannot peek

fakeroot installed as per guide. Fresh install on pc. new dvd, new dvd player.


Totem plays fine for about 30 seconds then starts to break up. It does this regardless of chapter, position in DVD.

alison@alison-desktop:~$ hdparm -d /dev/hdc
/dev/hdc:
 using_dma     =  1 (on)

alison@alison-desktop:~$ hdparm -d /dev/hdd
/dev/hdd:
 using_dma     =  0 (off)

DMA + Choppy video...

How to enable?

I also ran 

alison@alison-desktop:~$ sudo lshw -C disk
  *-cdrom:1
       description: DVD-RAM writer
       product: TSSTcorp CDDVDW SH-S202J
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       logical name: /media/cdrom1
       version: SB01
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: mode=udma4 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/hdd
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted


And the story continues
Attempted setting DMA to on

alison@alison-desktop:~$ hdparm -d 1 /dev/sdd
/dev/sdd: Permission denied

k hows about I jam it into U them...

alison@alison-desktop:~$ sudo hdparm -X -d1 --verbose /dev/hdd

/dev/hdd:
 setting using_dma to 1 (on)
 setting xfermode to 0 (default PIO mode)
outgoing cdb:  85 06 20 00 03 00 00 00 00 00 00 00 00 40 ef 00
SG_IO: ATA_16 status=0x2, host_status=0x0, driver_status=0x0
Trying legacy HDIO_DRIVE_CMD
 using_dma     =  1 (on)

k


Retest

alison@alison-desktop:~$  hdparm -d /dev/hdd

/dev/hdd:
 using_dma     =  1 (on)

Still choppy, now worse,,,
Producing segmentation fault


 Model=ST3160021A, FwRev=3.06, SerialNo=3JS2HZET
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=312579695
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 2:  ATA/ATAPI-1,2,3,4,5,6

 * signifies the current active mode

---

### Post by Bakon Jarser on 2008-07-02
In VLC try  Video > Deinterlace > Blend and see if it helps with the choppiness.

---

