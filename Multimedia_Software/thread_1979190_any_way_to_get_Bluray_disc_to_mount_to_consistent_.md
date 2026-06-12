---
title: "any way to get Bluray disc to mount to consistent location?"
date: 2012-05-12
forum: Multimedia Software
---

### Post by kenyee on 2012-05-12
I'm using 12.04 and when I stick a Bluray disc in, it gets mounted to /media/<volumelabel>.

E.g., the BBC Life series would mount to /media/LIFE_D3, /media/LIFE_D1, etc.
I just want it to mount to /media/bluray or /mount/cdrom or /mount/dvd.  None of these are mounted when you stick a Bluray in :-(

The reason is MythTV only lets me specify a fixed location to play Bluray discs from.
I know I can use makemkv to rip the bluray onto disk first, but I'm trying to see if this works first...

---

### Post by BicyclerBoy on 2012-05-14
Got sick of using mythavtest from cmd-line with 0.24+fixes & with 0.25 it is meant to work from the menus..
Various rants have it you couldn't play the BD from the ubuntu auto-mount point but it always worked for me.

As you found, using the /media/<volume label> in FE setup menu BD mount point works but that is not a workable solution..
I just created a mount point folder (/media/bd-dvd) & an entry in /etc/fstab to mount /dev/sr1 to /media/bd-dvd.
This works fine.
Incidentally, the same trick does not work for DVD (for me).

But I have 2 optical drives (one is DVD only). Using the fixed mount point works for BD (sr1) but not DVD (sr0) & it stops DVD drive disc being detected by MythTV.
So I can't access the DVD drive unless the BD disc is ejected..
The silly optical drive modal chooser/requestor  (mythtv) does not seem to do anything.

Side effects of fixed point mount:
- ugly desktop icons for your mounted optical disks
- myth does not recognise DVD in 2nd drive when BD is mounted.

It would seem a better solution if the system auto-mount path was usable by MythTV just like with DVDs.

---

### Post by nickrout on 2012-05-14
> **BicyclerBoy said:**
> Got sick of using mythavtest from cmd-line with 0.24+fixes & with 0.25 it is meant to work from the menus..
Various rants have it you couldn't play the BD from the ubuntu auto-mount point but it always worked for me.

As you found, using the /media/<volume label> in FE setup menu BD mount point works but that is not a workable solution..
I just created a mount point folder (/media/bd-dvd) & an entry in /etc/fstab to mount /dev/sr1 to /media/bd-dvd.
This works fine.
Incidentally, the same trick does not work for DVD (for me).

But I have 2 optical drives (one is DVD only). Using the fixed mount point works for BD (sr1) but not DVD (sr0) & it stops DVD drive disc being detected by MythTV.
So I can't access the DVD drive unless the BD disc is ejected..
The silly optical drive modal chooser/requestor  (mythtv) does not seem to do anything.

Side effects of fixed point mount:
- ugly desktop icons for your mounted optical disks
- myth does not recognise DVD in 2nd drive when BD is mounted.

It would seem a better solution if the system auto-mount path was usable by MythTV just like with DVDs.

What would be easiest would be if you didn't have to mount it at all. I have always played DVD's with mplayer which needs the device node (/dev/sr0) not a mount point (/media/whatever).

I was playing with this last night and getting nothing but errors even with mythavtest. Perhaps you could tell me:

1. How do I tell what my bluray is encrypted with, given some work and some don't, often depending how new the bluray is.

2. How can I be sure my encryption keys etc are set up correctly?

---

### Post by BicyclerBoy on 2012-05-15
BD don't have an obfuscated file system so auto-mount is no problem.
Direct device access is required to read the media key blocks.

I believe there are cues/clues in the folders present on the disc.
I use dumpHD & aacskeys from doom9 to check the disc etc & find the correct entry in the keyDB (aacskeys format).
If it does not exist, I extract it & save it back to keyDB.
Then copy/reformat the required entries from keyDB on a as-needed basis into the mythtv keyDB (libaacs format).
I play the disc direct from the optical drive with mythtv.

You can compile libbluray with bd-java enabled but I'm not what this is going to do & mythtv has its own private copy anyway.

If there is a specific title (& it's watchable) I'll rent it & see if it works..

"Sanctum" could be worth a look..

The most recent titles I have played have dates from Sept 2011.

---

### Post by BicyclerBoy on 2012-05-19
The /etc/fstab method works but the icon is an ugly CD.
```
/dev/cdrom1      /media/bd-dvd      auto    ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,umask=0077        0

```

The udev method works (BD playback) & you get a nice small icon (from the BD) on the desktop.
```
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:1f.2-scsi-4:0:0:0", ENV{ID_FS_TYPE}=="udf", SYMLINK+="bd1", ENV{GENERATED}="1", ENV{ID_FS_LABEL_ENC}="bd-dvd"

```

---

### Post by Personatech on 2012-07-11
> **BicyclerBoy said:**
> ...I just created a mount point folder (/media/bd-dvd) & an entry in /etc/fstab to mount /dev/sr1 to /media/bd-dvd.
This works fine.
Incidentally, the same trick does not work for DVD (for me).
For the record, setting up an entry in fstab worked for me for both playing BR or standard DVDs through a single LG BR drive.  I also had to set up automount in Thunar for some reason.

---

