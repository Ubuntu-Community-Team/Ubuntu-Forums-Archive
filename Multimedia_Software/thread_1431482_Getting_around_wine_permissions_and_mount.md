---
title: "Getting around wine permissions and mount"
date: 2010-03-16
forum: Multimedia Software
---

### Post by protiss on 2010-03-16
So here's what I've done so far.

Downloaded an .iso for a windows program.

sudo mount -o loop /home/admin/file.iso /media/dvd  --- no errors.
wine /media/dvd/Installer.exe --- don't have the correct permissions.
chmod ug+rxw Installer.exe --- no dice. (also tried chmod /media/dvd)
ln -s /media/dvd /home/admin/.wine/dosdevices/e:  --- no errors.
wine e:Installer.exe --- following error:
***wine: could not load L"Z:\\media\\dvd\\Installer.exe": Module not found***
if I navigate to .wine/dosdevices/z:/media/dvd, Installer.exe is present.

Not sure where to go from here.  Any ideas or should I just burn the iso?  Thanks.

---

### Post by mc4man on 2010-03-16
Maybe because your using sudo to mount, otherwise should work - 
The only iso I've got here is a live cd, but it does have wubi.exe so to test

I happen to have cdemu installed so mounted the iso and then opened winecfg and auto detected the new drive (E)-  screen 1

Then either of these two commands would run wubi.exe thru wine - screen 2

```
wine E:\wubi.exe
```
or
```
wine '/media/Ubuntu 10.04 i386/wubi.exe'
```

(Note I obviously didn't go ahead and run the installer

---

### Post by protiss on 2010-03-16
well, it's also a dvd .iso, not sure if that changes anything.  I messed around with trying to mount -t udf but got errors about it not being a block something-or-other, only way I was able to get the mount to succeed was with a loop mount.  I was also thinking I could possibly look in to the fstab, so I can get user permissions to mount without invoking root.  I think it's just a permissions issue - if I open wine config and go to e: it says Permission denied when I click on installer.  I guess if anyone has any advice on how you add a non-real drive to fstab that'd probably be my next step.  Or maybe it's just overkill and I'm doing something wrong.

---

### Post by mc4man on 2010-03-16
> Or maybe it's just overkill 
Well you certainly could have burned the iso 10 times over by now...

I only mount iso's occasionally (actually .cue's) so don't pay attention to methods other than I didn't like using sudo nor using the built-in archive mounter.

At some point installed cdemu, read the man, and  made a little nautilus action.

This way I just right click on the .iso or .cue and mount it.
When done I 'eject' the virtual disk. Very clean and easy, no root involved.

( happen to be on lucid atm where nautilus actions are broken or I'd give you the na parameters if you decide to pursue cdemu at some point, (will edit one in I think

(it - cdemu - loads the drive(s) at boot so /dev links are also created, as seen in the rules file
> # Virt._CD_DVD-ROM (platform-vhba-scsi-0:0:0:0)
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="platform-vhba-scsi-0:0:0:0", SYMLINK+="cdrom3", ENV{GENERATED}="1"
SUBSYSTEM=="block", ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="platform-vhba-scsi-0:0:0:0", SYMLINK+="dvd3", ENV{GENERATED}="1"

---

### Post by protiss on 2010-03-23
I solved my problem.  On my system anyways.  Hopefully this helps someone out.

Burned the .iso to a disc**

The reason the installer fails is because the standard mount keeps hidden files, hidden.  Then when you run setup or install or w/e, it can't see what it's looking for, and the process fails.

So when you put your CD/DVD in (DVD in my case), simply do this:

sudo mount -o remount,unhide /dev/sr0

Once that's done, if you change to /media/cdrom you should be able to see additional files.

then I still had to go to root (sudo didn't play well with wine for some reason), and then type:

wine Installer.exe

and bam, I was good.

---

