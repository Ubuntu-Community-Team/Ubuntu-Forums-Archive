---
title: "CD and DVD auto-mount not working in 10.04"
date: 2010-05-02
forum: Mythbuntu
---

### Post by Regen on 2010-05-02
I started playing with Mythbuntu about a month ago, specifically 9.10. Auto-mounting of CDs and DVDs in 9.10 works as expected. Now that 10.04 has been released, I did a fresh install of this on a spare hard drive (connected to the same computer, so same hardware). Auto-mounting does not seem to work in 10.04. The CD is recognised by the system and I can mount it manually, but it does not auto-mount. The disc is not available in /media/<volume label> and the icon does not appear on the desktop.
 
Has anyone else done a fresh clean (non-upgrade) install of Mythbuntu 10.04? Can you confirm that this is working or not working for you? I am relatively new to Linux, so I don't know what may be going wrong.
 
I tried installing Ubuntu 10.04 on another spare hard disk (again same hardware) and confirmed that it works as expected. The disc turns up in /media/<volume label> and the icon appears on the desktop, so there is no fault with my hardware. I read at [http://www.uluga.ubuntuforums.org/showpost.php?p=9198974&postcount=8](http://www.uluga.ubuntuforums.org/showpost.php?p=9198974&postcount=8) 
> lucid is no longer by default using fstab entries for cd/dvd drives.
 
media that has a filesystem now mounts to /media/<volume label> and also by default there is no /media/cdrom0, /media/cdrom1 dir's created, nor a /media/cdrom link.
so that answers why I don't see /media/cdrom0 any more. I suspect that Xfce is not handling the fact that > lucid is no longer by default using fstab entries for cd/dvd drives. but I don't know enough to confirm this. 
 
Can anyone help point me in the right direction please?

---

### Post by Adremelech on 2010-05-02
I have this same problem with 10.04 server, but im using VirtualBox. 9.04 works fine though.

---

### Post by Regen on 2010-05-03
@Adremelech: What are you using for your desktop environment? Xfce, Gnome, KDE, other? I'm trying to work out if Xfce is the culprit here.

---

### Post by dfdario on 2010-05-03
There is a workaround:

Edit /etc/rc.local to add hald as follows: sudo nano /etc/rc.local
 add this above the exit 0, like so:
 ~~~~~~~~~~
/usr/sbin/hald
 exit 0
~~~~~~~~~~
 Save


As reported in [https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/546992](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/546992).

---

### Post by Regen on 2010-05-03
@dfdario: Thanks for the link to the bug. I have tested and can confirm that this seems to be the same bug. The workaround of editing /etc/rc.local to add hald does not work for me, but logoff and logon does fix it.  At least I have now added myself to notifications on this bug and have supplied logs to help fix it.
 
It seems that my hunch about Xfce being involved in the problem was right after all.

---

### Post by clconway on 2010-06-28
Regen, I'm having the same problem: I can manually mount DVDs but they never automount in /media; they sometimes refuse to appear in Thunar unless I logout or reboot; and hald is running on my system . Have you solved this yet?

---

### Post by Regen on 2010-06-29
Hi clconway,
Yes the bug has been fixed. Please see [https://bugs.launchpad.net/bugs/546992](https://bugs.launchpad.net/bugs/546992) for details, in particular my post #81. These patches have since moved from lucid-proposed to lucid-updates, so running Update Manager and installing all available updates should fix it for you.

---

### Post by clconway on 2010-06-29
I must have a different problem, then, because I'm up-to-date but I'm stilling having trouble mounting DVDs.

---

### Post by tgm4883 on 2010-06-29
> **clconway said:**
> I must have a different problem, then, because I'm up-to-date but I'm stilling having trouble mounting DVDs.

What is the output of 

```
dpkg -l hal
```

---

### Post by clconway on 2010-06-29
hal version is 0.5.14-0ubuntu6.

If I manually eject a DVD while it is in use by XBMC, then I immediately see a flood of "VFS: busy inodes on changed media or resized disk sr0" and I automount will stop working until I log out or reboot. The same thing doesn't happen if I'm using VLC, so maybe it's an XBMC bug... The XBMC log shows the following when the disc is ejected:

```
22:45:35 T:3001023344 M:3330416640   DEBUG: Thread 3001023344 terminating (autodelete)
22:45:35 T:3024463744 M:3330416640   DEBUG: SECTION:UnloadDelayed(DLL: special://xbmc/system/ImageLib-i486-linux.so)
22:45:35 T:3024463744 M:3330416640   DEBUG: Unloading: ImageLib-i486-linux.so
22:45:36 T:2967452528 M:3330113536   DEBUG: Thread 2967452528 terminating (autodelete)
22:45:37 T:3024463744 M:3330002944   DEBUG: UDisks: DeviceChanged (/org/freedesktop/UDisks/devices/sr0)
22:45:37 T:3024463744 M:3330002944   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sr0 with interface org.freedesktop.DBus.Properties and method Get
22:45:37 T:3024463744 M:3330002944   DEBUG: UDisks: DeviceChanged - DeviceUDI /org/freedesktop/UDisks/devices/sr0: IsFileSystem false HasFileSystem udf IsSystemInternal false IsMounted true IsRemovable true IsPartition false
22:45:40 T:3024463744 M:3329994752   DEBUG: UDisks: DeviceChanged (/org/freedesktop/UDisks/devices/sr0)
22:45:40 T:3024463744 M:3329994752   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sr0 with interface org.freedesktop.DBus.Properties and method Get
22:45:40 T:3024463744 M:3329994752   DEBUG: UDisks: DeviceChanged - DeviceUDI /org/freedesktop/UDisks/devices/sr0: IsFileSystem false HasFileSystem udf IsSystemInternal false IsMounted true IsRemovable true IsPartition false
22:45:40 T:3024463744 M:3330035712   DEBUG: UDisks: DeviceChanged (/org/freedesktop/UDisks/devices/sr0)
22:45:40 T:3024463744 M:3330035712   DEBUG: DBus: Creating message to org.freedesktop.UDisks on /org/freedesktop/UDisks/devices/sr0 with interface org.freedesktop.DBus.Properties and method Get
22:45:40 T:3024463744 M:3330035712   DEBUG: UDisks: DeviceChanged - DeviceUDI /org/freedesktop/UDisks/devices/sr0: IsFileSystem false HasFileSystem udf IsSystemInternal false IsMounted true IsRemovable true IsPartition false

```

---

### Post by bcg30506 on 2010-08-11
I am also having issues in 10.04.  DVDs automount perfectly in /media with a folder name matching the volume ID of the disc.  However, CDs do not automount.  I see this repeated over and over in dmesg:

```
[  390.635589] sr 2:0:0:0: [sr0] Unhandled sense code
[  390.635592] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  390.635596] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  390.635599] sr 2:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  390.635603] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 04 ce 1a 00 00 02 00
[  390.635611] end_request: I/O error, dev sr0, sector 1259624
[  390.635615] Buffer I/O error on device sr0, logical block 157453
[  395.223823] sr 2:0:0:0: [sr0] Unhandled sense code
[  395.223826] sr 2:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  395.223829] sr 2:0:0:0: [sr0] Sense Key : Medium Error [current] 
[  395.223833] sr 2:0:0:0: [sr0] Add. Sense: L-EC uncorrectable error
[  395.223837] sr 2:0:0:0: [sr0] CDB: Read(10): 28 00 00 04 ce 1a 00 00 02 00
[  395.223844] end_request: I/O error, dev sr0, sector 1259624

```

I can manually mount the CD with the following command:
```

sudo mount -t udf /dev/sr0 /media

```

The CD was burned with wodim using an ISO file created with genisoimage as a udf data disc.

---

### Post by bcg30506 on 2010-08-12
A bit more info on my issue:  Out of curiosity I put a CDROM in the drive that is a basic ISO9660 prefab disc.  It automounted with no trouble just like DVDs do.

So the problem with automount is very specific to CDRs that I burn as a UDF filesystem.  Again, I can mount them manually but this defeats the purpose of the PVR as it has no keyboard and requires ssh access to do so, something the wife will not do.

I have installed udftools, pmount, and cryptsetup as suggested at a site found via Google.  After reboot, there was no change in behavior.

---

### Post by Robertjm on 2010-09-19
I'm having the mounting issue as well, though I'm not using Mythbuntu.

Running Ubuntu 10.04, with all updates.

If I put an audio CD in the tray it doesn't mount. When I check the /dev folder there is no sr0 at all. Matter of fact, there's nothing that sound "CDish" at all. However, I noticed that if I reboot the desktop with the CD in the try I get an audio disk icon on my desktop, and there is an sr0 and a scd0 in /dev. 

The CD file system is listed as CDDA. No entries in fstab for the drive, which was a problem I had earlier this Summer. I could've sworn this wasn't an issue on my laptop, which was running the same version. Unfortunately, that computer isn't around to compare with anymore.

Thoughts?

---

### Post by tonymaro on 2010-10-13
Same issue here in Lucid - I use the "Disk Utility" to mount CD's and DVD's because Gnome will never automount them. This problem seemed to start after I installed kubuntu just to play around with KDE.

Interesting to note that putting a blank CD or DVD in the drive brings up the what do you want to do menu.  USB sticks and drives work just fine.

Other posts suggested installing gnome-volume-manager for Lucid but it doesn't exist in Lucid or Maverick anymore.  The package has been deleted.

This has been driving me nuts.  I'm considering reformatting / reinstalling just to get rid of it.

And yes, I'm up to date and hald is running even though I thought hald was no longer needed in Lucid?

---

### Post by mcourneyea on 2010-10-30
I am using Maverick and am up to date as of the info pasted from my msg.log below.  I am seeing the same thing.  When I put a burned music cd in it does autoload though, but takes forever - not sure that has anything to do with it.  Also my laptop froze solid, req'd hard reboot - went looking & that's how I found this error msg - its all I could find - again, not sure they are related.  Haven't done a lot of investigation otherwise - just wanted to report those error codes are still happening in Maverick.

Oct 30 15:51:26 Compal-599-2 kernel: [  174.380690] sr 0:0:1:0: [sr0] Unhandled sense code
Oct 30 15:51:26 Compal-599-2 kernel: [  174.380699] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct 30 15:51:26 Compal-599-2 kernel: [  174.380710] sr 0:0:1:0: [sr0] Sense Key : Medium Error [current] 
Oct 30 15:51:26 Compal-599-2 kernel: [  174.380721] Info fld=0x0
Oct 30 15:51:26 Compal-599-2 kernel: [  174.380725] sr 0:0:1:0: [sr0] Add. Sense: L-EC uncorrectable error
Oct 30 15:51:26 Compal-599-2 kernel: [  174.380737] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 04 3e 22 00 00 01 00

---

