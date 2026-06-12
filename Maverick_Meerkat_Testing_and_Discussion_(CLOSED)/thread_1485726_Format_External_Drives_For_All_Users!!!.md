---
title: "Format External Drives For All Users!!!"
date: 2010-05-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Col-1023 on 2010-05-17
One annoying problem I have with Ubuntu is that when I format a usb drives, the drive is owned by root, so i have to chmod and chown to fix this.

Would It be possible to make gparted, to ubuntu format a drive with the default set so that all users and can read and write to the drive?

If someone wants the drive to be used by only specific users, then they can use the chmod and chown to change this, or a gui could be made to make changing partition and drive ownerships easy.

---

### Post by Yofel on 2010-05-17
You should file a whishlist bug about that at
[https://bugzilla.gnome.org/enter_bug.cgi?product=gparted](https://bugzilla.gnome.org/enter_bug.cgi?product=gparted)
You could file a bug with 'ubuntu-bug gparted' too, but the someone will still have to forward it to gnome.

---

### Post by andrewabc on 2010-05-17
Is this why in ubuntu 9.10 when I formatted a 1tb drive in external enclosure hooked up via esata, created ext4, it asks me everytime for password to mount it?

Yet it never asks me for password when I mount my usb drives.

---

### Post by zekopeko on 2010-05-17
double post

---

### Post by zekopeko on 2010-05-17
> **andrewabc said:**
> Is this why in ubuntu 9.10 when I formatted a 1tb drive in external enclosure hooked up via esata, created ext4, it asks me everytime for password to mount it?

Yet it never asks me for password when I mount my usb drives.

I assume that the system treats your hard drive as an internal storage and internal storage has a policykit config to allow only admin/approved users to mount drives that aren't in fstab.

Try googling for this. I fixed mine but forgot how exactly. You just need to change a single line in a config file.

Try this: [http://ubuntuforums.org/archive/index.php/t-1308528.html](http://ubuntuforums.org/archive/index.php/t-1308528.html)

---

### Post by andrewabc on 2010-05-17
> **zekopeko said:**
> I assume that the system treats your hard drive as an internal storage and internal storage has a policykit config to allow only admin/approved users to mount drives that aren't in fstab.

Try googling for this. I fixed mine but forgot how exactly. You just need to change a single line in a config file.

Try this: [http://ubuntuforums.org/archive/index.php/t-1308528.html](http://ubuntuforums.org/archive/index.php/t-1308528.html)

Thank you that worked perfectly.

EDIT:
For future reference
gksudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

In section:
id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal"
change to:
<allow_active>yes</allow_active>

---

### Post by psusi on 2010-05-17
Rather than installing and using gparted to format the disk, why not use the included palimeset disk admin utility that is installed on the admin menu by default?  It has an option to take ownership so that it will be owned by you.

---

### Post by ranch hand on 2010-05-17
Wow, I am working from an external enclosure right now and I have never had any problems with it or my other enclosure either.  I fool with them all the time.

I must just be lucky.

---

### Post by zekopeko on 2010-05-17
> **ranch hand said:**
> Wow, I am working from an external enclosure right now and I have never had any problems with it or my other enclosure either.  I fool with them all the time.

I must just be lucky.

The problem was an external **eSata** enclosure. It is detected as an internal disk.

---

### Post by zekopeko on 2010-05-17
> **andrewabc said:**
> Thank you that worked perfectly.

EDIT:
For future reference
**gk**sudo gedit /usr/share/polkit-1/actions/org.freedesktop.devicekit.disks.policy

In section:
id="org.freedesktop.devicekit.disks.filesystem-mount-system-internal"
change to:
<allow_active>yes</allow_active>

Could you fix your post from sudo to gksudo? Using sudo on GUI apps can result in some files being owned by root which could mess your user account.

---

### Post by andrewabc on 2010-05-17
> **zekopeko said:**
> Could you fix your post from sudo to gksudo? Using sudo on GUI apps can result in some files being owned by root which could mess your user account.

Done. I usually sudo whatever needs config files to be edited. I only have one user/password for ubuntu install. So I don't notice any problems that I know of about ownership. Or maybe it does cause lots of problems and I don't realize it (or would if I created new users?).

Using ubuntu since 6.06 and still havn't bothered to figure out which is proper sudo or gksudo (or su?).

---

### Post by zekopeko on 2010-05-17
> **andrewabc said:**
> Done. I usually sudo whatever needs config files to be edited. I only have one user/password for ubuntu install. So I don't notice any problems that I know of about ownership. Or maybe it does cause lots of problems and I don't realize it (or would if I created new users?).

Using ubuntu since 6.06 and still havn't bothered to figure out which is proper sudo or gksudo (or su?).

sudo is for any command line program ala nano , cp , mv etc.

gksudo is for GUI programs ala nautilus, gedit etc.

---

### Post by seeker5528 on 2010-05-17
> **zekopeko said:**
> The problem was an external **eSata** enclosure. It is detected as an internal disk.

If the enclosure is attached to an eSata port, then I would consider that a bug.

If it's not an eSata port, you probably have to live with the limitations.

If it is attached to one of the ports on the mother board and the board only has 2 or 4 ports, I would guess that none of them are eSata.

Later, Seeker

---

### Post by andrewabc on 2010-05-17
> **seeker5528 said:**
> If the enclosure is attached to an eSata port, then I would consider that a bug.

If it's not an eSata port, you probably have to live with the limitations.

If it is attached to one of the ports on the mother board and the board only has 2 or 4 ports, I would guess that none of them are eSata.

Later, Seeker

Well in my case, I have external enclosure, and connected via 'esata' (on enclosure) to my motherboard.

So I guess it is really connected directly to sata port on motherboard in my case.

In picture the far right side I have hooked into tower, made for easy access to plug/unplug sata devices to motherboard.
[[IMG]http://img139.imageshack.us/img139/7783/27852524.th.jpg[/IMG]](http://img139.imageshack.us/i/27852524.jpg/)

---

### Post by seeker5528 on 2010-05-17
> **zekopeko said:**
> sudo is for any command line program ala nano , cp , mv etc.

gksudo is for GUI programs ala nautilus, gedit etc.

That's an overly simplistic way to look at it.

Any program that might create or change files in your home directory when it is run is bad just to do 'sudo foobar' for. 

Take vim for example, when you are working on a document vim keeps a backup copy of it. If you run vim by doing 'sudo vim some-text-file', and something happens that causes the backup to get left behind, then when you run vim as a normal user it will complain about this backup file and no matter what you choose it it can't get rid of it because it is owned by root. I have not seen a lot of this with vim, but I have had it happen and I didn't know what was going on at the time.

If you do 'sudo -H foobar' that will change the home directory for the sudo session so the program you are running will use/create settings and temporary files in root's home directory instead of yours and is everything necessary for CLI programs, and should be fine if using GDM as your display manager. 

If you use KDM or other display manager that starts the X session with overly restrictive options, using 'sudo -H foobar' will fail for GUI programs because of some X credentials thing where using gksudo/kdesudo will take care of the credentials.

Later, Seeker

---

### Post by Col-1023 on 2010-05-17
I've filed a bug report, 


[https://bugzilla.gnome.org/show_bug.cgi?id=618947](https://bugzilla.gnome.org/show_bug.cgi?id=618947)

---

### Post by ranch hand on 2010-05-17
> **Col-1023 said:**
> I've filed a bug report, 


[https://bugzilla.gnome.org/show_bug.cgi?id=618947](https://bugzilla.gnome.org/show_bug.cgi?id=618947)
That is a great idea.  Unfortunately I can't help with it as I do not have that problem.

If no bugs are filed nothing will get fixed.

Good job.

---

### Post by seeker5528 on 2010-05-20
> **andrewabc said:**
> Well in my case, I have external enclosure, and connected via 'esata' (on enclosure) to my motherboard.

So I guess it is really connected directly to sata port on motherboard in my case.

Motherboards that have ports designed for eSata use, have a way to identify them as such, so the OS can tell the difference between the internal and external ports.

In Windows for example a drive that is attached to an eSata port will be idetified as a removable drive and you will have the option to stop or eject it. If it is a regular SATA port, it won't give you those options.

Also it doesn't matter what formatting options you use when you create an ext2/3/4 partition, it's just a file system, it's the options in fstab that determine who can and can't mount and/or create directories on a partition, it's the permissions on the directories that determine who can or can't create files or subdirectories within the parent directory.

I'm not 100% sure, but I think if you install mountmanager it provides options that are relevant for that type of use or at the very least allows you to specify the mount options you want to use and whether you want regular users to be able to mount/unmount the partition. It doesn't look like the utility that shows up at 'System --> Administration --> Disk Utility' does that.

The way I handle my internal drives is to create a directory, then depending on what type of use is intended I will create a group, make that group the owner of the directory, then add the users to that group. If you want everyone to be able to access/edit these then you would change the group ownership to 'users', but I don't know if you can rely on that group always getting the same numerical ID in cases where you are re-installing or using the same external drive on multiple systems.

Later, Seeker

---

### Post by Col-1023 on 2010-05-29
The Gparted devs have decided the bug is invalid because they say it's not Gparted's job to deal with permissions.

So it seems it's either mountmanager of the disk utility (Palimpeset) that can be used to change partition permissions via gui.

Which one of these is best (easiest) for the job?

TIA.

---

### Post by seeker5528 on 2010-05-29
> **Col-1023 said:**
> The Gparted devs have decided the bug is invalid because they say it's not Gparted's job to deal with permissions.

So it seems it's either mountmanager of the disk utility (Palimpeset) that can be used to change partition permissions via gui.

Which one of these is best (easiest) for the job?

Palimpeset lets you mount and unmount partitions, but doesn't give you any way to change the options related to mounting, so it looks like you will have to use mountmanager for this.

On a side note it looks like KDE Partition Manager will handle this, but it doesn't seem to be in the archive, much less at the version that added this capability.

[http://blog.volker-lanz.de/2010/05/28/new-in-kde-partition-manager-1-1-i-mount-management/](http://blog.volker-lanz.de/2010/05/28/new-in-kde-partition-manager-1-1-i-mount-management/)

[http://blog.volker-lanz.de/2010/05/29/new-in-kde-partition-manager-1-1-ii-smart-status-reports/](http://blog.volker-lanz.de/2010/05/29/new-in-kde-partition-manager-1-1-ii-smart-status-reports/)

To avoid problems later on, when you set up the mounts, the pass number only your root partition should be pass 1, everything else should either be 0 if you never want it to be checked for errors during boot or 2 if you do. 

Later, Seeker

---

### Post by DanaG on 2010-06-03
My motherboard quite definitely marks my eSATA port as external -- the stock Win7 AHCI driver sees it as hot-swappable.
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/153768](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/153768)

My comment is #27.  And if there are "patches" (as the kernel upstream bug claims), where the heck are they?  Why not post them?

---

### Post by dino99 on 2010-06-03
> **DanaG said:**
> My motherboard quite definitely marks my eSATA port as external -- the stock Win7 AHCI driver sees it as hot-swappable.
[https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/153768](https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/153768)

My comment is #27.  And if there are "patches" (as the kernel upstream bug claims), where the heck are they?  Why not post them?

bug opened in 2007 and not assigned, only 9 persons have subscribed :confused:

---

