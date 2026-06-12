---
title: "Faster boot times - testing needed"
date: 2011-02-12
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by psusi on 2011-02-12
I have made some changes to ureadahead to try and improve it.  If I could get enough people to test and report that it helps, the changes can be merged into Ubuntu.  Please help test if you can.

You can add my PPA and upgrade ureadahead with:

```
sudo apt-add-repository ppa:psusi/ppa
sudo apt-get update
sudo apt-get upgrade ureadahead
```

You can find the source code in bzr at code.launchpad.net/~psusi/ubuntu/natty/ureadahead/mine.

Make sure you also have bootchart installed and auto login enabled and compare the boot time with the stock package vs my version.  Remember that after installing bootchart or upgrading ureadahead, the next boot will be a profile boot, so leave it alone for a minute after it gets to the desktop, then reboot to see the performance of an accelerated run.

You can find the bootchart logs in /var/log/bootchart.

---

### Post by ebasa on 2011-02-12
Failed to fetch [http://ppa.launchpad.net/psusi/ppa./ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/psusi/ppa./ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

---

### Post by MacUntu on 2011-02-12
No change here... 

[[img]http://img.xrmb2.net/images/t506089.jpeg[/img]](http://img.xrmb2.net/images/506089.png)

Almost 16 seconds ureadahead with a 7200rpm HDD is not good. ;)

But maybe it's time for a reinstall... last time I played around with filefrag and the files in the pack file, I got this distribution of files on my partition (35% full, 49 blocks per pixel, allocation green -> red, and no, I lost the code for that thing):

[[img]http://img.xrmb2.net/315258.jpg[/img]](http://img.xrmb2.net/images/315258.png)

---

### Post by psusi on 2011-02-12
> **ebasa said:**
> Failed to fetch [http://ppa.launchpad.net/psusi/ppa./ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/psusi/ppa./ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found

Need to be running Maverick or Natty.

---

### Post by psusi on 2011-02-12
> **MacUntu said:**
> 
But maybe it's time for a reinstall... last time I played around with filefrag and the files in the pack file, I got this distribution of files on my partition (35% full, 49 blocks per pixel, allocation green -> red, and no, I lost the code for that thing):

If you are feeling adventurous, I also just uploaded a new defrag release to my PPA with a python script to generate an inode priority list from the ureadahead list.  This will result in all directories and files that ureadahead accesses being packed at the start of the disk in order.

IF YOU TRY THIS, HAVE A BACKUP.  It works well for me, but if something goes wrong it will almost certainly destroy your entire fs.

First run the dump2inodes.py script.  Redirect its output to a file somewhere, like:

```
sudo dump2inodes.py > inodes.priority
```

You will need to boot into another install or a livecd or something to defrag.  From there, mount the disk and copy the inodes.priority file out.  You also want to delete the ureadahead pack files to force a reprofile on the next boot.  If your hd is mounted in /mnt, then:

```
sudo rm -fr /mnt/var/lib/ureadahead/{pack,*.pack}
```

After that, unmount the drive, then defrag it:

```
sudo e2defrag -r -i inodes.priority /dev/sda1
```

Substitute /dev/sda1 for whatever is correct on your system.  You also might want to give it more ram to play with to speed it up.  It uses 8192 buffers by default which is 32mb, so if you have plenty of ram, you might want to add -p 32768 or 65536.

The -r is for read only mode.  Run it like that once just to make sure it doesn't puke, then drop the -r.  After it finishes, run a fsck to make sure it didn't screw things up:

```
sudo e2fsck -f /dev/sda1
```

Reboot, wait for the ureadahead profile to finish, then reboot again and enjoy the results.

---

### Post by jocko on 2011-02-13
> **psusi said:**
> I have made some changes to ureadahead to try and improve it.  If I could get enough people to test and report that it helps, the changes can be merged into Ubuntu.  Please help test if you can.

You can add my PPA and upgrade ureadahead with:

```
[COLOR=Red]sudo apt-add-repository ppa:psusi/ppa.[/COLOR]
sudo apt-get update
sudo apt-get upgrade ureadahead
```You can find the source code in bzr at code.launchpad.net/~psusi/ubuntu/natty/ureadahead/mine.

Make sure you also have bootchart installed and auto login enabled and compare the boot time with the stock package vs my version.  Remember that after installing bootchart or upgrading ureadahead, the next boot will be a profile boot, so leave it alone for a minute after it gets to the desktop, then reboot to see the performance of an accelerated run.

You can find the bootchart logs in /var/log/bootchart.

> **psusi said:**
> Need to be running Maverick or Natty.
I get the same error with maverick. You have a typo in the command, remove the dot at the end to make it:
```
sudo apt-add-repository ppa:psusi/ppa
```

---

### Post by plun on 2011-02-13
Well, I cannot see any Natty packages within this ppa

[https://launchpad.net/~psusi/+archive/ppa](https://launchpad.net/~psusi/+archive/ppa)

Changed to maverick repo and upgraded with no change in upstart time.

Pack-files removed and rebooted twice.

**For the moment I also have a Plymouth crash which takes som time.**

I am always around 10 seconds, Intel SSD.

[[IMG]http://i.imgur.com/yjq67s.jpg[/IMG]](http://imgur.com/yjq67)

More facts about ureahead:
[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

The defrag thing.....hmmm...:D

---

### Post by MacUntu on 2011-02-13
> **psusi said:**
> If you are feeling adventurous

Will try it on a cloned disk later today. According to ureadahead --dump, it's currently reading 160MB - that's 10MB/sec. :D 

It would be great to have all that data in one big boot file at the start of the partition/disk. Then it wouldn't take longer than 3 seconds even on slow notebook HDDs. :D

> **plun said:**
> Intel SSD.

Trying this on SSDs is more for regression testing - look at you boot chart, there's nothing to optimize.

> **plun said:**
> The defrag thing.....hmmm...:D
Not necessary on a SSD.

---

### Post by MacUntu on 2011-02-13
No luck. I ran

* e2fsck -> no errors
* e2defrag -r -> no errors
* e2defrag -> no errors (and a DEFRAG.EXE flashback :D)
* e2fsck -> ~50 errors, system unable to boot

---

### Post by psusi on 2011-02-13
> **jocko said:**
> I get the same error with maverick. You have a typo in the command, remove the dot at the end to make it:
```
sudo apt-add-repository ppa:psusi/ppa
```

Right.  The period was originally to end the sentence and then I decided to put it in code tags and forgot to remove it.  Fixed.

> **plun said:**
> 
I am always around 10 seconds, Intel SSD.


Ahh, yes... shouldn't really make a difference for an SSD, but it is good to know it doesn't slow things down.

---

### Post by psusi on 2011-02-13
> **MacUntu said:**
> No luck. I ran

* e2fsck -> no errors
* e2defrag -r -> no errors
* e2defrag -> no errors (and a DEFRAG.EXE flashback :D)
* e2fsck -> ~50 errors, system unable to boot

Crap... can you post the errors?

---

### Post by MacUntu on 2011-02-13
No, sorry, I already formatted the cloned drive. However, I can "re-clone" my partition and try again later if you want that information. Before I tried the defragging, your ureadahead reduced the time spent in ureadahead by 1.5 seconds to 16.5 seconds (had to put the cloned partition at the end of the disk, so it all was a bit slower).

Currently I'm repeating the process in a fresh daily Natty VM.

---

### Post by psusi on 2011-02-13
> **MacUntu said:**
> No, sorry, I already formatted the cloned drive. However, I can "re-clone" my partition and try again later if you want that information. Before I tried the defragging, your ureadahead reduced the time spent in ureadahead by 1.5 seconds to 16.5 seconds (had to put the cloned partition at the end of the disk, so it all was a bit slower).

Currently I'm repeating the process in a fresh daily Natty VM.

Good to know that ureadahead was faster, but yea, I'd also like to figure out what went wrong with defrag and fix it.

---

### Post by MacUntu on 2011-02-13
Just wondering, the inode list started with "=2" - is that by design (I guess so, else e2defrag probably would have complained)?

---

### Post by psusi on 2011-02-13
> **MacUntu said:**
> Just wondering, the inode list started with "=2" - is that by design (I guess so, else e2defrag probably would have complained)?

Yes, lines that start with an = set a priority level for the subsequent inodes.  The script gives directories priority of 2 and regular files 1 so the directories go first ( because ureadahead reads them first in order to find the files ).

---

### Post by MacUntu on 2011-02-13
Ah, I see. The defrag went fine in a VM - going from 6 down to 2 seconds for ureadahead (I restarted the VM before bootcharting to avoid caching). That VM now boots 10 seconds faster than its host. :D

---

### Post by donniezazen on 2011-02-13
My boot time is over a minute.

[http://img808.imageshack.us/i/mavericklaptopmaverick2.png/](http://img808.imageshack.us/i/mavericklaptopmaverick2.png/)

---

### Post by MacUntu on 2011-02-13
So, I retried with my current system cloned to another disk:

fsck before defragging is good:

```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sde1: 393047/2531328 files (0.7% non-contiguous), 3605064/10096896 blocks
```

Defragging finishes with

```
Relocation statistics
3464181 buffer reads in 1157 group of which 72205 read-aheads.
3435807 buffer writes in 1551 group 247175 migrations, 28374 forces.
```

Final fsck fails:

```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
Backing up journal inode block information.
Pass 1: Checking inodes, blocks, and sizes
Inode 7837, i_blocks is 1296, should be 8.  Fix<y>? yes
Inode 7855, i_blocks is 136, should be 8.  Fix<y>? yes
Inode 8026 has a bad extended attribute block 12.  Clear<y>? yes
Error while reading over extent tree in inode 8026: Corrupt extent header
Clear inode<y>? yes
Inode 8026, i_size is 4080850291470488, should be 0.  Fix<y>? yes
Inode 8026, i_blocks is 160, should be 0.  Fix<y>? yes
Inode 8080, i_blocks is 4000, should be 144.  Fix<y>? yes
Pass 2: Checking directory structure
Entry 'document.py' in /usr/share/pyshared/uniconvertor/app/Graphics (20445) has deleted/unused inode 8026.  Clear<y>? yes
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -(294796--294911) -(327596--327679) -(360378--360447) -(393208--393215) -(425828--425983) -(491406--491453) -819199 -851967 -884735 -(917499--917503) -(950147--950158) -(1343479--1343487) -1376255 -1409023 -(1507325--1507327) -(1540094--1540095) -(1703903--1703935) -1736703 -1769471 -1835007 -(1867774--1867775) -(2162602--2162687) -(2227254--2227290)
Fix<y>? yes
Free blocks count wrong for group #8 (0, counted=116).
Fix<y>? yes
Free blocks count wrong for group #9 (0, counted=84).
Fix<y>? yes
Free blocks count wrong for group #10 (0, counted=70).
Fix<y>? yes
Free blocks count wrong for group #11 (0, counted=8).
Fix<y>? yes
Free blocks count wrong for group #12 (0, counted=156).
Fix<y>? yes
Free blocks count wrong for group #14 (0, counted=48).
Fix<y>? yes
Free blocks count wrong for group #24 (0, counted=1).
Fix<y>? yes
Free blocks count wrong for group #25 (0, counted=1).
Fix<y>? yes
Free blocks count wrong for group #26 (0, counted=1).
Fix<y>? yes
Free blocks count wrong for group #27 (0, counted=5).
Fix<y>? yes
Free blocks count wrong for group #28 (0, counted=12).
Fix<y>? yes
Free blocks count wrong for group #40 (0, counted=9).
Fix<y>? yes
Free blocks count wrong for group #41 (0, counted=1).
Fix<y>? yes
Free blocks count wrong for group #42 (0, counted=1).
Fix<y>? yes
Free blocks count wrong for group #45 (0, counted=3).
Fix<y>? yes
Free blocks count wrong for group #46 (0, counted=2).
Fix<y>? yes
Free blocks count wrong for group #51 (0, counted=33).
Fix<y>? yes
Free blocks count wrong for group #52 (0, counted=1).
Fix<y>? yes
Free blocks count wrong for group #53 (0, counted=1).
Fix<y>? yes
Free blocks count wrong for group #55 (0, counted=1).
Fix<y>? yes
Free blocks count wrong for group #56 (0, counted=2).
Fix<y>? yes
Free blocks count wrong for group #65 (0, counted=86).
Fix<y>? yes
Free blocks count wrong for group #67 (0, counted=37).
Fix<y>? yes
Free blocks count wrong (6492168, counted=6492847).
Fix<y>? yes
Inode bitmap differences:  -8026
Fix<y>? yes
Free inodes count wrong for group #0 (36, counted=37).
Fix<y>? yes
Free inodes count wrong (2138281, counted=2138282).
Fix<y>? yes

/dev/sde1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sde1: 393046/2531328 files (0.0% non-contiguous), 3604049/10096896 blocks

```

While defragging I noted the special blocks "GB" (group desc., bad block) two times, but I'm sure that's not a bad block on-disk as it also showed up in the VM on a different disk. Could this be a problem (on the other hand, the VM defragging didn't cause any fsck hic-ups)?

---

### Post by psusi on 2011-02-13
> **soham_1207 said:**
> My boot time is over a minute.

[http://img808.imageshack.us/i/mavericklaptopmaverick2.png/](http://img808.imageshack.us/i/mavericklaptopmaverick2.png/)

That is really slow.  Also the idea is to compare the times with both versions of ureadahead; which one was that?  Are you running on btrfs?  That would explain why it is so slow, and also it looks like ureadahead is failing to run.  It is optimized to run on ext[234], but should still work on btrfs.

> **MacUntu said:**
> 
Final fsck fails:


Hrm.  Can you send me an image of this fs ( before defrag ) so I can debug what is going wrong?  This will only pack the fs metadata, not the actual contents of the files:

```
e2image -r /dev/sda1 - | bzip2 > sda1.bz2
```

Please email that to me at [email]psusi@cfl.rr.com[/email].

> **MacUntu said:**
> While defragging I noted the special blocks "GB" (group desc., bad block) two times, but I'm sure that's not a bad block on-disk as it also showed up in the VM on a different disk. Could this be a problem (on the other hand, the VM defragging didn't cause any fsck hic-ups)?

The resize inode can not be moved so it shows up as bad blocks.

---

### Post by donniezazen on 2011-02-13
> **psusi said:**
> That is really slow.  Also the idea is to compare the times with both versions of ureadahead; which one was that?  Are you running on btrfs?  That would explain why it is so slow, and also it looks like ureadahead is failing to run.  It is optimized to run on ext[234], but should still work on btrfs.

This is after i have upgraded ureadahead. My root partition is ext4 but my home partition is btrfs.

---

### Post by psusi on 2011-02-13
> **soham_1207 said:**
> This is after i have upgraded ureadahead. My root partition is ext4 but my home partition is btrfs.

Can you delete the pack files and try again?

```
sudo rm -fr /var/lib/ureadahead/{pack,*.pack}
```

---

### Post by Starks on 2011-02-13
The adventurous procedure works and leaves my system bootable, but I can't even get ureadahead to profile or bootchart to generate.

---

### Post by amano on 2011-02-13
> **soham_1207 said:**
> This is after i have upgraded ureadahead. My root partition is ext4 but my home partition is btrfs.

But what was your boot time before upgrading ureadahead? Then we could judge if and how much it regressed.

---

### Post by MacUntu on 2011-02-14
Hm, isn't soham's machine running a filesystem check in that chart?

> **psusi said:**
> Can you send me an image of this fs 
Will do, but could take one or two days.

---

### Post by psusi on 2011-02-14
> **Starks said:**
> The adventurous procedure works and leaves my system bootable, but I can't even get ureadahead to profile or bootchart to generate.

What about the non adventurous one?  Did you have bootchart working before the defrag?

Also don't forget that it takes a minute or two for the new bootchart image to show up.

---

### Post by Starks on 2011-02-14
No, I didn't.

Bootchart is quirky.

---

### Post by MacUntu on 2011-02-14
> Can you send me an image of this fs
Well, if only I could recreate the situation. I actually had to use the system before cloning it again and now I cannot get it to screw up. On the bright side, ureadahead now takes 2.5 instead of 18 seconds. ):P

My résumé for now: your ureadahead never performed worse (two times a slight improvement, one time no change and another "no change" with my SSD). The defrag method might kill your system, but if it doesn't the boot speed should be about the same as with a SSD.

---

### Post by donniezazen on 2011-02-15
> **psusi said:**
> Can you delete the pack files and try again?

```
sudo rm -fr /var/lib/ureadahead/{pack,*.pack}
```

This has reduced my boot time by 10 seconds which still is about 1 minutes.

Thanks.

[IMG]http://img15.imageshack.us/i/mavericklaptopmaverick2.png/[/IMG]

[http://img15.imageshack.us/i/mavericklaptopmaverick2.png/](http://img15.imageshack.us/i/mavericklaptopmaverick2.png/)

---

### Post by psusi on 2011-02-15
Cool, anyone else able to test?

---

### Post by donniezazen on 2011-02-17
> **psusi said:**
> Cool, anyone else able to test?

Why do i have boot time of over a minute? I see boot time is generally 10-20 seconds.

---

### Post by cariboo on 2011-02-17
I think your boot times are slow because of low hdd i/o, if you look at your bootchart, you'll see that disk i/o is 39MB/s where as mine is 94MB/s

[[IMG]http://i.imgur.com/eNVvrl.jpg[/IMG]](http://imgur.com/eNVvr)

---

### Post by psusi on 2011-02-27
Bump.

---

### Post by donniezazen on 2011-02-27
> **cariboo907 said:**
> I think your boot times are slow because of low hdd i/o, if you look at your bootchart, you'll see that disk i/o is 39MB/s where as mine is 94MB/s


And it is limited by hardware, so, no go from here. Thanks.

---

### Post by psusi on 2011-03-05
Bump.

---

### Post by psusi on 2011-03-10
Bump.

---

### Post by Starks on 2011-03-11
has you code been merged into the ureadahead bzr trunk?

---

### Post by psusi on 2011-03-11
> **Starks said:**
> has you code been merged into the ureadahead bzr trunk?

No, it needs testing with positive results to be merged.  Until then it is in my personal bzr branch and ppa on lp.

---

### Post by andyrogers2008 on 2011-03-19
Hi

I have just come across this, and must say iam impressed.

My boot times went from 45 Secs to 30 Secs for a bootup

a major improvement for me thanks

Now, only if this was in the main release of Natty.

---

### Post by VinDSL on 2011-03-20
Here's a weird one for you...

I ran across this thread, a few minutes ago, and realized I never installed Bootchart in Natty.

I love Bootchart.  I always run it on my Ubu boxes.

Anyway, I installed Bootchart and did a reboot.


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-20-mar-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-20-mar-2011.png")[/INDENT]


First thing...

I wish I could get ureadahead numbers like this ( <=1 sec ) EVERY time I boot!  LoL!

Secondly...

This uber-low ureadahead number obviously didn't make a lot of difference in overall boot time.

I realize Bootchart gives some strange results, especially the first few times you run it, but still...  Hope is not a strategy.

I'll give your PPA a shot tomorrow afternoon, and see how it does...  :D

---

### Post by MacUntu on 2011-03-20
Ureadahead hasn't been doing anything according to this chart (maybe because fsck has been running). Normally you would see almost no I/O activity after ureadahead has finished.

1. Add 'bootchart=disable' to the kernel line defaults in /etc/default/grub (you will then only get a chart when manually removing that option).
2. Run update-grub to update GRUB's configuration file.
3. Delete the .pack files in /var/lib/ureadahead/.
4. Reboot (with auto-login enabled) and don't do anything for a minute.
5. Make sure you have new .pack files in /var/lib/ureadahead.
6. Reboot and manually delete 'bootchart=disable' from the kernel line in GRUB.
7. Wait a bit, then check your chart.

---

### Post by psusi on 2011-03-22
Yea, that's a graph of a non functioning ureadahead.

---

### Post by VinDSL on 2011-03-22
> **MacUntu said:**
> Ureadahead hasn't been doing anything according to this chart (maybe because fsck has been running). 

Normally you would see almost no I/O activity after ureadahead has finished.[...]

> **psusi said:**
> Yea, that's a graph of a non functioning ureadahead.
Oh, ureadahead is working.  It just isn't reflected it that bootchart.

Bootchart is a great analyzer, but it isn't perfect.  ;)

Here's the current snapshot (from this session).  It's more typical...


[INDENT][IMG]http://vindsl.com/images/Zuul-natty-20110322-4.png[/IMG][/INDENT]

---

### Post by psusi on 2011-03-22
That looks better.  Is that the standard ureadahead?  How about the one from my ppa?

---

### Post by Iehova on 2011-03-22
Hi psusi,

The standard Natty version of ureadahead is now at a later version than that in your ppa, and synaptic doesn't give an option to force the version to yours. :S

---

### Post by MacUntu on 2011-03-22
You can always install different versions using ```
sudo apt-get install package=version
```E.g.:```
sudo apt-get install ureadahead=0.100.0-9ubuntu2
``` (maybe need '--reinstall', not sure).

---

### Post by VinDSL on 2011-03-23
> **psusi said:**
> That looks better.  Is that the standard ureadahead?  How about the one from my ppa?
That's the standard ureadahead.

Heh!  I suppose, in a way, that boot chart is a testament to Natty.

21 second boot times, with an 8 year-old, single-core, NetBurst-based, Intel P4 processor and 1 GB RAM ain't too shabby!

Just saying...

But, I still want to try the one from your PPA.  ;)

It seems like every time I start to install it, some pressing event crops up.

I'll try to set some time aside, this weekend.

---

### Post by Iehova on 2011-03-23
It seems that psusi's Natty repository doesn't include ureadahead, see here: [https://launchpad.net/~psusi/+archive/ppa?field.series_filter=natty](https://launchpad.net/~psusi/+archive/ppa?field.series_filter=natty) . That is why I have been unable to install it.

---

### Post by Iehova on 2011-03-23
Well, I have installed psusi's ureadahead twice now with different results. As my home partition is encrypted, I can't enable automatic login. Therefore, the first time I installed the new ureadahead, I left the machine sitting at the login screen. The result of this (newureadahead1.png) was a dramatically faster boot to login, but logging in took considerably longer (I assume because it wasn't profiled?)

I re-installed ureadahead (suppose i could have just re-profiled) and this time logged in straight away. Now, of course, boot to login is a few seconds longer (about 25 seconds compared to 21) but logging in is considerably quicker (about 10-13 seconds compared to 17-20).

Either way, as you can see from the attached bootcharts, psusi's ureadahead is a huge improvement on the stock ureadahead, and although the latest bootchart appears to show my overall boot as marginally longer, from my perspective it's much much quicker than before.

Thanks a lot!

EDIT: Gaah, of course ubuntuforums messed up the images...

OK, here we go: [http://img155.imageshack.us/i/oldureadahead.png/](http://img155.imageshack.us/i/oldureadahead.png/)
[http://img812.imageshack.us/i/newureadahead1.png/](http://img812.imageshack.us/i/newureadahead1.png/)
[http://img34.imageshack.us/i/newureadahead2.png/](http://img34.imageshack.us/i/newureadahead2.png/)

---

### Post by Starks on 2011-03-23
> **Iehova said:**
> It seems that psusi's Natty repository doesn't include ureadahead, see here: [https://launchpad.net/~psusi/+archive/ppa?field.series_filter=natty](https://launchpad.net/~psusi/+archive/ppa?field.series_filter=natty) . That is why I have been unable to install it.

You are supposed to change the value to Maverick in Software Sources.

---

### Post by Starks on 2011-03-23
ureadahead refuses to reprofile. it'll only process triggers.

/var/lib/ureadahead has no pack files.

---

### Post by psusi on 2011-03-23
> **Starks said:**
> ureadahead refuses to reprofile. it'll only process triggers.

/var/lib/ureadahead has no pack files.

Are you using a fs other than ext3/4?

---

### Post by Starks on 2011-03-23
I'm using ext4 for / and /home

---

### Post by psusi on 2011-03-24
This is with the one in my PPA right?  Can you try downgrading to the stock one and see if that works?  If it does, upgrade again, and if it still doesn't want to reprofile, try running it manually and see if it throws up any errors:

sudo ureadahead --force-trace

Then launch a program or something to give it something to trace.

---

### Post by Iehova on 2011-03-25
OK, I have had an interesting development. I had updated my computer but forgotten to lock the ureadahead version to psusi's, as a result it upgraded the package and I lost my nice speedy boot. I re-installed psusi's ureadahead but this time after every boot I would get a message that it (and often policykit, but that may be unrelated) had crashed, and it was no longer speeding my boot.

I then fully updated my computer (ca. 20 mins ago) and re-reinstalled psusi's ureadahead, and this time it didn't crash. However if you look at the bootchart [http://img826.imageshack.us/f/lucymk4natty2011032512.png/](http://img826.imageshack.us/f/lucymk4natty2011032512.png/) it is most certainly NOT quicker (;)) and doesn't seem to successfully profile at all as there is no file /var/lib/ureadahead/pack.

I assume that this must be caused by one of the updates?

EDIT:Ah, looks like the same problem Starks is having...

EDIT 2: OK, standard ureadahead profiles fine. Now I suppose I can check what happens if I copy its pack files to the new ureadahead...

EDIT 3: OK, trying to use old ureadahead's pack files doesn't work: [http://img218.imageshack.us/f/lucymk4natty2011032515.png/](http://img218.imageshack.us/f/lucymk4natty2011032515.png/)

It's a great shame that something has broken your ureadahead, psusi, because it was brilliant when it worked!

---

### Post by VinDSL on 2011-03-26
Whoops!

Procrastination pays off again!?!?!?!

---

