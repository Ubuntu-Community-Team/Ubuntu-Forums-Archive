---
title: "How To LVM in Mythbuntu"
date: 2007-10-21
forum: Mythbuntu
---

### Post by apauna on 2007-10-21
Hello, Here is my first contribution to the cause! I am not sure if this is the best spot for this type of a thing, but at least it may help someone! :)

After installing Mythubuntu RC I manually configured lvm. 

What is lvm? 

It lets you span partitions into on large volume so that one can add more space later on.

In the below example we have two disks *sda sdb* and we want to create a lvm partition on sdb and include sda3 in that lvm so that the /var/lib directory is mounted on lvm partition. This means that /var/lib will span sdb1 and sda3. When I installed Mythbuntu I manually created the partitions and sda1 mounts / (root) and sda2 is swap with sda3 as the /var/lib partition. This was similar to the way Feisty installs were done in the old days. **It is also important that the sdb partition be large enough to hold all of /var/lib**
df -h will display the used space in mounted partitions. In my case I deleted all the recordings so that I could fit it on sdb only around 20 GB in my case. 
```
df -h
```

Steps:
 All connections to myth box should use sudo after terminal is open:
```
sudo -i
```


[LIST=1]
[*] Open a terminal window or SSH into myth box.
[*]Get LVM2 from apt-get
```
apt-get install lvm2
```
[*]Reboot **Note: I had to anyway because it messed with the kernel or boot or something**
```
shutdown -r now
```
[*]setup an lvm partition. **Note: this example assumes that the sdb disk is empty!**
***Remember that fdisk can really mess up your existing partitions so know what you are doing before you start doing this stuff! You have been warned!!!!***
```
fdisk /dev/sdb
```
[*]At Command (m for help): type **n** 
[*]At Command action 
e extended 
p primary partition (1-4) type **p** 
[*] At Partition number (1-4): type **1**
[*] At First cylinder (1-19457, default 1): **(press Enter for default)** 
[*] At Last cylinder or +size or +sizeM or +sizeK (1-19457, default 19457): **(Press Enter for default)**
[*] At Command (m for help): type **t**
[*] At Hex code (type L to list codes): type **8e** 
[*] At Command (m for help): type **w**
[*]Create the physical volume.
```
pvcreate /dev/sdb1
```
[/LIST]
Great we have a physical lvm partition sdb1 created!

[LIST=14]
[*]Now we have to create the lvm stuff for the volume.
**Note:  Example below is for about 500 GB use the power of two to go to larger table sizes. use 16M for example is for over 1 TB volumes**
```
vgcreate -s 8M vg /dev/sdb1
```
[*]Get the vg lvm volume size
```
vgdisplay vg | grep "Total PE"
```
[I]Display shows on my pc:
Total PE              9543
Use that value in cmd below replace 9543 with your value.[/I]
```
lvcreate -l 9543 vg -n lib
```
[*]This starts the device mapper on startup. Not sure if this is needed or not, but will not hurt anything.
```
modprobe dm-mod 
echo dm-mod >> /etc/modules
```
[*]format the partition as xfs **Note: LVM partitions created as XFS are difficult to size down, so note that it may not be possible to make smaller very easy, at least that is what I heard on the net. Anyway why would you want to remove space from your lvm. I can only see it getting bigger so that I can store more stuff on it.**
```
mkfs.xfs -f /dev/vg/lib
```
[*]Make a mount point and mount.
```
mkdir /mnt/sdb1
mount /dev/vg/lib /mnt/sdb1
```
**Note: It may be wise to stop myth back-end and mysql at this point, but I did not but do not do this step or following steps why recording anything.**
[*]copy all from /var/lib into mounted sdb1.
```
cp -p -r /var/lib/* /mnt/sdb1
```
[*]Make a copy of fstab
```
cp /etc/fstab /etc/fstab.backup
```
[*]Fix fstab to mount lvm vg-lib as /var/lib
```
nano /etc/fstab
```
[*]Comment out your current /var/lib in fstab 
line looks like *#UUID=3aa29488-1c13-4042-a246-3f317aa7ddf7 /var/lib        xfs     defaults * in my fstab
[*]Add the new mount-point for xfs lvm partition in fstab file. Iplaced it at the bottom of the file.
```
/dev/mapper/vg-lib /var/lib xfs defaults 0 1
```
save the fstab file.

Here is my fstab when done.
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=682462da-1414-48a7-8614-21c45ba68529 /               ext3    defaults,erro$
# /dev/sdb1
# UUID=d790b268-b2af-4380-92f4-e1a8192fbd65 /var/lib        xfs     defaults   $
# /dev/sda2
UUID=f9e95dd5-155e-4100-b34c-0725ccfc92d9 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0

# mount lvm vg-lib  as /var/lib
/dev/mapper/vg-lib /var/lib xfs defaults 0 1


[*]reboot the system and confirm var/lib is there. If it is not then set the fstab back so 
that you can recopy it to /mnt/sdb1
```
ls /var/lib
```
Almost done!
Now add the space taken up by sda3 to the volume group.
[*]fix sda3 with fdisk.
```
fdisk /dev/sda
```
[*] At Command (m for help): type **d**
[*] At Partition number (1-4): type **3**
[*] At Command (m for help): type **n**
[*] At Command action
   e   extended
   p   primary partition (1-4): type **p**
[*] At Partition number (1-4): type **3**
[*] At First cylinder (1-19457, default 1):  **(press Enter for default)** 
[*] At Last cylinder or +size or +sizeM or +sizeK (1-19457, default 19457): **(Press Enter for default)**
[*] At Command (m for help): type **t**
[*] At Partition number (1-4): type **3**
[*] At Hex code (type L to list codes): type **8e**
Changed system type of partition 3 to 8e (Linux LVM)
[*] At Command (m for help):type **w** 
[*] Finish creating the partition
```
pvcreate /dev/sda3
```
[*] Extend the vg lvm partition
```
vgextend vg /dev/sda3
vgdisplay
```
note the line:
*Free PE / Size	2925 / 11.43 GB*
[*]extend the vg lvm by the amount indicated above in my case 2925 so that is the +2925 below it is important to use your value not mine.
```
lvextend -l+2925 /dev/vg/lib
```
[*]extend xfs  
```
xfs_growfs /var/lib
``` 

[*]confirm sizes
```
df -h
```           
[*]reboot 
```
shutdown -r now 
```
[/LIST]

---

### Post by superm1 on 2007-10-21
Awesome tutorial.  I'm going to sticky this, and we'll see if we can sneak it into our install manual.

---

### Post by davemorris on 2007-10-21
Nice guide, I don't suppose you know how to recover from a drive failing in the volume, or adding new drives to the volume do you?

---

### Post by davemorris on 2007-10-21
stupid me, you already show how to add a drive to a LVM volume.

---

### Post by apauna on 2007-10-21
> **davemorris said:**
> stupid me, you already show how to add a drive to a LVM volume.

Failing drive in the lvm is something I have not spent any time on as of yet.

Try [http://codeworks.gnomedia.com/archives/2005/general/lvm_recovery/]("http://codeworks.gnomedia.com/archives/2005/general/lvm_recovery/")

I will do some more research on this, but I think it really depends on how the data spans across the partitions in the LVM. In the above all that is affected is /var/lib, so the system remains semi bootable

---

### Post by boob11 on 2007-10-22
thnx

---

### Post by Meph1st0 on 2007-10-23
Could you elaborate on this part?

> Now we have to create the lvm stuff for the volume.
Note: Example below is for about 500 GB use the power of two to go to larger table sizes. use 16M for example is for over 1 TB volumes

I have two 320 GB hard drives that I want to setup as an LVM.  When I installed mythbuntu I setup my partitions as you had described on my first drive.  I used 10 GB for / and 2048 for Swap and the rest for /var/lib.  So for my 600 something GB LVM partition would I use 8M like you did?  Should I use the same command here? 
```
vgcreate -s 8M vg /dev/sdb1
```

Also for the following step it says to format as XFS.  I had formatted /var/lib with JFS.  Will this be a problem?

> format the partition as xfs Note: LVM partitions created as XFS are difficult to size down, so note that it may not be possible to make smaller very easy, at least that is what I heard on the net. Anyway why would you want to remove space from your lvm. I can only see it getting bigger so that I can store more stuff on it.

And finally my last question.  I know this one is a really obvious newb question but how do I stop the backend and mysql?

> Note: It may be wise to stop myth back-end and mysql at this point, but I did not but do not do this step or following steps why recording anything.

---

### Post by apauna on 2007-10-24
Hello Meph1st0,

> I have two 320 GB hard drives that I want to setup as an LVM. When I installed mythbuntu I setup my partitions as you had described on my first drive. I used 10 GB for / and 2048 for Swap and the rest for /var/lib. So for my 600 something GB LVM partition would I use 8M like you did? Should I use the same command here? 


In your case I would use.
```
vgcreate -s 16M vg /dev/sdb1
```

This would let you add more partitions later and not have to worry much about what you started vgcreate with. It is possible to fix this later, but less messing around is always better.

> Also for the following step it says to format as XFS. I had formatted /var/lib with JFS. Will this be a problem?


I assume you are referring to your original /var/lib partition and not the one that will be mounted as /var/lib when you complete this process. As long as that is true you will be fine all that is going to happen is data on that /var/lib will be copied from /var/lib onto starting lvm partition and the format of the partition does not have any affect on the data that it contains. /var/lib will be absorbed into the lvm later in the process. see second step 12 > fix sda3 with fdisk.
 
In my case this was the original var lib and was re-partitioned below that step and added to the lvm.

lvm partition can be may types ext3 was the first one I used, but for performance I chose xfs type. 

here is some more info on lvm and xfs
[http://wiki.randompage.org/index.php/DistOS:Linux:LVM]("http://wiki.randompage.org/index.php/DistOS:Linux:LVM")

---

### Post by Meph1st0 on 2007-10-25
I ran into a problem.  After I tried mounting the LVM volume to /mnt/sdb1 (second step number 5) I got an error message on the desktop (not in the xterm).

Saying it couldn't mount due to an NTFS volume named "replacement".

I installed Gparted through the synaptec installer to look at the volume.  The device named /dev/mapper/vg-lib has the following error message.

xfs_db: /dev/mapper/vg-lib contains a mounted filesystem.

fatal error -- couldn't initialize XFS library

/sdb used to be used as an NTFS formatted drive for windows.  During the Mythbuntu install, I had deleted the partition but didn't create any.  It looks like it's still able to see my ntfs partition.

Can I just undo everything I've done (remove my Physical Volume, Volume Group and Logical Volume) and start over?  Or is there an easy fix to this?

---

### Post by Meph1st0 on 2007-10-25
Nevermind, I think I was able to get through this.  My df -h shows:

<code>Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  1.5G  7.3G  17% /
varrun                506M  216K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M  104K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/mapper/vg-lib    585G   81G  504G  14% /var/lib</code>

and /var/lib is there with all the files as far as I can tell.

except now I can't connect to the mythconverg databse.  Please refer to the following post: [http://ubuntuforums.org/showthread.php?t=591891](http://ubuntuforums.org/showthread.php?t=591891)

I don't want to dirty up this thread any more than I already have.

---

### Post by ubuntology on 2007-10-28
Is there any way at all to do this at install time?
I have a 40GB drive as sda and an 80GB drive as sdb.

---

### Post by superm1 on 2007-10-28
You can follow these manual steps prior to install if you would like.  There is no GUI (yet) for this however built into the installer.

---

### Post by ubuntology on 2007-10-28
OK. Thanks,

---

### Post by Etih on 2007-11-05
There is one other way to do the Mythbuntu install with LVM.  I used the Ubuntu Server alternate CD to install Ubuntu  server on a 2 HDD system with LVM.  I used the server install because I wanted an install with as little extraneous packages as possible.  I then installed the mythbuntu-desktop package via the commandline with: 

sudo apt-get install mythbuntu-desktop


This method gives you a bit more options for setting up your partitions and LVM.

One tricky but easy to deal with issue I ran into was installing the proprietary 3D drivers for my Nvidia card. I found out that you have to uninstall the server kernel and install the generic kernel, because the server kernel does not have a pre-compiled package for the restricted kernel modules

---

### Post by trimeta on 2007-11-28
Is there anything else one needs to know to convert a ubuntu-server install into a mythbuntu install? It looks like ubuntu-server makes LVMs trivial, and I'd much rather just install that and then apt-get install mythbuntu-desktop than mess with the 30-odd steps mentioned in the first post.

---

### Post by superm1 on 2007-11-28
> **trimeta said:**
> Is there anything else one needs to know to convert a ubuntu-server install into a mythbuntu install? It looks like ubuntu-server makes LVMs trivial, and I'd much rather just install that and then apt-get install mythbuntu-desktop than mess with the 30-odd steps mentioned in the first post.
Yeah you should be able to go this route, but you will just have post install configuration steps to sort out still that are normally handled by the installer.

---

### Post by dudeskeeroo on 2008-01-03
Hi,

LVM is fantastic and I now use it for everything (mediabox, laptop, desktop, SLUG).  The ability to grow a FS or take a snapshot (or even add another distro) is invaluable for managing a myth box.

Compared to the original poster (thanks for bringing LVM to people's attention =D>), I preferred to go a little more fine-grained with my LVM setup.  I have created LVs for each of the music, pictures, recordings and videos directories (as well as /home and the root partition...and my swap partition is getting more nervous every day :roll:).

With this scheme you can allocate your space more efficiently and also use different file systems for different directories (I use JFS for recordings and videos, and ext3 for the others...you can use your favorites instead).

Also, when trying out a new distro (e.g. when I tried Mythbuntu!) you can easily reuse your /home in the new installation, and your music/pictures/videos will all be accessible from the VG. \\:D/

Here is the relevant output of my mounts:

> 
/dev/mapper/vg-mythbuntu64 on / type ext3 (rw,errors=remount-ro)
/dev/mapper/vg-home on /home type ext3 (rw)
/dev/mapper/vg-images on /var/lib/mythtv/pictures type ext3 (rw)
/dev/mapper/vg-music on /var/lib/mythtv/music type ext3 (rw)
/dev/mapper/vg-root on /media/old-mythtv type ext3 (rw)
/dev/mapper/vg-recordings on /var/lib/mythtv/recordings type jfs (rw)
/dev/mapper/vg-videos on /var/lib/mythtv/videos type jfs (rw)


For those of you who like GUI stuff, there is a tool called **system-config-lvm** that is very useful for getting a n00b head around this LVM business.  Unfortunately it isn't available in the repos :-({|= but you can get a hold of the RPM and use the **alien** tool to make it into an installable package. 	:-$  See [http://www.linuxforums.org/forum/ubuntu-help/104528-how-install-system-config-lvm-ubuntu-feisty-7-04-a.html](http://www.linuxforums.org/forum/ubuntu-help/104528-how-install-system-config-lvm-ubuntu-feisty-7-04-a.html) (first google hit) for details on how to install it.

I hope this is helpful to someone. :)

---

### Post by AusIV4 on 2008-01-04
For what it's worth, I recommend people use LVM even if they don't think they need it. It makes it much easier to expand or regroup later on.

For example, I have a 500 GB RAID 5 array (3x250), and even though this is one device, I use LVM to make one logical volume out of it. Next summer, I hope to buy two 500 GB drives, and make a 500 GB RAID 1 array (2x500). Since I put an LVM layer on top of my current RAID array, I'll be able to add my new 500 GB array to the volume group and expand the physical volume to 1 TB without ever taking my volumes offline (except to shut down so I can plug in the new devices).

---

### Post by rusty0101 on 2008-01-14
One reason you might want to size down the partition is to replace hardware for even more capacity. As an example, I started out with three 400 G PATA IDE hard drives in my current system. When I replaced the motherboard a couple of weeks ago, the new motherboard only came with 1 PATA IDE bus, but 4 SATA IDE interfaces. I elected to add a couple of 500 gig SATA drives to my LVM, and along with the SATA DVD-R/W(+/-) and a sata to pata plug I now have all existing drive interfaces in use.

Let's say I would really rather use all of the SATA interfaces for 500G drives as one logical volume to improve performance. (It's not necessary. The highest bandwidth requirement I'm going to have when handling video files is moving them, which in my case is almost always across the net, but just for consideration.)

To do that, and have a dvd drive that doesn't use a usb port, I'm going to have to drop at least two of the 400G hard drives that are in the LVM. The process is time expensive enough to be reasonably discarded for many people. After all it's just video, you can almost always re-record it. Right? Well perhaps. But in this case I would rather not. At the very least it's a pain to copy things back and forth over the net.

Similarly I could decide to replace all the SATA devices with 1 TB drives in the next couple of years. Having the opportunity to re-size the LVM to get the hadware that I don't want to keep in the system off the LVM is somewhat handy. If it can't be done with XFS, that suggests to me that XFS isn't the correct file system for a dynamic system.

Now there are "out's." You could use an external drive or array of drives via firewire or USB to backup the entire LVM, replace the hardware, and build a new LVM around the new hardware, move the content back off the external drive, and re-mount the drive at the appropriate mount point.

Another option is to use a USB to IDE adapter to attach the drive you are migrating off of through a USB connection, then pvmove the content from that drive to the new hardware, extend it, etc. However I've had some mixed results with some of those adapters. I'm inclinded to sugest using them as a last resort.

All that said, Start by getting the hardware that makes sense for you to get, and work out what strategy you want to use to deal with migrating to new resources if that is something that will come up.

---

### Post by nunrgguy on 2008-02-09
Fantastic tutorial. Just got this working here:guitar:
I tihnk there's a typo at 12 though:
fix sda3 with fdisk.
Code:

fdisk /dev/sda

Should be fdisk /dev/sda3
Otherwise you'll end up formatting the entire drive rather than partition 3

---

### Post by llsouder on 2008-02-25
Hello all,
I found this procedure in the pdf manual but there was an error.  
Some of the places it used <Volume name> and then some it used "vg"

So I called my volume vol2 then when I got to the parts that had vg I got an error.  Now that I found this post I can easily continue.  But some of the vg's in the manual need to be replaced with <Volume Name>

---

### Post by blaze416 on 2008-03-07
I am having an error right out of the box.  When i go to fdisk sdb it tells me that it is unable to open.  can anyone help me out?

---

### Post by lime4x4 on 2008-03-15
Will this work on the hardy version of mythbuntu? And also can the drives be mixed meaning using sata and ide drives? or would that be a performance hit?

---

### Post by apauna on 2008-03-16
> **lime4x4 said:**
> Will this work on the hardy version of mythbuntu? And also can the drives be mixed meaning using sata and ide drives? or would that be a performance hit?

1. I just tried on my Alpha 3 Hardy PC and it worked fine. Same instructions as I originally posted.

2. Mixing most likely will have a small impact on performance, but I have successfully done LVM even to external USB drives and had it work fine. There is also a concept called striping that can help.

Check out the link below for more info on advanced LVM topics:
[http://tldp.org/HOWTO/LVM-HOWTO/]("http://tldp.org/HOWTO/LVM-HOWTO/")

---

### Post by bigredradio on 2008-03-18
Here is a more up to date LVM guide. This one is by RedHat. This is by the maintainers of LVM

[http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/Cluster_Logical_Volume_Manager/index.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/Cluster_Logical_Volume_Manager/index.html)

---

