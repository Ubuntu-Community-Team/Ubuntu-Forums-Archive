---
title: "Beta does not recognize existing partitions"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Mooney10 on 2010-09-19
When trying to install the new beta, I am having an issue on my Acer Aspire 6930 laptop. I have a 320GB SATA HDD and Windows 7 installed on half the hard drive. So 150gb/150gb real space available more or less. I have tried reinstalling Windows 7 and the error persists:


Essentially it does not recognize the partitions that exist on the hard drive in the installer, however I can mount and view the files in the. (I unmounted the partition before beginning installation).

So the options I see are A) fix the problem or B) Install Linux first and then hopefully figure out afterwards.

Any ideas?

---

### Post by mörgæs on 2010-09-19
This forum will help you better:
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

Edit by staff: Thread moved to Maverick.

---

### Post by psusi on 2010-09-19
Open a terminal window and post the output of sudo fdisk -lu /dev/sdb.

---

### Post by Mooney10 on 2010-09-19
> **psusi said:**
> Open a terminal window and post the output of sudo fdisk -lu /dev/sdb. 
Here you go.

ubuntu@ubuntu:~$ sudo fdisk -lu /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe1bf4456

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2          206848   317939711   158866432    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by psusi on 2010-09-19
Hrm... what about sudo parted /dev/sdb print?

---

### Post by Mooney10 on 2010-09-19
> **psusi said:**
> Hrm... what about sudo parted /dev/sdb print?

Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?  

What should i do?

---

### Post by 23dornot23d on 2010-09-19
You might want to have a look at it first ..... 

I repaired mine using testdisk a while back ..... but you need to know what you are doing
otherwise all sorts of things can go wrong .... here is one of [the help pages]("http://www.cgsecurity.org/wiki/Running_TestDisk")

I think the procedure is something like this just to get you in and out without causing damage ......

Make a Backup .......
Analyze ... Y ..... (NTFS check) ... Y ..... Quit .... Quit ..... Quit ......

Its best to get as much information as you can first before commiting to anything.

It tells you a lot .... and then you are left to make choices .....
( I have done this and its worrying with a 1 Terra USB hard drive at stake ...... although it tends
just to hold backups on it ......)

---

### Post by srs5694 on 2010-09-19
First, you've posted information on your *second* hard disk (/dev/sdb). This may be what you intended, but most laptops have just one internal hard disk, which turns up as /dev/sda in Linux. If you intended to install to /dev/sda, you might find it useful to unplug /dev/sdb (if it's an external drive) and deal with its problems later.

The problem with /dev/sdb is that you've got two conflicting partition tables -- or one partition table and most of another. Therefore, the partitioning tools don't know what to do with the disk. This problem is easily corrected; however, you've got to know what you're doing to fix it. To that end....

You've clearly got a complete Master Boot Record (MBR) partition table on /dev/sdb; that's what fdisk is designed to manipulate, and your MBR table, according to the fdisk output you posted, has two NTFS partitions (/dev/sdb1 and /dev/sdb2). The fdisk output also includes a warning that GUID Partition Table (GPT) data exist on the disk. GPT is a newer partitioning system that's used on Macs and some other systems. It's unclear from the output you posted what GPT partitions might be defined on the disk.

GPT data structures are much larger than MBR data structures. GPT also includes what's called a "protective MBR," which is an MBR that consists of a single massive partition that's designed to keep GPT-unaware utilities from messing with the disk. There's no hint of this protective MBR in your output, though, just a conventional (non-protective) MBR.

Chances are that /dev/sdb was used on a Mac, or perhaps on some other system that uses GPT, and then repartitioned with a GPT-unaware utility. This left the bulk of the GPT data intact but created an incompatible MBR. Older OSes will see the MBR and treat the disk as a normal MBR disk, but OSes with both MBR and GPT support, like Linux, might get confused by this mish-mash. Another, less likely, possibility is that the disk should be treated as a GPT disk, and the MBR got placed on the disk by accident. If you know the history of the disk, you can probably figure out which of these things happened. If you're unsure, it may take some more investigating.

Whatever the cause of the problem, one possible solution is to use my [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) which is an fdisk-like tool for GPT disks. It includes recovery options that can either wipe the errant GPT data (if the disk really should be MBR-only, with the MBR partitions that fdisk reported) or restore the GPT data, creating a fresh protective MBR. I recommend you download and install the latest version for your architecture from the [GPT fdisk Sourceforge page.](http://sourceforge.net/projects/gptfdisk/files/) (Ubuntu 10.04 includes the program in its repositories, installable by typing "sudo apt-get install gdisk"; however, that's a rather old version with some known bugs, so it's best to get the latest versions, IMO).

You can launch gdisk much as you would fdisk; you'll then see something like this:

```

$ sudo gdisk /dev/sdb
GPT fdisk (gdisk) version 0.6.10

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer:
```

You have several choices at this point:


[list=1]
[*]If you're not sure whether to use the MBR or the GPT side, select GPT (option 2 in the menu) and then type "p" at the main menu. This will show you the GPT partitions. You can compare them to the MBR partitions shown by fdisk. With any luck that will help you figure out which to use. If you want to use GPT, just go on with the next option below; if MBR, skip to option #3 in this list.
[*]If you want to use the GPT partitions, select option #2 in the gdisk list, then type "w" to save your GPT data, which will include a regenerated protective MBR.
[*]If you want to use the MBR partitions, select any option in the gdisk list, then type "x" to enter the experts' menu, then type "z" to "zap" (destroy) the GPT data. You'll be asked to confirm this decision. Answer "y"; but when the program asks if you want to blank out the MBR, *answer "n"!* If you let gdisk wipe the MBR, your MBR partition table will be destroyed!
[*]If the NTFS partitions on the disk are data partitions, not boot partitions, and if you use Windows Vista or later, you can select "1" at the gdisk prompt to use the MBR data. If you then type "w", gdisk will write the MBR partitions in GPT form, converting the disk from MBR to GPT. GPT has some minor advantages over MBR, such as storing backups of itself in two places on the disk and the elimination of primary/extended/logical partition distinctions. OTOH, Windows can't boot from GPT. (Linux can boot from GPT.) Chances are a pure MBR configuration will work fine; I only mention this possibility in case you want to experiment with it. (We'll all be using GPT before too long, since MBR tops out at 2 TiB disk size, given standard 512-byte sectors. GPT's limit is much higher than this.)
[/list]


If you need more help, just post back with additional details.

---

### Post by VMC on 2010-09-20
I was just yesterday reading your tutorial on GTP on an unrelated search. Its a great tutorial on the subject. Concern for me would be getting Windows to cooperate with GPT.

I was thinking of your article when reading the first several posts here, and then lo and behold you show up and reveal what may be the OP's problem.

---

### Post by srs5694 on 2010-09-20
> **VMC said:**
> I was just yesterday reading your tutorial on GTP on an unrelated search. Its a great tutorial on the subject. Concern for me would be getting Windows to cooperate with GPT.

The rules of how Windows and GPT interact are complex. AFAIK, the best source of information on that topic is Microsoft's [Windows and GPT FAQ.](http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx) It's dated 2006 and doesn't reference Windows 7, but AFAIK Windows 7 is exactly like Windows Vista in terms of GPT support, so it's still relevant. The most important points, however, are:


[list]
[*]All versions of Windows Vista and Windows 7 can handle GPT fine as *data* (non-boot) disks.
[*]Windows Vista and Windows 7 can boot from GPT only on EFI-based systems; on BIOS-based systems, they can't boot from GPT. Although not mentioned in Microsoft's FAQ, [hybrid MBRs](http://www.rodsbooks.com/gdisk/hybrid.html) are a way around this limitation, albeit a limited, ugly, and dangerous one.
[*]For Windows XP and earlier, the rules are more complex, and depend on the platform.
[/list]


Chances are Mooney10's disk should be pure-MBR, although as I point out in option #4 in my original post, if those are data (non-boot) NTFS partitions, converting to GPT would probably work, too.

---

### Post by srs5694 on 2010-09-20
Oh, one more point: This isn't really an Ubuntu 10.10 beta-specific issue. I've seen reports of the exact same problem cropping up in earlier versions of Ubuntu and/or other distributions and/or in GParted. (I don't recall the exact circumstances offhand, but I've definitely seem reports of this exact same problem.) The fundamental cause is that the disk partitioning is at least a little bit ambiguous. Of course, a good case could be made that the installer should be better able to detect this sort of condition and offer the user intelligent options for how to proceed, like the ones I outlined in my first post in this thread. Looked at from this perspective, the developers might want to examine the issue in more detail. Unfortunately, I don't think that libparted, upon which the Ubuntu installer relies, really offers very good diagnostic or recovery options for this sort of problem. A script that uses a variety of text-mode tools, like fdisk, sgdisk, and perhaps parted, might be able to do some useful pre-screening and recovery, though....

---

### Post by Mooney10 on 2010-09-20
**UPDATE**: So I rebuilt the partition table using TestDisk (Thanks 23dornot23d!)which I already tried before this. (but i did it again for good measure)

So when I rebooted into the live cd the installer saw *a* partition but no type or used space, so i tried to make 2 ext4 partitions, it failed. 

So I rebooted into the live cd once again, the installer found the partition and found the type and used space, so once again i tried to install , made two ext4 partition and both worked and everything installed fine :guitar:  

But.... What the funk happened?

**THANK YOU ALL**

---

### Post by srs5694 on 2010-09-20
> **Mooney10 said:**
> But.... What the funk happened?

Please see my first post in this thread [noparse](#8).[/noparse]

---

### Post by 23dornot23d on 2010-09-20
> **Mooney10 said:**
> **UPDATE**: So I rebuilt the partition table using TestDisk (Thanks 23dornot23d!)which I already tried before this. (but i did it again for good measure)

So when I rebooted into the live cd the installer saw *a* partition but no type or used space, so i tried to make 2 ext4 partitions, it failed. 

So I rebooted into the live cd once again, the installer found the partition and found the type and used space, so once again i tried to install , made two ext4 partition and both worked and everything installed fine :guitar:  

But.... What the funk happened?

**THANK YOU ALL**

Same thing here .... 
I had a similar situation with my main drive in my laptop and I had a good idea that it would work - but how well testdisk works everytime I am not sure ..... my main problems seem to be with NTFS partitions though .......
 
I did a webpage of the steps I took while recovering a disk and it got more complex than I was prepared for [LINK it managed to get it 99% sorted]("https://sites.google.com/site/problems7730zg/sda-layout-after-testdisk---30402")

Then I did the rest here .... [Link]("https://sites.google.com/site/problems7730zg/sda-layout-after-testdisk---30402/my-best-solution")

The latest was my USB Terra Hard Drive .... problems seem to always be with NTFS partitions too ...... no idea why ..... the only programs on this new computer that I used to repartition have been the Linux installers ...... so it does leave me wondering if they are
working 100% .......

Overlaps and partitions extending beyond the end of the drive should not happen and yet they have ...... This was where mine happened in the testing so it maybe was to be expected in a way best there with the best help available ...... LINK[http://ubuntuforums.org/showthread.php?p=9582637#post9582637](http://ubuntuforums.org/showthread.php?p=9582637#post9582637)

Since this report I had no problems with repartitioning ..... until the other day when I used a old Distro to set up one OS ...... and then I had big problems again ..... luckily it was my backup drive ...... so deletiing and adding new partitions sorted the problem.

I would love to know though if having all the different formats that are available now on one disk is a good idea , and as time goes on how do you avoid doing this ......

Yet another format is coming out now ...... and I was quite happy with the old formats as
nothing ever appeared to go wrong ..... 

This to me is the foundation that everything sits on ..... and if this goes wrong then everything goes wrong ...... it needs to be 100% correct everytime .....

Glad you got sorted though ..... 

I would love to go deeper into this subject, but this is not my aim when using my computer ..... others that set these systems up are the ones we rely on to do all the hard work of making sure that they (the formatting tools) work for all the different situations ......

[COLOR=Red](ext2 ext3 reiserfs jfs NTFS ext4 GPT ...... plus many more and so it continues ..... each new format getting better ..... but leaving all the legacy behind ........ to me the less formats we have in the future the better for all ...... we probably have to change at some point  .....
but if they are so much better ..... maybe the old formats need to be upgraded ..... when we are changing to later releases otherwise the legacy just keeps growing)
[/COLOR] 
Obviously this may be impractical for massive drives .... but say below 20Gig .... on older systems ...... it would possibly take an hour or so to make a new partition and move the data over - this of course would have to be given as a choice to the USER if they want to take the risk - depending on what Data they have.

---

### Post by srs5694 on 2010-09-20
> **23dornot23d said:**
> Same thing here .... 
I had a similar situation with my main drive in my laptop and I had a good idea that it would work - but how well testdisk works everytime I am not sure ..... my main problems seem to be with NTFS partitions though .......
 
I did a webpage of the steps I took while recovering a disk and it got more complex than I was prepared for [LINK it managed to get it 99% sorted]("https://sites.google.com/site/problems7730zg/sda-layout-after-testdisk---30402")

Actually, it appears from your links (which I admit to only skimming, not reading in depth) that your problem and Mooney10's problems have fundamentally different causes. They're both partitioning troubles, but beyond that they're entirely different.

> The latest was my USB Terra Hard Drive .... problems seem to always be with NTFS partitions too ...... no idea why ..... the only programs on this new computer that I used to repartition have been the Linux installers ...... so it does leave me wondering if they are
working 100% .......

I've been trying to spot a commonality in the problem reports of mis-sized partitions but I've not found one. I've also never encountered it myself, aside from deliberately re-creating of the problem by hacking at the MBR with a hex editor. Thus, I'm not sure what tool is creating it. In fact, it's entirely possible that multiple tools are to blame; there could be similar bugs in different tools.

> Overlaps and partitions extending beyond the end of the drive should not happen and yet they have ...... 

One common problem is an extended partition that ends a few sectors after the end of the hard disk. I haven't checked the numbers, but this could easily be caused by a rounding error when converting from cylinder values to sector values. Most disks end "mid-cylinder," since the cylinder values these days are entirely meaningless. Thus, if the software counts the last partial cylinder as a whole cylinder, it'll compute a sector value for the end of that cylinder that's beyond the end of the disk.

> I would love to know though if having all the different formats that are available now on one disk is a good idea , and as time goes on how do you avoid doing this ......

Yet another format is coming out now ...... and I was quite happy with the old formats as
nothing ever appeared to go wrong ..... 
[COLOR=Red]
(ext2 ext3 reiserfs jfs NTFS ext4 GPT ...... plus many more and so it continues ..... each new format getting better ..... but leaving all the legacy behind ........ to me the less formats we have in the future the better for all ...... we probably have to change at some point  .....
[/COLOR]

It's unclear to me what you mean by "format," since your list mixes two entirely different types of data structures:


[list]
[*]The Master Boot Record (MBR; which you don't mention) and the GUID Partition Table (GPT) are partitioning systems. They define where partitions begin and end on the disk, as well as some metadata (partition type code, boot flags, etc.) associated with each partition. It's impossible to mix both of them on one disk and be 100% legal; however, a technically illegal mixture known as a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) does exist. As described on the page to which I linked, hybrid MBRs are *not* a "good idea," as you say, but they are sadly necessary for certain types of multi-booting.
[*]Ext2fs, ext3fs, ext4fs, ReiserFS, JFS, and NTFS are all filesystems. These are much more complex data structures that enable named access to individual files. Filesystems are typically stored inside partitions. You can safely put as many different filesystems as you like on a single disk, so long as each resides in its own partition (or in different image files or other container data structures).
[/list]


So from the start, you need at least one from each category to use a computer. (Well, technically, you could get by without a partition table, but that would be very awkward, particularly if you want to multi-boot the system.)

On the partitioning system side, MBR was created in the 1980s, at a time when hard disks were 5 MB (*mega*bytes, not GB or TB) in size. MBR's designers didn't think anybody could possibly want more than four partitions, so that was the limit. It's been updated through the years to overcome this and several other limitations. Each time, it's gotten uglier, more ungainly, and more likely to cause compatibility problems because old and new OSes and utilities might treat it a bit differently. For these reasons, MBR has been well-hated for at least two decades. Today, though, it's coming up on a brick wall: It uses 32-bit pointers to identify sector values. Given a 512-byte sector size (the current standard in hard disks), this means that MBR cannot handle disks more than 2 TiB in size -- or at least, it can't handle partitions more than 2 TiB in size, and no partition may begin beyond the 2 TiB point on the disk, so even stretching things, it maxes out at 4 TiB. Given that RAID arrays routinely exceed this size and at least one 3 TiB disk is now available, this is a huge problem. It can be pushed back by increasing the sector size (as is done with the one 3 TiB disk I know of), but that'll only buy another 2-5 years life for MBR, at most. Note that it's not possible to just "tweak" MBR to use 64-bit pointers; there simply isn't enough unallocated space in the data structures to cram in more bits for the pointers.

GPT is designed, in part, to overcome MBR's limitations. It uses 64-bit pointers and abandons all the ugly hacks that have worked their way into MBR over the years. In theory, it should be more reliable than MBR. Thus, the transition to GPT is inevitable, unless something else comes along. (I'm not aware of any other partitioning system that could possibly compete with GPT for dominance in the next few years.)

As to filesystems, some of the differences are due to the different needs of OSes. FAT and NTFS lack features that Linux needs, and all Linux-native filesystems lack features that modern versions of Windows need. OS vendors also often have a "not-invented-here" mentality that can make it hard to standardize on just one filesystem, even when the OSes' needs are similar. Linux has accumulated an embarrassing wealth of filesystems for a variety of reasons, including filesystem donations (XFS and JFS) from other OSes and a progression of new features. For instance, ext3fs added a journal to ext2fs, which greatly speeds up system startup time after system crashes. Ext4fs extends file and filesystem size limits in ext2fs/ext3fs and improves performance. The next-generation filesystem for Linux, Btrfs, adds a number of features that are important for advanced users, and it looks like it may perform better than most of its predecessors, too. Early filesystems had filesystem size limits that have long since been exceeded, and even ext2fs and ext3fs have limits that will become issues before too long (and already are issues for some users). Thus, filesystems have proliferated.

> 
[COLOR=Red]but if they are so much better ..... maybe the old  formats need to be upgraded ..... when we are changing to later releases  otherwise the legacy just keeps growing)

[/COLOR]Obviously this may be impractical for massive drives .... but say below 20Gig .... on older systems ...... it would possibly take an hour or so to make a new partition and move the data over - this of course would have to be given as a choice to the USER if they want to take the risk - depending on what Data they have.

The absolute number of filesystems, partition table formats, drivers, etc. will almost certainly continue to increase over the years. At some point, some may be retired. A few already have been, such as Xiafs.

For the most part, the effort involved in creating conversion utilities is too great to justify; the benefits of converting a filesystem in place are usually pretty small. There are exceptions to this rule, of course. It's possible to convert ext2fs to ext3fs and to convert ext3fs to ext4fs, for instance. My GPT fdisk utility can convert MBR to GPT. As a general rule, in-place conversions like this are at least a little bit risky, so forcing users to convert so that the developers can retire an obsolete filesystem or partitioning scheme would be unwise at best. Better to just wait until the old filesystem is no longer being used and then drop support for it.

Furthermore, sometimes there are reasons to keep using an old system. Ext2fs is preferred to ext3fs on small disks, such as Linux /boot partitions, because the overhead of the ext3fs journal is too great on small disks. MBR is preferable to GPT if you're dual-booting or exchanging removable disks with an older OS that doesn't understand GPT.

---

### Post by 23dornot23d on 2010-09-21
Thanks for taking the time to go through all of that .... that makes it a lot clearer to me now .....

I have only got involved with the filesystems due to problems that I encountered .... and found that it gets really complicated ..... your explanation clears a lot of things up especially between GPT and MBR ..... 

I mistook it as another filesystem .... its a 64 bit partition table then for bigger drives in the future ....

> 
Actually, it appears from your links (which I admit to only skimming,  not reading in depth) that your problem and Mooney10's problems have  fundamentally different causes. They're both partitioning troubles, but  beyond that they're entirely different.
You are right .... but I did make sure that testdisk did handle GPT ..... that was why I posted the help page link .... its then for the person to check that this will do what they want ..... my advise was to analyse the structure first before doing anything .... and testdisk
seems a good tool for doing that ...... and also for repairing the Boot Records ...... you obviously know the full story of how all this works in depth ...... therefore I am happy to learn from you ......

______________________________________________

Also the new filesystem ..... 
I was wondering why this too was coming ..... again I guess its the future sizes of drives and speed at accessing information on them.

> 
Btrfs, adds a number of features that are important for advanced users,  and it looks like it may perform better than most of its predecessors,  too. Early filesystems had filesystem size limits that have long since  been exceeded,

 I keep reading reports on it and have no idea how it will be implimented ..... my worry was that like with Ext4 ..... the older OS's I had running could not identify the Ext4 partitions .... therefore I worried that using gparted frome these with Ext4 being present could cause problems ...... but you have cleared that up too , as it seems as long as the boundaries are in place set either by MBR or GPT then ..... it matters not what type of filesystem lies between these boundaries ....... 

I was told a load of rubbish then when I was younger ..... because ..... 

I used to mix them all the time and was told it was a bad thing to do ........... NTFS .... FAT ...... and Linux partitions .... all on the same drive ...... but I knew from trying and succeeding that they all worked ok together ..... thanks for the clarification.

I tend to be a suck it and see person ..... if I have tried something out and it is good and works then I will advise it to others .....
but I will always have tried it out on my own system first ...... never have I lost a piece of hardware through the things I have tried
and have always recovered disks from bad formats ...... but I trust in the people that write these programs ......

Would I gain anything from a change from MBR to GPT ..... my biggest hard drive is a Terrabyte ...... my guess is untill I get a bigger drive than 4 terra than its best to stay as I am .... especially if the installers are not picking it up properly yet.
but I have been having problems with the terra drive ..... mainly due to it being slow to get recognised at boot up ........ seems I have to cold boot and then do a warm reboot to get it to pick up properly once the system sees it ok then alls fine ...... but if it does not pick it up properly things go to a crawl and I get fsync problems ...... it can also cause problems when I have all 3 USB drive plugged in at the same time as the order of them can end up set up differently ....... 
( I have a routine now for plugging them in and setting the order the same each time .... but that took some figuring out what was going on ...... as with all 3 plugged in a warm boot and a cold boot would give different results  - for the order of the drives .... sda sdb sdc sdd ) 

I always set it 250 Gig internal as sda ..... 300 Gig USB as sdb ...... 500 Gig USB as sdc and the 
(Terrabyte as sdd ..... but often this is only plugged in occassionally and used for backups ......)
 
Cheers for the info ..... :)

---

### Post by srs5694 on 2010-09-21
> **23dornot23d said:**
> I keep reading reports on it and have no idea how it will be implimented ..... my worry was that like with Ext4 ..... the older OS's I had running could not identify the Ext4 partitions .... therefore I worried that using gparted frome these with Ext4 being present could cause problems ...... but you have cleared that up too , as it seems as long as the boundaries are in place set either by MBR or GPT then ..... it matters not what type of filesystem lies between these boundaries ....... 

Correct, but there is a caveat: There are always buggy programs (even including OSes) that go blundering in where they shouldn't. If a utility or OS doesn't understand Filesystem X but decides to go ahead and write to the partition on which it's stored, there will be problems. This sort of issue is quite rare today, but if you were to try out (say) every partitioning tool in existence, along with a dozen exotic filesystems, one of the partitioners is bound to have a bug that will cause problems.

> Would I gain anything from a change from MBR to GPT ..... my biggest hard drive is a Terrabyte ...... my guess is untill I get a bigger drive than 4 terra than its best to stay as I am .... especially if the installers are not picking it up properly yet.

GPT has advantages on smaller drives, but they're fairly modest: GPT includes a backup of all its data structures, which protects it against accidental erasure; data structures are given CRC codes, which helps the OS or disk utility detect corruption; partitions have names that can help you tell what specific partitions are for; there's no distinction between primary, extended, and logical partitions, which simplifies partition layout; cylinder/head/sector (CHS) addressing is completely eliminated, except for the protective MBR partition; and boot loaders (particularly GRUB 2) don't rely on code being stored in unallocated space, which is a dangerous but common practice in MBR boot loaders. IMHO, these advantages are great enough, considered together, to recommend GPT for Linux-only installations or for data-only (non-boot) disks when all the OSes are capable of reading GPT. That said, there are problems with GPT, mostly because of utilities that are still a little rough around the edges with GPT. The worst (and thankfully rare) of these problems are [some buggy BIOSes](http://www.rodsbooks.com/gdisk/bios.html) that give booting headaches.

Of course, all this is aside from the big issue, which is the 2 TiB limit of MBR. Note that although it's possible to create an MBR partition layout that reaches just shy of 4 TiB, that's stretching things and imposes unusual restraints on partition sizes and locations; 2 TiB is the practical limit, at least with 512-byte sectors.

> but I have been having problems with the terra drive ..... mainly due to it being slow to get recognised at boot up ........ seems I have to cold boot and then do a warm reboot to get it to pick up properly once the system sees it ok then alls fine ......

It sounds like your drive is slow to get warmed up. You might check your BIOS settings to see if there's an option to delay the boot process a bit longer for drive startup. If not, it's conceivable that disabling the "fast boot" option in the BIOS would help. That option normally disables a lengthy RAM check. If the BIOS activates the hard disk before the RAM check, then this would give it time to spin up. I'm not positive this would work, though.

If the problem is in the Linux drivers, perhaps there's a driver option that would cause the driver to wait longer for new drives to spin up. I haven't looked into this, though.

> but if it does not pick it up properly things go to a crawl and I get fsync problems ...... it can also cause problems when I have all 3 USB drive plugged in at the same time as the order of them can end up set up differently .......

This shouldn't be a problem if you use UUIDs or labels to identify drives in /etc/fstab, as in:

```

UUID=3631a288-673e-40f5-9e96-6539fec468e9  /home  reiserfs  defaults  0 0

```

If that filesystem is on /dev/sdb one time and /dev/sdc another, it won't matter. It's also possible to use UUIDs in GRUB, if the naming issues cause boot problems.

---

### Post by 23dornot23d on 2010-09-21
A quick update and thanks again for the in depth reply .....

_______________________________________________________________

Just to clarify the last statement and situation .... the uuids are not a problem its something to do with it recognozing one
USB Drive ... 
( You do not need to reply to this but I thought I would clarify what the situation is 
as it boots ok with the other two smaller USB drives ...... and it may just be a drive compatibility problem or the BIOS or the slow boot time )

From a cold boot even with the memory test enabled and also as the CD as first drive to slow the boot even more ... 
I try to give it as much time as possible now to pick up the SLOW USB drive .... and it still has a problem.

**On the very first boot** with the Terra USB drive plugged in - it will leave a flashing cursor top left on a black screen and sits there flashing forever ..... 

It could be a BIOS issue ..... but is there a way of testing for it ? 
( I doubt it very much - and even if there is its not that big a problem as the other USB drives are fine )
It does not seem to recognise the drive other than giving it power and spinning it up ......

BUT ......

If I plug the Terra USB drive in at the point the internal drive menu pops up ......[B]
sda (internal drive) BOOT MENU pops up[/B] from a complete cold start ........ it seems then to be able to recognise the drive properly .... this is an IOMEGA TERRA DRIVE
( I do not know of any issues with it ....... but maybe others have similar problems.
if so feel free to comment here if you happen to read this ) 

Then I press CTRL + ALT + DEL ..... doing a warm re-boot it will then correctly boot to the Terra Drive ....
**sdb (external Terra USB) BOOT MENU**

Then the computer runs fine for the continuing session allowing as many warm boots as I want and runs perfectly well.


But ..... if I switch it off and come back to it ..... then I have  to do this same procedure above again to get it to work properly.

Its a small inconvenience .... but not a major problem .... and

I have a work around now so its not really too much of an issue ..... but it would be interesting to know for sure what is happening ..... but we have now digressed from the original problem and I am sure that your time is valuable ..... so this is just for information really ...... it may be useful to someone at sometime ..... but probably not the OP ......

But I am glad that he got his problem sorted and I hope that it is still running ok .....
Ok all for now and thank you very much for all the useful information. :)

---

