---
title: "Mythbuntu partitions guidance"
date: 2007-12-21
forum: Mythbuntu
---

### Post by se99paj on 2007-12-21
Could you give me some guidance specifically regarding mythbuntu partitions during installation.

I have a 250GB HDD and I want to use the majority of the space for storing videos and music.

During my previous installation I think I cocked up somewhere as mythbuntu doesn't seem to be able to access the majority of my HDD.

---

### Post by andrewb78 on 2007-12-21
Do you recall how you partitioned the drive last time?

On my drive, I set up three partitions.  One is the / partition, which is about 20 GB and is ext3.  One is the swap partition, which is about 2GB.  The rest of the disk I partitioned as /myth and is JFS.  This partition needs to have a file system that can handle very large files.  Now that I've used the box for a bit, I wish I hadn't partitioned it as /myth but rather as /var/lib, as it might have saved some configuration steps later.

It's probably better yet to do something with LVM, but I didn't look into that.  Perhaps someone else can help you there.

---

### Post by se99paj on 2007-12-22
Unfortunately I was in a bit of a rush as I had to go off to work. (I know its a pretty stupid excuse).

I'm half tempted to reinstall mythbuntu, I haven't made that many changes since the installation.

What I am looking for is almost identical to your setup, 3 partitions, one swap one root and the the rest of the HDD as to store videos/music/pictures so they can be viewed by other PC's on the network. 

If I wanted to do this then would I only need to set the bigger partition as the /var/lib directory during the partitions stage of the installation?

---

### Post by andrewb78 on 2007-12-22
If you want, you could try using gparted rather than hosing and reinstalling your box (which you might get to do anyway if gparted doesn't go well :) ).

```
sudo aptitude install gparted
```

then

```
sudo gparted
```.

That will at least show you your partition table.  If you don't care about a graphic interface, substitute parted for gparted above.  I'm no partition table expert, so I will defer to others who might be.

---

### Post by StooJ on 2007-12-24
I'm messing about finding my way around the world of Myth as well.

Partitioned my drives as I would a desktop:
/ = 10gb ex3
swop = 2gb
/home = 235 gb ex3

Which is completely WRONG! :D

Starting again with:

/  = 20gb ex3
swop = 2gb
/var/lib = 235gb JFS

Hopefully this'll work out better all round.

---

### Post by mymythtv on 2007-12-24
Hmm - why making it so complicated ?

I installed Mythbuntu with the following partition:
/boot - 500 Mb - ext3
swap - 2Gb
/ - all remaining space - xfs

It's "one big fill it all" partition - don't worry about /var/lib or anything else

Just beware that system-files are on same partion as recordings, videos, audio and so on...

I could go for a split of / into / and /var/lib, but thats another story as my setup was/is just a "test setup"  :)

Hope it helps...

---

### Post by newlinux on 2007-12-24
On my systems I do:

/ - 10GB
swap - 2GB 
/storage - rest - XFS

/storage is where I store recordings for my backends. Having it on a separate partition allows me to reinstall the OS without losing any recordings.

---

### Post by k3lt01 on 2007-12-24
I am wondering what the advantage is to using a different file system to ext3, which people are using as the / , for the partition which contains the media files. If someone could explain the idea to this I would appreciate it.

---

### Post by andrewb78 on 2007-12-24
From what I understand, the reason to go with JFS or XFS for the partition where the video files go is that these filesystems have much better support for large files than a filesystem like ext3 does.  In particular, it is best if the filesystem can do delete operations on large files quickly, which JFS at least does quite well.

The reason I don't just put everything but my boot and swap partitions into the giant JFS partition is that there are basic system operations that will fail if the disk is full.  I want to guarantee that the system can run even if Mythbuntu has used up every last bit in the large partition so that I can fix it if there are problems.  Also, this way, Myth-generated logs can still happen even if the disk is full.  You might not need 20 GB for the / partition, but I wanted to be able to do some basic normal-desktop-computer stuff as well. 

I would really rather have the large partition be something like /var/lib/mythtv instead of /var/lib, but as of Mythbuntu 7.10, there is also /var/lib/mythdvd (I think) as well, so I settle for /var/lib rather than trying to create two separate partitions.  (Or, I would at least if I was doing this again rather than naming the large partition /myth.)

---

### Post by newlinux on 2007-12-25
XFS and JFS have much better large file support, as already mentioned. If you use EXT3 for your recordings, I would enable the "Delete Files Slowly" Option.

I use my computers as regular desktops too, but I have a file server for all user files, and 10GB has always been more than enough for any apps I want to install. Each person's situation is a little different, but hopefully you have enough examples and guidelines to tailor it to your own situation.

---

### Post by GLMontyWV on 2007-12-27
So lets say I have two drives in my PC, a primary 80GB and a secondary 250GB.  I want to use the 80GB for two distros ( 1 + Mythbuntu), my swap, and my /home and my secondary 250GB drive for just media.  

How would be the best way to set that up?

Thanks, Monty

---

### Post by andrewb78 on 2007-12-27
I would say that on the smaller disk, you need four partitions.  I would guess probably 10-15 GB for each of the distributions (each will be mounted as / within its own distribution), 2 GB for swap, and the rest for /home.  All these partitions (except swap) can probably be ext3, assuming your other distribution can read and write ext3.  For the larger disk, you can have the whole thing be one partition that, if you are going to access from both distributions, I would mount as /myth rather than /var/lib and make the necessary configuration changes in Mythbuntu.  This partition (the whole disk) should probably be JFS.  The reason I would go with /myth rather than /var/lib is that the two distributions may have different, conflicting things in /var/lib besides MythTV stuff.

You'll have to do some work to make sure that the partitions get mounted the way you want in the different distributions, and you will probably have some bootloader work to do to get this dual-boot system going.  I'm not sure off the top of my head how to do those things, but you might see the GRUB documentation, for instance.

---

### Post by theacoustician on 2007-12-29
This is a great topic.  I really think this is something  that needs to go front and center in the Mythbuntu guide.  Setting up partitions and the advantages/disadvantages of which file system to use could make a real big difference in system performance, expandability, and just general information about the Linux file structure for those new to it.

Speaking of expandability, another good one that needs more coverage is the backend server, multiple frontend client config is getting more popular, but it seems to have the least amount of stuff written on it.

---

### Post by Furry_Fighter_20x66 on 2007-12-29
> **se99paj said:**
> Could you give me some guidance specifically regarding mythbuntu partitions during installation.

I have a 250GB HDD and I want to use the majority of the space for storing videos and music.

During my previous installation I think I cocked up somewhere as mythbuntu doesn't seem to be able to access the majority of my HDD.

You might want to try some like I did with my setup assuming you have the spare parts. Price was a factor when I built mine. It runs on almost all salvaged pieces of hardware (an old desktop P700 to be exact) except for one brand new HD. Instead of having all my stuff on one drive I did the following.

hda - 20 gig drive - / 
hdb - 350 gig drive - all myth recordings and myth temp directories are held on this drive.
hdc - DVD burner
hdd - 80 gig drive - stores all of mythvideo and mythmusic recordings.

There is also a small assortment of external drives for backup of hda and hdd drives and extra file storage for the rest of my network. If one drive goes dead in this I can simply swap it out, restore the backup and continue. If hdb goes dead I shrug and put a new drive in, at least in theory. Fortunately I have never had to do this to any of the drives.   

With high definition television on the horizon my intention in a few years is to build a new system. I haven't made much thought to it yet but it will have some raid setup.

---

### Post by erland on 2007-12-31
> **mymythtv said:**
> Hmm - why making it so complicated ?

I installed Mythbuntu with the following partition:
/boot - 500 Mb - ext3
swap - 2Gb
/ - all remaining space - xfs

It's "one big fill it all" partition - don't worry about /var/lib or anything else

Just beware that system-files are on same partion as recordings, videos, audio and so on...

Putting the system files on the same partition as the recordings are IMHO a big mistake. The problem with this is that it won't give you the chance to do a clean install when you like to upgrade to the next version of the OS. To make a clean install, you really want to format the system partition but you still want to keep the recordings.

My partitioning looks as follows:
/ - 20GB
swap - 1GB
/media/xxx - The rest 

Recordings are stored in /media/xxx/recordings.

The only thing you need to remember in this scenario is to take a backup of the MythTV mysql database before you format the system partition before an upgrade.

---

### Post by dudeskeeroo on 2008-01-03
I highly recommend LVM.  Once you've had LVM you'll wonder how you ever did without it.  It may take a little bit of reading and playing around but the payoff is well worth it.

On my Mythbuntu system I have 2 HDD and have the following physical partition scheme:

sda1 - boot (300MB)
sda2 - swap (2GB)
sda3, sdb1..n (LVM PVs)

I prefer to split a disk up into multiple chunks to add them to LVM (in case I need to reclaim one later).  e.g  a 320GB sdb *may* look like this (sample only):

sdb1 - 100GB
sdb2 - 100GB
sdb3-5- 40GB each

Then the LVM has the following Logical Volumes (LVs):

> 
/dev/mapper/vg-mythbuntu64 on **/** type ext3 (rw,errors=remount-ro)
/dev/mapper/vg-home on **/home** type ext3 (rw)
/dev/mapper/vg-images on **/var/lib/mythtv/pictures **type ext3 (rw)
/dev/mapper/vg-music on **/var/lib/mythtv/music **type ext3 (rw)
/dev/mapper/vg-root on **/media/old-mythtv **type ext3 (rw)
/dev/mapper/vg-recordings on **/var/lib/mythtv/recordings** type jfs (rw)
/dev/mapper/vg-videos on **/var/lib/mythtv/videos **type jfs (rw)


As you can see the diferent partitions have different filesystems that are best at their particular purposes, and you can make them as big or as small as required.  If you want to add another Linux OS, you can create a new LV and use it as the root partition (recycling /home LV etc. if required).

Unfotunately the LVM setup isn't pointy-clicky with the Mythbuntu LiveCD. There are several threads around describing how to setup LVM prior to clicking the installer icon. Basically you need to follow these steps (assume sudo):

[LIST]
[*]Install the LVM package in the live environment (apt-get install lvm2)
[*]Load the LVM kernl module (modprobe dm-mod)
[*]Partition your disks (gparted).
[*]Create your Physical Volumes (PVs, using pvcreate)
[*]Create a Volume Group (VG, vgcreate)
[*]Create each LV (lvcreate)
[*]Create the filesystems for each LV (mkfs.ext3, mkfs.jfs, mkfs.xfs etc.)
[/LIST]

I'm running from memory here so accuracy may not be 103%.

You should now see the LVs in the installer process.

Once everything is installed, you may need to chroot to the new installation (chroot /target) to install the LVM package on the new system (apt-get install lvm2) and add the dm-mod module to the /etc/modules (echo dm-mod >> /etc/modules).

In the LiveCD environment you can play around with LVM, creating and destroying VGs, PVs and LVs until you get a feel for what is going on.  Once you are comfortable with the commands, figure out what your space requirements are and create your LVs.

Some really handy commands for showing you what is going on with your LVM are **vgs**, **pvs** and **lvs** (using sudo).

Remember, it is easier to make a LV bigger than it is to make one smaller (depending on the overlying FS type).

Rock on.

---

### Post by mymythtv on 2008-01-04
> **erland said:**
> Putting the system files on the same partition as the recordings are IMHO a big mistake. The problem with this is that it won't give you the chance to do a clean install when you like to upgrade to the next version of the OS. To make a clean install, you really want to format the system partition but you still want to keep the recordings.

My partitioning looks as follows:
/ - 20GB
swap - 1GB
/media/xxx - The rest 

Recordings are stored in /media/xxx/recordings.

The only thing you need to remember in this scenario is to take a backup of the MythTV mysql database before you format the system partition before an upgrade.

I Agree, but my answer to the original question was based on the fact that he had one big 250Gb disk :-)
I just build my first mythtv system, and I have a 40Gb disk for the system ( properly partitioned, ext3 ) and a seperate disk for recordings ( xfs )
so I agree that mere physical disks are a "must have", and yes - backup your database :-)

---

