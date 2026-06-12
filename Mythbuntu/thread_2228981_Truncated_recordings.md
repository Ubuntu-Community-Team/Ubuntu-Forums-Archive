---
title: "Truncated recordings"
date: 2014-06-10
forum: Mythbuntu
---

### Post by mr.raider2 on 2014-06-10
I am having an issue with recordings being truncated after 15 or 20 minutes. The log file says something about the disk not being fast enough. 



Maximum buffer size exceeded.#012#011#011#011file will be truncated, no  further writing will be done.#012#011#011#011This generally indicates  your disk performance #012#011#011#011is insufficient to deal with the  number of on-going #012#011#011#011recordings, or you have a disk  failure.



My hardware as follows;

AMD fx-8350
AMD radeon 7870 GPU
HD homerun HDHR3-US (CAN) for ATSC TV
OS: Kubuntu 14.04 LTS
Myth TV (whatever is in the repos, O.27?)
Main drive OCZ Agility 3 SSD (OS only), Single btrfs partition
Drive for recordings: WD green mounted at /mnt/hdd, partition formatted in btrfs

I thought maybe the issue was the 5400rpm drive, so I tried using teh SSD as the target folder for recordings and I had no issues with truncation.

But if I dual boot to Windows 8.1, and use next-pvr with a a target NTFS partitition on the same WD drive, I get no issues.

Then it occurs to me that btrfs to slow? Or is Myth TV's HDhomerun support more buggy? Should reformat the target drive to ext4?

---

### Post by blm-ubunet on 2014-06-11
What have you done with "mr.raider(1)" ?.

FWIW Ext3 or ext4 is still one of the better filesystems for rotating/magnetic HDD.
For SDD you can tweak nobarriers/noatime etc.

There is nothing wrong with the WD green HDDs (for multiple recordings).
Drive partition alignment ? (only causes <25% perf hit).

But the fact that writing to SDD stops the problem suggests you are on the right cause.

You can have a SDD partition folder as storage group & manually or cron job copy files over to HDD; mythtv does not care which folder recs are in.
(**Never** use a root folder as storage group entry)
 
Do you have mythcommflag running on in-progress recordings?

The mythtv versions from 0.25 to 0.27.0 have terrible mysql overhead & other file writing problems.
Is your database on the same spindle as recordings ?

The recent 0.27.1 from mythbuntu repos (can be installed on ubuntu) should fix a lot of performance problems.

You can check your version from:
- FE information menu
- mythweb summary
- synaptic
- dpkg

ls -al /usr/lib/libmyth*

---

### Post by mr.raider2 on 2014-06-12
> What have you done with "mr.raider(1)" ?

He got killed in the whole Ubuntu SSO login fiasco. Now the original mr raider is gone, as is my Ubuntu cloud storage. I've been a member since Hardy Heron.

> FWIW Ext3 or ext4 is still one of the better filesystems for rotating/magnetic HDD.
For SDD you can tweak nobarriers/noatime etc.

thanks. I used btrfs for the SSD since it resolves the old issue of how much space to allocate between / and /home. I like teh whole subvolume concept. Since my SSD is only 240gb, I created a second partition on the HDD which has 500gb of empty space. I chose btrfs for consistency initially, but have since wiped teh partition and reformatted to ext4. We will see how it goes.

> There is nothing wrong with the WD green HDDs (for multiple recordings).
Drive partition alignment ? (only causes <25% perf hit).


Alignment is not an issue on rotational drives from what I was told.

> But the fact that writing to SDD stops the problem suggests you are on the right cause.

You can have a SDD partition folder as storage group & manually or cron job copy files over to HDD; mythtv does not care which folder recs are in.
(**Never** use a root folder as storage group entry)
 

I created a folder on the hdd partition called recodings (/mnt/hdd/recordings). I set the permissions to mythtv owner and group, and readable by everybody so I can directly inspect the contents via ssh after recordings.


> 

Do you have mythcommflag running on in-progress recordings?




From inspection of teh log, I do. Since I do not use mythtv for playback, commercial flagging seems useless for me. How do I disable this?

> The mythtv versions from 0.25 to 0.27.0 have terrible mysql overhead & other file writing problems.
Is your database on the same spindle as recordings ?

The recent 0.27.1 from mythbuntu repos (can be installed on ubuntu) should fix a lot of performance problems.


Mythbuntu Control Centre does not behave on KDE, so I just pulled in the mythtv packages directly via synaptic. Can you link the repo/ppa for mythtv updates? My guess is that the database is still on the SSD, since I added teh HDD partitions afterwards and then added the new partition to the default, live tv and stream storage groups. I could have also just symlinked /var/lib/mythtv I guess.

> 
You can check your version from:
- FE information menu
- mythweb summary
- synaptic
- dpkg

ls -al /usr/lib/libmyth*


Thanks.

---

### Post by howefield on 2014-06-12
> **mr.raider2 said:**
> He got killed in the whole Ubuntu SSO login fiasco. Now the original mr raider is gone, as is my Ubuntu cloud storage. I've been a member since Hardy Heron.

We can get you back to your original account should you wish. Post in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123") or PM me if you want help in doing that.

---

### Post by blm-ubunet on 2014-06-12
@mr-raider

same here (SSO login fiasco)

One of the mythtv devs prefers zfs filesystem for recordings.

I tested the real throughput between & on each of 2 2TB green drives (old core2duo mobo).
- one HDD was not partition aligned.
- copying 500GB (lots of 2-5GB files) there was a ~20% difference.
- the sustained I/O was ~90MB/sec
- the idle park times had been changed to ~30 sec
- ext3 & ext4 (aligned)

I think 27.1 is a good choice.
[https://launchpad.net/~mythbuntu/+archive/0.27?field.series_filter=trusty](https://launchpad.net/~mythbuntu/+archive/0.27?field.series_filter=trusty)

Have to be careful of ubuntu versioning of packages..
They call version 99+fixes as 100.
But I think 0.27.1 is really 0.27.1.

IIRC mythcommflag can be disabled in mythtv-setup (disruptive) or via mythweb.
The MBE may need to be restarted before those settings kick in.

Remember to always run mythtv-setup **first** after any upgrades.

Each to their own..but I find mythtv player to be the best.
With a media keyboard there is nothing that come close to seek performance & easy interface.

---

### Post by mr.raider2 on 2014-06-13
I'm using 

mythtv/trusty,now 2:0.27.1+fixes.20140612.050bf9d-0ubuntu0mythbuntu3

---

### Post by khPWXxF on 2014-06-14
Yes, same here - I was  PhilB before the password problems.

Does your disk show anything amiss in the SMART data?

PhilB

---

### Post by mr.raider2 on 2014-06-14
I reformatted the partition to ext4. Seems to be Ok for now.

---

