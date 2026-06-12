---
title: "DVD playback fails all the time..."
date: 2008-07-18
forum: Multimedia Software
---

### Post by xeriouxi on 2008-07-18
Hi!

I'm trying to play DVD's on Hardy but they're failing all the time with the message "Could not read from resource" in Totem.

I've got libdvdcss2 and all the other libdvd things installed, have tried using the xine method with Totem, using different players... everything I can think of.

Is this some kind of known bug or something because I've never been able to get DVD working in Ubuntu and it's driving me up the wall not knowing why.

Thanks for any info! =)

---

### Post by cj100570 on 2008-09-06
I'm having the same issue. The strange thing is that DVD playback was working just fine on my system previously. I've tried everything and nothing has helped. I'm contemplating a full OS reinstall.

---

### Post by wolfen69 on 2008-09-06
try VLC. works great for me.

---

### Post by cj100570 on 2008-09-06
> **wolfen69 said:**
> try VLC. works great for me.

"Non" of the players on my system will play DVDs anymore; VLC, Totem, MPlayer, SMPlayer.

---

### Post by irishrm on 2008-09-06
I,ve been posting the same problem on the general help thread(maybe the wrong place) None of the players mentioned work but I downloaded  gnome mplayer and that works fine. try it.
However I would like to get vlc working if anybody has the answer.
Irishrm

---

### Post by joze7205 on 2008-09-06
I just tried gnome-mplayer. My system still freezes when I try to play a DVD... 

Any other suggestions?

---

### Post by Shazaam on 2008-09-07
gxine works for me. Even shows the dvd menu. Get it through Synaptic.

---

### Post by cj100570 on 2008-09-07
This is totally odd. I reinstalled Ubuntu and DVD playback still doesn't work. I tried using openSUSE which I have on another hard drive and it plays without issue. Up until now I've never had an issue getting DVD playback to work on any version of Ubuntu. There's obviously something screwy going on.

---

### Post by lukjad on 2008-09-07
I have the exact same problem. I even made thread about it. The closest to an answer I got was that 8.04 didn't like my hardware and/or it's just a bug.

---

### Post by hazelnut on 2008-09-07
Something must have happened with a recent update.  I can no longer read DVDs.  I get constant read errors.  

At first I thought my drive was broken, but I put in a brand new drive that works in another machine it I got the same problem.  I then rebooted to windows and loaded vlc, the disc playes just fine with no errors.  Back to ubuntu, and massive read errors.

This is obviously a software bug that only showed up recently.

In case it helps, I have a Liteon LH-20A1S

---

### Post by lukjad on 2008-09-07
I have an LG.

---

### Post by hazelnut on 2008-09-07
New Information:

I have solved the problem for me.

I have always used /dev/scd0 to reference my dvd drive.  I have vlc configured to auto play /dev/scd0 upon disk insertion.  But that no longer works.

I ran this:

```

$ sudo lshw -C disk

  *-cdrom
       description: DVD-RAM writer
       product: DVDRW LH-20A1S
       vendor: LITE-ON
       physical id: 1
       bus info: scsi@5:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 9L08
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,noexec state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,noexec state=mounted


```

I noticed that the *-medium does not show /dev/scd0 as a logical name.  

All I did was change my reference from /dev/scd0 to /dev/cdrom1 and it works as expected now with no read errors.

---

### Post by lukjad on 2008-09-07
How did you do that? Here is my output:

```
lukjad007@stationx:~$ sudo lshw -C disk
[sudo] password for lukjad007: 
  *-disk:0                
       description: ATA Disk
       product: SAMSUNG SV2044D
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MM10
       serial: 0191J1FN430529
       size: 19GiB (20GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=48c4d750
  *-disk:1
       description: ATA Disk
       product: WDC AC26400R
       vendor: Western Digital
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 22.0
       serial: WD-WM6272673518
       size: 6149MiB (6448MB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000a621b
  *-cdrom:0
       description: DVD-RAM writer
       product: DVD-RAM GSA-H55N
       vendor: HL-DT-ST
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/dvd2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: 1.05
       serial: [HL-DT-STDVD-RAM GSA-H55N1.0507/12/11 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD reader
       product: XJ-HD165H
       vendor: JLMS
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: CH11
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: ST3500830A
       vendor: SEAGATE
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 3.AA
       size: 465GiB (500GB)
       capacity: 465GiB (500GB)
       capabilities: 5400rpm partitioned partitioned:dos
       configuration: ansiversion=2 signature=000a621b

```

---

### Post by hazelnut on 2008-09-07
> How did you do that? Here is my output:

Try putting a disk in the drive, wait about 30 seconds till it mounts and rerun the command.

---

### Post by lukjad on 2008-09-07
Here we go again:
```
lukjad007@stationx:~$ /usr/share/themes/UbuntuStudio/gtk-2.0/gtkrc:83: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.

[1]+  Done                    gedit ~/.gnome2/nautilus-scripts/Open\ as\ root
lukjad007@stationx:~$ sudo lshw -C disk
[sudo] password for lukjad007: 
  *-disk:0                
       description: ATA Disk
       product: SAMSUNG SV2044D
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MM10
       serial: 0191J1FN430529
       size: 19GiB (20GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=48c4d750
  *-disk:1
       description: ATA Disk
       product: WDC AC26400R
       vendor: Western Digital
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 22.0
       serial: WD-WM6272673518
       size: 6149MiB (6448MB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000a621b
  *-cdrom:0
       description: DVD-RAM writer
       product: DVD-RAM GSA-H55N
       vendor: HL-DT-ST
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom2
       logical name: /dev/dvd2
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom1
       version: 1.05
       serial: [HL-DT-STDVD-RAM GSA-H55N1.0507/12/11 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom2
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
  *-cdrom:1
       description: DVD reader
       product: XJ-HD165H
       vendor: JLMS
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: CH11
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=open
  *-disk
       description: SCSI Disk
       product: ST3500830A
       vendor: SEAGATE
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 3.AA
       size: 465GiB (500GB)
       capacity: 465GiB (500GB)
       capabilities: 5400rpm partitioned partitioned:dos
       configuration: ansiversion=2 signature=000a621b

```

---

### Post by hazelnut on 2008-09-07
You're good,  use /dev/cdrom2

```
     *-medium
          physical id: 0
          logical name: /dev/cdrom2
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted

```

---

### Post by lukjad on 2008-09-07
Well, my DVDs and other long movie clips still don't play well in 8.04. They are very jumpy and fade to B&W.

---

### Post by cj100570 on 2008-09-07
This is a totally unsatisfactory situation. :mad: I've tried DVD playback on 3 more distros on hard drives that I switched into my pc and the dvd played each time. It is only while running Ubuntu that there is no dvd playback. And what makes this really odd is that my system played dvds without issue until a few days ago.

---

### Post by cj100570 on 2008-09-07
I did the following and I now have DVD playback in MPlayer. I'll be testing my other players shortly.

sudo aptitude install libdvdcss2
sudo /usr/share/doc/libdvdread3/./install-css.sh

:guitar:

---

### Post by Maniacal on 2008-09-10
My video freezes for 5 - 15 seconds in SMplayer during DVD playback. Audio continues while video is still. Playback appears to be fine under Movie Player. Have a 2-3 week old load of 8.04 on a new AMD64 dual core machine. Any ideas?


Just tried DVD playback with SMPlayer on my 32 bit machine. It locked up solid after around 6 minutes. Was fine a few weeks ago. Have we got a recent update that is causing these problems?

---

### Post by cj100570 on 2008-09-10
> **Maniacal said:**
> My video freezes for 5 - 15 seconds in SMplayer during DVD playback. Audio continues while video is still. Playback appears to be fine under Movie Player. Have a 2-3 week old load of 8.04 on a new AMD64 dual core machine. Any ideas?

This situation really is strange. I'm at a loss at this point. As best as I can tell it's an Ubuntu issue because non of the other distros I use exhibit this behavior.

---

### Post by rvm4000 on 2008-09-11
> **Maniacal said:**
> My video freezes for 5 - 15 seconds in SMplayer during DVD playback. Audio continues while video is still. Playback appears to be fine under Movie Player. Have a 2-3 week old load of 8.04 on a new AMD64 dual core machine. Any ideas?

By default smplayer uses no cache for DVDs (because seeking to chapters may not work with it). Try to increase the cache (Preferences->Performance).

---

### Post by stinger30au on 2008-09-11
probably th easiest way to to click applications -> add/remove software


in the box at the top set it to show all available applications

now click the right side box that says 

sound and video

scroll down the list and you will find a few boxes that say Gstreamer plugins, should be about 6 or so of them

put a tick in every single one of the g streamer codex box you can find

then click apply changes and let it download all the software

once done restart your pc

try playing movies now.... it should work... it did for me

---

### Post by seagull man on 2008-09-11
I second the idea that it's the fault of a recent update since dvds have recently stopped working for me also. They run fine in windows, haven't tried another distro yet but I assume it works in everything but ubuntu.

---

### Post by lukjad on 2008-09-11
I disagree. My problem has being going on for months since I installed 8.04.

---

### Post by kierpaul on 2008-09-11
You may want to uninstall your DVD program and then try reinstalling it using add/remove from the applications menu. Also, some of the codecs on DVD's is encrypted and has to be decrypted. I solved my issues by loading these libraries in the Synaptic Package Manager after reinstalling the software:

libdvdnav4
libdvdread3

For decryption do this under a terminal window: 
sudo /usr/share/doc/libdvdread3/install-css.sh

I used gxine and it works excellent! If you choose to use this program make sure you have all the plugins with it! Most of them will come with install. Hope this helps!

---

### Post by Maniacal on 2008-09-11
Thanks all for the assistance.

Tried increasing cache, no change. Installed the 6 Gstreamer packages, no change. Still experiencing the same video freeze in SMPlayer and also Movie Player. Even removed / reinstalled packages with no change.

Kierpaul,
Installed libdvdnav4 & libdvdread3. Getting an error during decryption. All appears well until last 4 lines of process. Reads as follows:

checking for C compiler default output... configure: error: C compiler cannot create executables
See `config.log' for more details.
make: *** [build-stamp] Error 77

Information in 'config.log' is not understood. Same result with decryption command from earlier post by cj100570. format was slightly different.

kierpaul = sudo /usr/share/doc/libdvdread3/install-css.sh
cj100570 = sudo /usr/share/doc/libdvdread3/./install-css.sh

Anymore ideas?

---

### Post by kierpaul on 2008-09-11
Sorry that I could not help. To me it looks like you have some kind of a problem in Ubuntu with the install. I will be honest that I do not know what to think about these results you posted and I am just as lost as you are. Google your problem as well. I have often found that googling a problem can sometimes turnout results I cannot find in the forum. As a last resort you may want to report this problem to the support team as it could be bug of some sort as you stated earlier.

---

### Post by Irihapeti on 2008-09-12
A "compiler cannot create executables" error usually means that you are missing some files needed for compiling programs.

Install build-essential:
```
sudo apt-get install build-essential
```

or install through synaptic.

Then try running your script again.

---

### Post by Maniacal on 2008-09-12
Thanks Irihapeti, script ran fine. Must say it was my first and quite the experience.

Still have the video freeze issue though. Seeing it on gxine, Movie Player, MPlayer, & VLC. There is no pattern to it, completely random. Based on that, can't decide if it is still a Ubuntu issue or hardware. Machine is just a few weeks old. Identified this when trying to play first DVD.

Is there a way for Ubuntu to run this new burner through its paces? Like to make sure it isn't the drive. Have I crossed a line here by mentioning possible hardware problem? This newb is on a steep learning curve.

Thanks for any guidance that can be provided.

---

### Post by Irihapeti on 2008-09-12
I'm a bit (a lot?) out of my depth with DVD and similar issues, because I've had almost no problems with them. At least, nothing that couldn't be solved with installing stuff from Medibuntu etc.

One way of finding out if it's a problem with Ubuntu would be to try some other distros. If they play DVDs nicely, then it would appear that there's a problem with Ubuntu and your hardware.

I have wondered myself if there are particular drives or other hardware that have problems, but I've not seen any list or poll on this. Maybe someone else can give some information here.

---

### Post by lukjad on 2008-09-13
It's Ubuntu. I can play a DVD off of a live CD but not Ubuntu. How bad is that?

---

### Post by mc4man on 2008-09-13
> I can play a DVD off of a live CD but not Ubuntu

Well then you should be able to get playback going. I'd load up the livecd, and install vlc and libdvdcss2. (all that's needed for vlc to play dvds

Then compare the differences in some key area's, /dev links, where and how the dvd is mounting, fstab, 70-persistent-cd.rules, running  > grep 'DMA' /var/log/kern.log  grep 'CDROM',  ect.

Without even comparing it certainly appears your 70......rules needs some attention, why don't you post it. (use a maximized terminal for readability.

```
 gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

Also when you run something like sudo lshw -C disk have a dvd in your drive(s), you'll get additional info of filesystem found, if mounted, and where

---

### Post by lukjad on 2008-09-13
The operative word here is "a" live cd. It was TEENpup.

---

### Post by amj on 2008-09-13
> **mc4man said:**
> Well then you should be able to get playback going. I'd load up the livecd, and install vlc and libdvdcss2. (all that's needed for vlc to play dvds


I'm not seeing libdvdcss2 in the synaptic options.   Is there an extra repo that needs to be added?

---

### Post by mc4man on 2008-09-13
> Is there an extra repo that needs to be added? Medibuntu
See here if you wish, the way I always get things going
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)

> The operative word here is "a" live cd. It was TEENpup.

It wouldn't hurt to fix your 70...rules and take a look at a few other things, post if you want

---

### Post by lukjad on 2008-09-13
grep 'DMA' /var/log/kern.log

```
lukjad007@stationx:~$ grep 'DMA' /var/log/kern.log 
Sep  8 05:37:30 stationx kernel: [ 1365.194630] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
Sep  8 15:53:05 stationx kernel: [    0.000000]   DMA             0 ->     4096
Sep  8 15:53:05 stationx kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep  8 15:53:05 stationx kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep  8 15:53:05 stationx kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Sep  8 15:53:05 stationx kernel: [   28.522381] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Sep  8 15:53:05 stationx kernel: [   28.522396] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Sep  8 15:53:05 stationx kernel: [   28.695805] ata1.00: ATA-4: SAMSUNG SV2044D, MM101-48, max UDMA/66
Sep  8 15:53:05 stationx kernel: [   28.695890] ata1.01: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
Sep  8 15:53:05 stationx kernel: [   28.695943] ata1.01: limited to UDMA/33 due to 40-wire cable
Sep  8 15:53:05 stationx kernel: [   28.699890] ata1.00: configured for UDMA/66
Sep  8 15:53:05 stationx kernel: [   28.737673] ata1.01: configured for UDMA/33
Sep  8 15:53:05 stationx kernel: [   29.397869] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
Sep  8 15:53:05 stationx kernel: [   29.397949] ata2.01: ATAPI: JLMS XJ-HD165H, CH11, max UDMA/33
Sep  8 15:53:05 stationx kernel: [   29.554916] ata2.00: configured for UDMA/66
Sep  8 15:53:05 stationx kernel: [   29.705911] ata2.01: configured for UDMA/33
Sep  9 05:23:43 stationx kernel: [    0.000000]   DMA             0 ->     4096
Sep  9 05:23:43 stationx kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep  9 05:23:43 stationx kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep  9 05:23:43 stationx kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Sep  9 05:23:43 stationx kernel: [   28.730810] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Sep  9 05:23:43 stationx kernel: [   28.730825] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Sep  9 05:23:43 stationx kernel: [   28.904562] ata1.00: ATA-4: SAMSUNG SV2044D, MM101-48, max UDMA/66
Sep  9 05:23:43 stationx kernel: [   28.904654] ata1.01: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
Sep  9 05:23:43 stationx kernel: [   28.904707] ata1.01: limited to UDMA/33 due to 40-wire cable
Sep  9 05:23:43 stationx kernel: [   28.908494] ata1.00: configured for UDMA/66
Sep  9 05:23:43 stationx kernel: [   28.946392] ata1.01: configured for UDMA/33
Sep  9 05:23:43 stationx kernel: [   29.606541] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
Sep  9 05:23:43 stationx kernel: [   29.606623] ata2.01: ATAPI: JLMS XJ-HD165H, CH11, max UDMA/33
Sep  9 05:23:43 stationx kernel: [   29.763552] ata2.00: configured for UDMA/66
Sep  9 05:23:43 stationx kernel: [   29.914586] ata2.01: configured for UDMA/33
Sep  9 16:15:35 stationx kernel: [    0.000000]   DMA             0 ->     4096
Sep  9 16:15:35 stationx kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep  9 16:15:35 stationx kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep  9 16:15:35 stationx kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Sep  9 16:15:35 stationx kernel: [   28.353032] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Sep  9 16:15:35 stationx kernel: [   28.353047] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Sep  9 16:15:35 stationx kernel: [   28.526770] ata1.00: ATA-4: SAMSUNG SV2044D, MM101-48, max UDMA/66
Sep  9 16:15:35 stationx kernel: [   28.526859] ata1.01: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
Sep  9 16:15:35 stationx kernel: [   28.526910] ata1.01: limited to UDMA/33 due to 40-wire cable
Sep  9 16:15:35 stationx kernel: [   28.530671] ata1.00: configured for UDMA/66
Sep  9 16:15:35 stationx kernel: [   28.568578] ata1.01: configured for UDMA/33
Sep  9 16:15:35 stationx kernel: [   29.228785] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
Sep  9 16:15:35 stationx kernel: [   29.228864] ata2.01: ATAPI: JLMS XJ-HD165H, CH11, max UDMA/33
Sep  9 16:15:35 stationx kernel: [   29.385772] ata2.00: configured for UDMA/66
Sep  9 16:15:35 stationx kernel: [   29.536842] ata2.01: configured for UDMA/33
Sep 10 06:01:57 stationx kernel: [    0.000000]   DMA             0 ->     4096
Sep 10 06:01:57 stationx kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep 10 06:01:57 stationx kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 10 06:01:57 stationx kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Sep 10 06:01:57 stationx kernel: [   28.772683] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Sep 10 06:01:57 stationx kernel: [   28.772698] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Sep 10 06:01:57 stationx kernel: [   28.946410] ata1.00: ATA-4: SAMSUNG SV2044D, MM101-48, max UDMA/66
Sep 10 06:01:57 stationx kernel: [   28.946498] ata1.01: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
Sep 10 06:01:57 stationx kernel: [   28.946549] ata1.01: limited to UDMA/33 due to 40-wire cable
Sep 10 06:01:57 stationx kernel: [   28.950322] ata1.00: configured for UDMA/66
Sep 10 06:01:57 stationx kernel: [   28.988181] ata1.01: configured for UDMA/33
Sep 10 06:01:57 stationx kernel: [   29.648347] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
Sep 10 06:01:57 stationx kernel: [   29.648430] ata2.01: ATAPI: JLMS XJ-HD165H, CH11, max UDMA/33
Sep 10 06:01:57 stationx kernel: [   29.805313] ata2.00: configured for UDMA/66
Sep 10 06:01:57 stationx kernel: [   29.956437] ata2.01: configured for UDMA/33
Sep 10 17:01:37 stationx kernel: [    0.000000]   DMA             0 ->     4096
Sep 10 17:01:37 stationx kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep 10 17:01:37 stationx kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 10 17:01:37 stationx kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Sep 10 17:01:37 stationx kernel: [   29.216462] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Sep 10 17:01:37 stationx kernel: [   29.216476] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Sep 10 17:01:37 stationx kernel: [   29.390083] ata1.00: ATA-4: SAMSUNG SV2044D, MM101-48, max UDMA/66
Sep 10 17:01:37 stationx kernel: [   29.390171] ata1.01: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
Sep 10 17:01:37 stationx kernel: [   29.390223] ata1.01: limited to UDMA/33 due to 40-wire cable
Sep 10 17:01:37 stationx kernel: [   29.394013] ata1.00: configured for UDMA/66
Sep 10 17:01:37 stationx kernel: [   29.431894] ata1.01: configured for UDMA/33
Sep 10 17:01:37 stationx kernel: [   30.092130] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
Sep 10 17:01:37 stationx kernel: [   30.092209] ata2.01: ATAPI: JLMS XJ-HD165H, CH11, max UDMA/33
Sep 10 17:01:37 stationx kernel: [   30.249098] ata2.00: configured for UDMA/66
Sep 10 17:01:37 stationx kernel: [   30.400143] ata2.01: configured for UDMA/33
Sep 11 06:20:50 stationx kernel: [    0.000000]   DMA             0 ->     4096
Sep 11 06:20:50 stationx kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep 11 06:20:50 stationx kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 11 06:20:50 stationx kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Sep 11 06:20:50 stationx kernel: [   28.315017] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Sep 11 06:20:50 stationx kernel: [   28.315031] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Sep 11 06:20:50 stationx kernel: [   28.488695] ata1.00: ATA-4: SAMSUNG SV2044D, MM101-48, max UDMA/66
Sep 11 06:20:50 stationx kernel: [   28.488782] ata1.01: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
Sep 11 06:20:50 stationx kernel: [   28.488834] ata1.01: limited to UDMA/33 due to 40-wire cable
Sep 11 06:20:50 stationx kernel: [   28.492597] ata1.00: configured for UDMA/66
Sep 11 06:20:50 stationx kernel: [   28.530482] ata1.01: configured for UDMA/33
Sep 11 06:20:50 stationx kernel: [   29.191649] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
Sep 11 06:20:50 stationx kernel: [   29.191731] ata2.01: ATAPI: JLMS XJ-HD165H, CH11, max UDMA/33
Sep 11 06:20:50 stationx kernel: [   29.348654] ata2.00: configured for UDMA/66
Sep 11 06:20:50 stationx kernel: [   29.499713] ata2.01: configured for UDMA/33
Sep 11 15:55:21 stationx kernel: [    0.000000]   DMA             0 ->     4096
Sep 11 15:55:21 stationx kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep 11 15:55:21 stationx kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 11 15:55:21 stationx kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Sep 11 15:55:21 stationx kernel: [   27.981197] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Sep 11 15:55:21 stationx kernel: [   27.981212] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Sep 11 15:55:21 stationx kernel: [   28.154941] ata1.00: ATA-4: SAMSUNG SV2044D, MM101-48, max UDMA/66
Sep 11 15:55:21 stationx kernel: [   28.155030] ata1.01: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
Sep 11 15:55:21 stationx kernel: [   28.155081] ata1.01: limited to UDMA/33 due to 40-wire cable
Sep 11 15:55:21 stationx kernel: [   28.158892] ata1.00: configured for UDMA/66
Sep 11 15:55:21 stationx kernel: [   28.196670] ata1.01: configured for UDMA/33
Sep 11 15:55:21 stationx kernel: [   28.856944] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
Sep 11 15:55:21 stationx kernel: [   28.857025] ata2.01: ATAPI: JLMS XJ-HD165H, CH11, max UDMA/33
Sep 11 15:55:21 stationx kernel: [   29.013947] ata2.00: configured for UDMA/66
Sep 11 15:55:21 stationx kernel: [   29.164923] ata2.01: configured for UDMA/33
Sep 12 06:06:35 stationx kernel: [    0.000000]   DMA             0 ->     4096
Sep 12 06:06:35 stationx kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep 12 06:06:35 stationx kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 12 06:06:35 stationx kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Sep 12 06:06:35 stationx kernel: [   28.773972] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Sep 12 06:06:35 stationx kernel: [   28.773987] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Sep 12 06:06:35 stationx kernel: [   28.947645] ata1.00: ATA-4: SAMSUNG SV2044D, MM101-48, max UDMA/66
Sep 12 06:06:35 stationx kernel: [   28.947732] ata1.01: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
Sep 12 06:06:35 stationx kernel: [   28.947783] ata1.01: limited to UDMA/33 due to 40-wire cable
Sep 12 06:06:35 stationx kernel: [   28.951634] ata1.00: configured for UDMA/66
Sep 12 06:06:35 stationx kernel: [   28.989480] ata1.01: configured for UDMA/33
Sep 12 06:06:35 stationx kernel: [   29.649685] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
Sep 12 06:06:35 stationx kernel: [   29.649764] ata2.01: ATAPI: JLMS XJ-HD165H, CH11, max UDMA/33
Sep 12 06:06:35 stationx kernel: [   29.806694] ata2.00: configured for UDMA/66
Sep 12 06:06:35 stationx kernel: [   29.957730] ata2.01: configured for UDMA/33
Sep 12 16:30:06 stationx kernel: [    0.000000]   DMA             0 ->     4096
Sep 12 16:30:06 stationx kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep 12 16:30:06 stationx kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 12 16:30:06 stationx kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Sep 12 16:30:06 stationx kernel: [   28.357082] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Sep 12 16:30:06 stationx kernel: [   28.357097] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Sep 12 16:30:06 stationx kernel: [   28.530567] ata1.00: ATA-4: SAMSUNG SV2044D, MM101-48, max UDMA/66
Sep 12 16:30:06 stationx kernel: [   28.530654] ata1.01: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
Sep 12 16:30:06 stationx kernel: [   28.530704] ata1.01: limited to UDMA/33 due to 40-wire cable
Sep 12 16:30:06 stationx kernel: [   28.534540] ata1.00: configured for UDMA/66
Sep 12 16:30:06 stationx kernel: [   28.572450] ata1.01: configured for UDMA/33
Sep 12 16:30:06 stationx kernel: [   29.232600] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
Sep 12 16:30:06 stationx kernel: [   29.232679] ata2.01: ATAPI: JLMS XJ-HD165H, CH11, max UDMA/33
Sep 12 16:30:06 stationx kernel: [   29.389579] ata2.00: configured for UDMA/66
Sep 12 16:30:06 stationx kernel: [   29.540632] ata2.01: configured for UDMA/33
Sep 13 05:57:24 stationx kernel: [    0.000000]   DMA             0 ->     4096
Sep 13 05:57:24 stationx kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Sep 13 05:57:24 stationx kernel: [    0.000000]   DMA zone: 0 pages reserved
Sep 13 05:57:24 stationx kernel: [    0.000000]   DMA zone: 4040 pages, LIFO batch:0
Sep 13 05:57:24 stationx kernel: [   28.292641] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Sep 13 05:57:24 stationx kernel: [   28.292656] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Sep 13 05:57:24 stationx kernel: [   28.466328] ata1.00: ATA-4: SAMSUNG SV2044D, MM101-48, max UDMA/66
Sep 13 05:57:24 stationx kernel: [   28.466415] ata1.01: ATA-4: WDC AC26400R, 22.01N23, max UDMA/66
Sep 13 05:57:24 stationx kernel: [   28.466467] ata1.01: limited to UDMA/33 due to 40-wire cable
Sep 13 05:57:24 stationx kernel: [   28.470327] ata1.00: configured for UDMA/66
Sep 13 05:57:24 stationx kernel: [   28.508155] ata1.01: configured for UDMA/33
Sep 13 05:57:24 stationx kernel: [   29.168389] ata2.00: ATAPI: HL-DT-STDVD-RAM GSA-H55N, 1.05, max UDMA/66
Sep 13 05:57:24 stationx kernel: [   29.168468] ata2.01: ATAPI: JLMS XJ-HD165H, CH11, max UDMA/33
Sep 13 05:57:24 stationx kernel: [   29.325343] ata2.00: configured for UDMA/66
Sep 13 05:57:24 stationx kernel: [   29.476358] ata2.01: configured for UDMA/33

```

 gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules

```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# JLMS_XJ-HD165H (pci-0000:00:04.1-ide-1:1)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-ide-1:1", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-ide-1:1", SYMLINK+="dvd", ENV{GENERATED}="1"
# HL-DT-STDVD-RAM_GSA-H55N (pci-0000:00:04.1-ide-1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-ide-1:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-ide-1:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-ide-1:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-ide-1:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
# DVD-RAM_GSA-H55N (pci-0000:00:04.1-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:0:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:0:0", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:0:0", SYMLINK+="dvdrw2", ENV{GENERATED}="1"
# XJ-HD165H (pci-0000:00:04.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:1:0", SYMLINK+="cdrom3", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:04.1-scsi-1:0:1:0", SYMLINK+="dvd3", ENV{GENERATED}="1"
```

---

### Post by amj on 2008-09-13
> **mc4man said:**
> Medibuntu
See here if you wish, the way I always get things going
[http://ubuntuforums.org/showthread.php?p=5182809#post5182809](http://ubuntuforums.org/showthread.php?p=5182809#post5182809)


Thanks.   Medibuntu got me what I needed to play DVDs.

---

### Post by mc4man on 2008-09-13
@lukjad007
there are a few things of interest. Normally this line can be ignored
> limited to UDMA/33 due to 40-wire cable except when it's also seen with this
> Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)

The first line seems to point to a hdd, the second I'm not sure. See if you can find that line in your logs and post 2 or 3 lines **before it**.

In any event do this with your 70....rules, run the gksudo gedit again and delete all the entries and reboot. Leave it looking like this (before you reboot

```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.

```

Post your fstab (cat /etc/fstab) and also run sudo lshw -C disk after rebooting. (put a dvd in both drives if possible before running the lshw command

Edit: also run this (after the reset of 70...rules) for all your drives (4 total (disconnect the usb if you have one for the moment
> 
 sudo hdparm -i /dev/sda  
 and also sudo hdparm -i /dev/sdb,  sudo hdparm -i /dev/scd0,  sudo hdparm -i /dev/scd1  (looking only for the pio, dma and udma modes lines

---

### Post by lukjad on 2008-09-13
```
lukjad007@stationx:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d1cd5b95-3528-4732-a4bd-400aa29c047a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=3c5b2871-399f-46f0-8db0-6242de192c57 /home           ext3    relatime        0       2
# /dev/sda5
UUID=54f62003-7379-4842-bbab-f999f7f2b872 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

```
lukjad007@stationx:~$ sudo lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: SAMSUNG SV2044D
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: MM10
       serial: 0191J1FN430529
       size: 19GiB (20GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=48c4d750
  *-disk:1
       description: ATA Disk
       product: WDC AC26400R
       vendor: Western Digital
       physical id: 1
       bus info: scsi@0:0.1.0
       logical name: /dev/sdb
       version: 22.0
       serial: WD-WM6272673518
       size: 6149MiB (6448MB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000a621b
  *-cdrom:0
       description: DVD-RAM writer
       product: DVD-RAM GSA-H55N
       vendor: HL-DT-ST
       physical id: 2
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom1
       version: 1.05
       serial: [HL-DT-STDVD-RAM GSA-H55N1.0507/12/11 7U02
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
  *-cdrom:1
       description: DVD reader
       product: XJ-HD165H
       vendor: JLMS
       physical id: 3
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/cdrom0
       version: CH11
       capabilities: removable audio dvd
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted
  *-disk
       description: SCSI Disk
       product: ST3500830A
       vendor: SEAGATE
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdc
       version: 3.AA
       size: 465GiB (500GB)
       capacity: 465GiB (500GB)
       capabilities: 5400rpm partitioned partitioned:dos
       configuration: ansiversion=2 signature=000a621b

```

```
lukjad007@stationx:~$ sudo hdparm -i /dev/sda 

/dev/sda:

 Model=SAMSUNG SV2044D                         , FwRev=MM101-48, SerialNo=0191J1FN430529
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=472kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=39862368
 IORDY=yes, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: ATA/ATAPI-4 T13 1153D revision 17:  ATA/ATAPI-1,2,3,4

 * signifies the current active mode


```

```
lukjad007@stationx:~$ sudo hdparm -i /dev/sdb

/dev/sdb:

 Model=WDC AC26400R                            , FwRev=22.01N23, SerialNo=WD-WM6272673518     
 Config={ HardSect NotMFM HdSw>15uSec SpinMotCtl Fixed DTR>5Mbs FmtGapReq }
 RawCHS=13328/15/63, TrkSize=57600, SectSize=600, ECCbytes=40
 BuffType=DualPortCache, BuffSize=512kB, MaxMultSect=16, MultSect=?16?
 CurCHS=13328/15/63, CurSects=12594960, LBA=yes, LBAsects=12594960
 IORDY=on/off, tPIO={min:160,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 udma3 udma4 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4

 * signifies the current active mode

```

```
lukjad007@stationx:~$ sudo hdparm -i /dev/scd0

/dev/scd0:

 Model=HL-DT-STDVD-RAM GSA-H55N                , FwRev=1.05    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  sdma0 sdma1 sdma2 mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2,3,4,5

 * signifies the current active mode


```

```
lukjad007@stationx:~$ sudo hdparm -i /dev/scd1

/dev/scd1:

 Model=JLMS XJ-HD165H                          , FwRev=CH11    , SerialNo=                    
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:227,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 *udma2 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-5

 * signifies the current active mode


```

---

### Post by mc4man on 2008-09-13
everything looks good, 
your XJ-HD165H is /dev/scd1, with links of /dev/dvd1, /dev/cdrom1, mounting @ /media/cdrom0
your DVD-RAM GSA-H55N is /dev/scd0, links of /dev/dvd, /dev/cdrom, mounting @ /media/cdrom1

Most players with the exception of vlc will default to /dev/dvd for dvd's and /dev/cdrom for cd's.

With dvds still in both drives ( or re insert them) run ```
dmesg | tail

```
to see if anything odd appears.

Also start vlc from the terminal -> file -> open disk and for dvd device use /dev/scd1 (trying playback from the dvd reader XJ-HD165H. Post output

---

### Post by lukjad on 2008-09-13
```
lukjad007@stationx:~$ dmesg | tail
[ 1233.174167] Buffer I/O error on device sdc1, logical block 1883
[ 1233.174176] lost page write due to I/O error on sdc1
[ 1233.186119] REISERFS: abort (device sdc1): Journal write error in flush_commit_list
[ 1233.186156] REISERFS: Aborting journal for filesystem on sdc1
[ 1233.567215] Buffer I/O error on device sdc1, logical block 1885
[ 1233.570626] lost page write due to I/O error on sdc1
[ 1233.571354] Buffer I/O error on device sdc1, logical block 1886
[ 1233.572133] lost page write due to I/O error on sdc1
[ 1243.493316] eth0: link down
[ 1245.212121] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

```

```
lukjad007@stationx:/media/cdrom1$ XJ-HD165H
bash: XJ-HD165H: command not found
lukjad007@stationx:/media/cdrom1$ vlc
VLC media player 0.8.6e Janus
/usr/share/themes/UbuntuStudio/gtk-2.0/gtkrc:83: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
[00000572] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[00000563] main playlist: stopping playback

```

It played the movie but the sound and video were very choppy. The movie was auto loaded and no menu as to what I wanted to watch. (Thanks for all your help BTW!)

---

### Post by mc4man on 2008-09-13
If your using vlc do this 
Right click Applications -> edit menus, highlight sound & video, right click on vlc -> properties. Change the launch command to this
```
vlc %m
```

What is your default dvd movie player (what app popped up when inserting dvd? (because you have 2 drives I'd suggest adding  vlc as a default **choice** and making it the active one (if it isn't already? 

you may need to make some adjustments to your vo (video out) and ao (audio out) system wide and app specific

for vlc - settings -> preferences, click show advanced options, expand audio, highlight output modules and in drop down change from 'default' to something specific (alsa is good choice.

same method for video - try Xv first, if no improvement try X11. (if X11 works better try going back to Xv after a while.

Make sure you click save after changing settings, if you screw up you can always choose 'reset all'

system wide - preferences -> sound -> music and movies - change from autodetect to a specific ( again alsa is good first choice


Remember most other players will default to /dev/dvd or /dev/cdrom so make adjustment in the player settings if wanting to use the reader (XJ-HD165H) (exceptions vlc, and totem in autoplay

little  point - don't *cd to the mount point* to run vlc or any other player > lukjad007@stationx:/media/cdrom1$ vlc

just do it from your normal prompt or from app menu.  Various 'open with' / autoplay opportunities present or created are fine also.

---

### Post by lukjad on 2008-09-13
Nothing Popped up when I inserted my DVD. I had to choose to install then activate vlc. Also, vlc now seems to be my default player and every video file I open is played in vlc. The sound is still in Totem for now but it is a little choppy now. I'll read and answer the rest of your post in the morning. G'night and thanks.

---

### Post by mistere23 on 2008-09-17
> **cj100570 said:**
> I did the following and I now have DVD playback in MPlayer. I'll be testing my other players shortly.

sudo aptitude install libdvdcss2
sudo /usr/share/doc/libdvdread3/./install-css.sh

:guitar:

This solved my problem as I was getting this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85604&stc=1&d=12217093 02[/IMG]

in VLC and MPlayer

---

### Post by cj100570 on 2008-09-17
> **mistere23 said:**
> This solved my problem as I was getting this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=85604&stc=1&d=12217093 02[/IMG]

in VLC and MPlayer

I'm glad it worked for you too. I don't understand why this issue has popped u all of a sudden. My pc initially had no issues with DVD playback and then suddenly it just stopped working. The funny part is that DVD playback works perfectly when I run other distros on the same hardware. Hopefully this won't be an issue in 8.10.

---

### Post by carl99fan on 2008-09-23
> **cj100570 said:**
> I did the following and I now have DVD playback in MPlayer. I'll be testing my other players shortly.

sudo aptitude install libdvdcss2
sudo /usr/share/doc/libdvdread3/./install-css.sh

:guitar:

I had the same problems and this solved it!!

---

### Post by cbconway on 2008-09-23
> **Shazaam said:**
> gxine works for me. Even shows the dvd menu. Get it through Synaptic.

gxine works for me, too, but I sometimes get brief flashes when playing. Any ideas how to fix?

---

