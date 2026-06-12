---
title: "Cannot play DVDs!  Help!"
date: 2008-06-10
forum: Multimedia Software
---

### Post by Mozenrath on 2008-06-10
I recently upgraded from 7.10 to 8.04.  I'm very satisfied with all the improvement that have been made, except for one thing: DVDs don't play at all!  

I've downloaded all the Gstreamer and Medibuntu stuff, but none of it has any effect.

When I put in a DVD and the totem window pops up, it gives me an error message that says "An error occurred: could not read from source".

Here's a screenshot. 

[http://i29.tinypic.com/w6wod5.png](http://i29.tinypic.com/w6wod5.png)

I'm pretty sure that I was able to play DVDs when I had 7.10.  I've searched these forums and found no solution.

---

### Post by aquavitae on 2008-06-10
Which medibuntu stuff - did you install libdvdcss? And are you sure its not a problem with the dvd - does it do the same with others?

---

### Post by Mozenrath on 2008-06-10
> **aquavitae said:**
> Which emdibuntu stuff - did you install libdvdcss? And are you sure its not a problem with the dvd - does it do the same with others?

I got medibuntu from here. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

And yes, I did install libdvdcss.

I'm sure it's not a problem with the dvd because it's done this with a bunch of other dvds that I know work.

All other players show an error message too.  Even VLC won't play it.

The disc seems to mount fine, and I can see all of the vob and sub files that the disc contains.

---

### Post by peitschie on 2008-06-10
Have you installed libdvdread?

Try the following in a terminal window:
```
sudo apt-get install libdvdread3
```

Then run the following:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

This might be out of date as this is what I used to use to make it work under Gutsy :)... but hey, it won't hurt to try

---

### Post by Mozenrath on 2008-06-10
I haven't tried your suggestion yet, peitschie, but something strange just happened.

This hasn't happened before, but when I tried ejecting the disc, a similar error window popped up from ubuntu saying: "Cannot unmount the volume STAR_TREK_VOL_40 - unmount: it seems /media/cdrom1 is mounted multiple times"

What the heck? :confused:

Now it won't let me eject the drive at all.  When I try unmounting from the terminal, it just says:

benjamin@benjamin-desktop:~$ sudo umount -v /media/cdrom1
umount: /media/cdrom1: device is busy
umount: /media/cdrom1: device is busy
umount: /media/cdrom1: device is busy

---

### Post by lexanite on 2008-06-10
> **Mozenrath said:**
> I recently upgraded from 7.10 to 8.04.  I'm very satisfied with all the improvement that have been made, except for one thing: DVDs don't play at all!  

I've downloaded all the Gstreamer and Medibuntu stuff, but none of it has any effect.

When I put in a DVD and the totem window pops up, it gives me an error message that says "An error occurred: could not read from source".

Here's a screenshot. 

[http://i29.tinypic.com/w6wod5.png](http://i29.tinypic.com/w6wod5.png)

I'm pretty sure that I was able to play DVDs when I had 7.10.  I've searched these forums and found no solution.

I just finish installing Ubuntu 8.04 and have the same problem.
Wait for anybody's help.

---

### Post by peitschie on 2008-06-10
Can you afford a quick reboot?  We could untangle that possibly but I don't know if its worth the effort :)

Just for interests sake, you can sometimes find which application is trying to use it by going:
```
lsof | grep /media/cdrom1
```

Also, when you say you have downloaded the Medibuntu stuff, which "stuff" exactly?

---

### Post by aquavitae on 2008-06-10
That usually means some process has got hold of the dvd and won't let go. If you can work out which process it is you could kill it, but usually when that happens I end up rebooting. I'm sure theres a way round it though... must find out...

---

### Post by Mozenrath on 2008-06-10
Alright, the only way I was able to eject the disc was to restart the machine.

So far, it did the same thing and totem couldn't read the disc.

I've now tried peitschie's suggestion, and it didn't make a difference.

Though now I tried ejecting the disc and it actually ejected this time and got no error.

Totem must be able to recognize it somewhat, because it changes the aspect ratio (the size of the window) when I open the dvd in it, and it also displays the total time for the dvd at the bottom before the error message pops up.

---

### Post by Mozenrath on 2008-06-10
> **peitschie said:**
> Can you afford a quick reboot?  We could untangle that possibly but I don't know if its worth the effort :)

Just for interests sake, you can sometimes find which application is trying to use it by going:
```
lsof | grep /media/cdrom1
```

Also, when you say you have downloaded the Medibuntu stuff, which "stuff" exactly?

That command didn't work for me.

I got medibuntu from this page. [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

I c/p and executed these codes from that site in the terminal:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```


I think I may have accidentally executed this command, though.

```
sudo sed -e 's/ non-free//' -i /etc/apt/sources.list.d/medibuntu.list

```

Supposedly it excludes getting packages from the non-free medibuntu repository.  I'm not sure if that's a bad or good thing.

---

### Post by Loosewheel on 2008-06-10
I also am not able to play DVDs w/Ubuntu 8.04. It can't read the disk and says no media in the drive.
I am able to play a disk with .avi files and vcd's are ok with the drive.

---

### Post by Itzi on 2008-06-10
Getting the same error you are getting.  Gonna search some more and see if ii can find anything.

---

### Post by wildman4god on 2008-06-10
I feel your pain, I have installed everything I could find that is supposed to make dvds play and it still doesn't work and is really annoying somebody help us please

---

### Post by wildman4god on 2008-06-10
CHEESE AND CRACKERS!!!! I downloaded mplayer and it now plays dvds, none of the other programs will play it but mplayer does.

---

### Post by Mozenrath on 2008-06-10
> **wildman4god said:**
> CHEESE AND CRACKERS!!!! I downloaded mplayer and it now plays dvds, none of the other programs will play it but mplayer does.

Lucky.  Mplayer doesn't work for me.  It gives me an error message saying "Error! - Seek failed".

When I get back from class, I'm going to put in my gutsy cd to see if my drive works fine in that.  Just to make sure it's not a hardware issue, which I doubt it is.

---

### Post by mc4man on 2008-06-10
run and post
```
sudo lshw -C disk
```

---

### Post by Mozenrath on 2008-06-10
> **mc4man said:**
> run and post
```
sudo lshw -C disk
```

```
  *-disk                  
       description: ATA Disk
       product: WDC WD2000JD-60K
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 08.0
       serial: WD-WCAMT1320081
       size: 186GiB (200GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=cbbacbba
  *-disk:0
       description: SCSI Disk
       product: USB SD Reader
       vendor: Generic
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/sdc
       version: 1.00
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdc
  *-disk:1
       description: SCSI Disk
       product: USB CF Reader
       vendor: Generic
       physical id: 0.0.1
       bus info: scsi@3:0.0.1
       logical name: /dev/sdd
       version: 1.01
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdd
  *-disk:2
       description: SCSI Disk
       product: USB SM Reader
       vendor: Generic
       physical id: 0.0.2
       bus info: scsi@3:0.0.2
       logical name: /dev/sde
       version: 1.02
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sde
  *-disk:3
       description: SCSI Disk
       product: USB MS Reader
       vendor: Generic
       physical id: 0.0.3
       bus info: scsi@3:0.0.3
       logical name: /dev/sdf
       version: 1.03
       capabilities: removable
     *-medium
          physical id: 0
          logical name: /dev/sdf
  *-disk
       description: SCSI Disk
       product: 1A
       vendor: ST330063
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sdb
       version: 3.04
       serial: 5NF0W70R
       size: 279GiB (300GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=20e57d84
  *-cdrom
       description: DVD writer
       product: DVDR/RW DX162D-A
       physical id: 0
       bus info: ide@0.0
       logical name: /dev/hda
       logical name: /media/cdrom1
       version: 150F
       capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
       configuration: mode=udma2 mount.fstype=udf mount.options=ro,nosuid,nodev state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/hda
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev state=mounted
  *-disk
       description: ATA Disk
       product: Maxtor 6E040L0
       vendor: Maxtor
       physical id: 1
       bus info: ide@1.1
       logical name: /dev/hdd
       version: NAR61590
       serial: E1JQY0TE
       size: 38GiB (41GB)
       capacity: 38GiB (41GB)
       capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
       configuration: apm=off mode=udma5 signature=153b5f49 smart=on

```

---

### Post by kystorms on 2008-06-10
> **peitschie said:**
> Have you installed libdvdread?

Try the following in a terminal window:
```
sudo apt-get install libdvdread3
```

Then run the following:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

This might be out of date as this is what I used to use to make it work under Gutsy :)... but hey, it won't hurt to try

This worked grand for me, but now my DVD will only play in French! I tried to switch the languages to english ( Movie Player ) but it wont switch, any way to reset it to english via terminal?

thanks

---

### Post by mc4man on 2008-06-10
@ Mozenrath
point your dvd player to /dev/hda  or to maybe fix 
You should have a scdx designation (scd0) and with only one dvd drive the links of dev/dvd, dev/cdrom ect. with a mount point of /media/cdrom
post from /etc/udev/rules.d - the contents of 70-persistent-cd rule and
cat /etc/fstab

---

### Post by Mozenrath on 2008-06-10
> **mc4man said:**
> @ Mozenrath
point your dvd player to /dev/hda  or to maybe fix 
You should have a scdx designation (scd0) and with only one dvd drive the links of dev/dvd, dev/cdrom ect. with a mount point of /media/cdrom
post from /etc/udev/rules.d - the contents of 70-persistent-cd rule and
cat /etc/fstab

How would I go about doing this?  I'm only minimally familiar with how to work with linux, and I only really know how to mount and unmount stuff.  Not much else.

Here are the contents of the 70-persistent-cd rule.
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# SAMSUNG_DVD-ROM_SD-616T (pci-0000:00:14.1-ide-0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
# DVD_Writer_840d (pci-0000:00:13.2-usb-0:6:1.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HP_DVD_Writer_840d_49106D-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HP_DVD_Writer_840d_49106D-0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HP_DVD_Writer_840d_49106D-0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HP_DVD_Writer_840d_49106D-0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
# DX162D-A (pci-0000:00:14.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="dvdrw2", ENV{GENERATED}="1"
```

Here are the contents of fstab.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=40bc103f-e519-417a-a967-f31a39262863 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=62cb04fd-846a-4b22-94b6-e1f466cd08d8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
```

---

### Post by mc4man on 2008-06-10
What happens if you put a dvd in the drive, open vlc, choose file -> open disc and in the pop up type in /dev/hda for device name?  Try /dev/dvd2 also
Do you have 1 or 2 dvd drives? (internal) If only one is it the DX162D-A or SAMSUNG_DVD-ROM_SD-616T? (would assume the former)

Did you have a usb dvd drive hooked up while you were updating the Os?

---

### Post by Mozenrath on 2008-06-11
It's weird.  I've inserted the disc, and suddenly it plays.  Though it skipped the menu.

It's not letting me burn anything to blank discs though.  I burned an iso of ophcrack to a cd, and it won't boot.  I downloaded an iso of ubuntu to a cd.  That one won't boot either.  I tried burning just an individual file to a DVD, and it won't even let me, saying that "burn:// is inaccessible".

I don't know what the heck is going on.  I think I might downgrade if this can't be fixed.

I only have one internal dvd drive.  I have an external hard drive, though.  The dvd drive is the Samsung one. EDIT: Actually, let me correct myself.  The other dvd drive is the one I'm currently using.  The last drive I had was a Samsung, and I discarded it a month or two ago and swapped it for the DX162D-A.

Oh, and I tried the thing with VLC, and this time it worked, and it loaded the dvd menu too.

Now I just have to figure out how I'm going to burn stuff now.

EDIT: I restarted my machine and I am now able to burn stuff to discs without any problem.  This is really quite a mystery.  I don't know how this situation could have solved itself.  I really haven't done anything that would fix the problem.  Well if the problem arises again, I'll report back.  Thanks for all the help, guys!

---

### Post by Mozenrath on 2008-06-11
Okay, so here's my current status:

DVDs will play for the most part, but Totem doesn't recognize the menus and goes straight to playing whatever's on the disc.  VLC can play DVDs and recognize the menus.

Burning discs, especially from iso images, doesn't seem very reliable.  Part of the time, I get an error when inserting a blank disc that says "burn:// 'cannot be mounted?'", or something along those lines.  So I usually eject the disc and reinsert it and it works fine.  The thing is the burning process for CD/DVD Creator gives me an error at the end, but when I use Brasero I get no such error.  Either way, whatever comes out is crap.  It can't be read on either my windows machine or my ubuntu.  Whatever it wrote to those discs is garbage.  The only time it's worked so far is when I burned Ophcrack, and that boots fine.

When trying to make a copy of Hardy so I can boot the live cd on another machine, it seems to do a half job.  When I boot off the disc, it gets to the first menu, and when I go any further it gives me an error that says "I/O error" and it tells me that it isolinux cannot read the disc.

The situation doesn't seem very reliable.  It feels like something's conflicting with the drive, but I don't know what.

---

### Post by mc4man on 2008-06-12
Do all this with no external usb dvd drive connected
run in terminal ```
sudo gedit /etc/udev/rules.d/70-persistent-cd.rules
``` (If it opens a blank page exit without saving and try comm. again, ie. copy above and paste) Delete everything in red.
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.[COLOR="Red"]
# SAMSUNG_DVD-ROM_SD-616T (pci-0000:00:14.1-ide-0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
# DVD_Writer_840d (pci-0000:00:13.2-usb-0:6:1.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HP_DVD_Writer_840d_49106D-0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HP_DVD_Writer_840d_49106D-0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HP_DVD_Writer_840d_49106D-0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="HP_DVD_Writer_840d_49106D-0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"[/COLOR]
# DX162D-A (pci-0000:00:14.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="dvdrw2", ENV{GENERATED}="1"
```
Then edit what's left as such
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DX162D-A (pci-0000:00:14.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
``` _Just removing the #2 from each link._ Save and exit. 

Then in the terminal ```
gksudo nautilus /dev
```  In dev look for all symlinks you can find (_files with arrow_) with these names (including ones with a #, ex. dvd1, cdrw1, ect.).  cdrom, cdrw, dvd, dvdrw, sr0, sr1 and delete them. _Only delete symlinks_, the sr0, sr1 are much further down the page. (if there's a sr2 delete that as well) Then exit the browser window. Then run  ```
sudo gedit /etc/fstab
```
Delete this line
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
save and exit. Then _reboot_ and see.

edit :any questions ask first - pretty straightforward. Your default device, links for any of your dvd/media  players will now be /dev/scd0, w/ links of /dev/dvd, /dev/cdrom - that's what they all expect by default.
If you were to connect a usb dvd drive afterwards it will be /dev/scd1 w/ links of /dev/dvd1, dev/cdrom1, ect.

---

### Post by huck416 on 2008-06-12
When I upgraded to 8.04 I also lost the dvd playback capability. Kaffeine gave the following error:

To be able to watch it you will need to install libdvdcss by running from a console: sudo /usr/share/doc/kaffeine/install-css.sh

I checked and noticed libdvdcss2 was installed but apparently it's not capatible with Kaffeine. So I ran the above command and it "downgraded" to libdvdcss. I rebooted and Kaffeine was able to play the dvd complete with menu. However, then I was left with a constant upgrade reminder icon in the task tray for libdvdcss2. When I upgraded, I once again lost the ability to play dvds. I then installed vlc and it plays the dvds no problem although it goes straight to the movie which is fine with me; who wants all the preview nonsense anyway.

So I've got dvd playback with Hardy using vlc. Everything else is good as well.

---

### Post by Mozenrath on 2008-06-12
@ mc4man

Okay, I did what you said and rebooted, and here's what I got when I tried opening the DVD.

[http://i28.tinypic.com/2zdvwye.png](http://i28.tinypic.com/2zdvwye.png)

So now it can't even mount. :P

---

### Post by Pjotr123 on 2008-06-12
Upgrade woes... Consider a clean reinstallation of 8.04:
[http://ubuntutip.googlepages.com/upgrading](http://ubuntutip.googlepages.com/upgrading)

---

### Post by Mozenrath on 2008-06-13
So pretty much the only thing I can do is reinstall?  What a hassle. =(

---

### Post by mandriva9786 on 2008-06-13
Ya when ever i try to play dvds it says i have no permission to run it. You cant set any permissions. I cn play music disks but not dvds!!!!

---

### Post by Mozenrath on 2008-06-13
Here's the status of what's going on with my machine since I made the changes.

```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# DX162D-A (pci-0000:00:14.1-scsi-0:0:0:0)
#ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
#ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
#ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
#ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DVDRRW_DX162D-A (pci-0000:00:14.1-ide-0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-ide-0:0", SYMLINK+="dvdrw2", ENV{GENERATED}="1"
```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=40bc103f-e519-417a-a967-f31a39262863 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=62cb04fd-846a-4b22-94b6-e1f466cd08d8 none            swap    sw              0       0

/dev/sda3 /media/cdrom3 udf,iso9660 user,noauto,exec 0 0
```


And here's a screenshot of what happens now when I try mounting a dvd.

[http://i28.tinypic.com/2mnpqo7.png](http://i28.tinypic.com/2mnpqo7.png)


The situation is quite worse now. :P

---

### Post by rrm3 on 2008-08-01
Hmmm.  Perhaps no one is reading this thread anymore, but I just had that problem.  I don't usually watch DVDs on my computer though so I didn't know what the expected behavior was.  Anyway, whenever I get the totem error "cannot read from source" it means I have to unmount the volume to play the DVD.  For example, opening up a terminal and typing "unmount /media/cdrom" or whatever the DVD gets mounted under.  Apparently totem doesn't want to read from the disc while it's mounted.

---

