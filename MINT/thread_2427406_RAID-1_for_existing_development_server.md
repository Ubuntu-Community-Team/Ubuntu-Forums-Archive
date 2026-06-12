---
title: "RAID-1 for existing development server"
date: 2019-09-21
forum: MINT
---

### Post by turtle320 on 2019-09-21
I have a Dell Optiplex 790 DT i5-2400 Quad-Core 3.1GHz 16GB RAM 2TB that I use for PHP/MySQL software development.  I'm also using it as a high value development server.  It stores mission critical work so I can't afford to lose information on it from HD failures.  I have 2x 2TB HDs of the exact same type (purchased a second one exactly like the first). 


How can I set up RAID-1 between the 2 HDs while still keeping everything I already have?


Particulars:
[ ]  I don't know much about RAID or Linux although I am running a LAMP server for development work.
[ ]  Need RAID-1
[ ]  I assume I need to add a RAID card.
[ ]  Prefer low cost RAID card ($100-$200).
[ ]  I need to preserve the entire OS and everything installed on the first HD during initial RAID mirroring.  
[ ]  Need SMART monitoring to know when a HD is dying.
[ ]  The RAID card must fit within the case of the Dell Optiplex 790 DT.  [https://i.dell.com/sites/csdocuments/Shared-Content_data-Sheets_Documents/en/us/optiplex-790-customer-brochure.pdf](https://i.dell.com/sites/csdocuments/Shared-Content_data-Sheets_Documents/en/us/optiplex-790-customer-brochure.pdf)     Looks like it uses half-height PCIex16 cards and one half-height PCIex1 card.
[ ]  Should be future proof.  If a HD dies, I intend to replace both with whatever I can buy at the time for cheap but comparable HDD size.  Would I be able to mix 2 completely different HDs (different brands, different sizes)?
[ ]  Must work with Linux and be relatively future proof with Linux.  I'm using Linux Mint 19.1 Cinammon.

---

### Post by fragglebliss on 2019-09-22
> **turtle320 said:**
> [ ]  I don't know much about RAID or Linux although I am running a LAMP server for development work.You lost my interest when you said this. Because what you're trying to do requires advanced knowledge. And if you're putting it out there that you "don't know much about RAID or Linux" then I'd suggest you're not up to the task to begin with.

---

### Post by TheFu on 2019-09-22
> **turtle320 said:**
> I have a Dell Optiplex 790 DT i5-2400 Quad-Core 3.1GHz 16GB RAM 2TB that I use for PHP/MySQL software development.  I'm also using it as a high value development server.  It stores mission critical work so I can't afford to lose information on it from HD failures.  I have 2x 2TB HDs of the exact same type (purchased a second one exactly like the first). 
First, how are your system and data backups?  If the backups are 100% perfect, know-you-can-restore, then you aren't ready for RAID.  RAID solves 2 problems.  Backups solve 1001 problems, including a corrupted RAID array.

No backups?  Don't even consider RAID.  Period.

> **turtle320 said:**
> 
How can I set up RAID-1 between the 2 HDs while still keeping everything I already have?

If they are new disks, this is easy, when you know how.  But Linux admin skills aren't point-n-click.  They build on prior skills, so you need to be intermediate with your Linux skills before tackling more advanced admin skills.

> **turtle320 said:**
> 
Particulars:
[ ]  I don't know much about RAID or Linux although I am running a LAMP server for development work.
You need to learn about RAID and perhaps LVM.  There are many storage techniques that normal users have never heard about.  Windows skills don't matter at all.

> **turtle320 said:**
> 
[ ]  Need RAID-1
Best choice for HA needs for disks over 1TB in size.

> **turtle320 said:**
> 
[ ]  I assume I need to add a RAID card.
Wrong.  Unless you are willing to buy 2 RAID cards - probably in the $300/ea range, you don't want HW-RAID.  Use SW-RAID, which is rock solid in Linux and often faster.

> **turtle320 said:**
> 
[ ]  Prefer low cost RAID card ($100-$200).
Nope. Bad idea. This is exactly what you DO NOT WANT.

> **turtle320 said:**
> 
[ ]  I need to preserve the entire OS and everything installed on the first HD during initial RAID mirroring.  
If you have a disk already and plan to add 2 more. Leave the 1st alone.  Mirror only the 2 new.

> **turtle320 said:**
> 
[ ]  Need SMART monitoring to know when a HD is dying.
smartctl.  However, HDDs fail about 22% of the time when SMART doesn't show anything wrong.  

> **turtle320 said:**
> 
[ ]  The RAID card must fit within the case of the Dell Optiplex 790 DT.  [https://i.dell.com/sites/csdocuments/Shared-Content_data-Sheets_Documents/en/us/optiplex-790-customer-brochure.pdf](https://i.dell.com/sites/csdocuments/Shared-Content_data-Sheets_Documents/en/us/optiplex-790-customer-brochure.pdf)     Looks like it uses half-height PCIex16 cards and one half-height PCIex1 card.
You don't need/want any hardware.  HW-RAID is netorious for not working without using the same, identical, version of the RAID cards.

> **turtle320 said:**
> 
[ ]  Should be future proof.  If a HD dies, I intend to replace both with whatever I can buy at the time for cheap but comparable HDD size.  Would I be able to mix 2 completely different HDs (different brands, different sizes)?

HW doesn't work this way, especially RAID.

> **turtle320 said:**
> 
[ ]  Must work with Linux and be relatively future proof with Linux.  I'm using Linux Mint 19.1 Cinammon.
I know ZERO, nothing, about Mint. You are on your own with that.

You need to do your research on LVM, RAID, and Linux administration.  If you don't have perfect backups. Stop.  That is 1000x more important than RAID anything

---

### Post by SeijiSensei on 2019-09-22
Remember the adage, "RAID is not a substitute for backups."  

Rather than buying a RAID card, use [software RAID]("https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04"). Spend that money on a backup device. I use one of [these]("https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817").  I reformatted it to ext4 since I'm only backing up Linux systems.

---

### Post by turtle320 on 2019-09-22
> **fragglebliss said:**
> You lost my interest when you said this. Because what you're trying to do requires advanced knowledge. And if you're putting it out there that you "don't know much about RAID or Linux" then I'd suggest you're not up to the task to begin with.

Interesting that I've been able to teach C and microcontroller programming to high school students and elderly people.  They too were not "up to the task" to begin with.  I put that disclaimer up there because I want to avoid people talking in techno-jibberish to compensate for their inability to explain things.  In case you haven't noticed, Linux has a big problem with documentation, usability, and ergonomics.  Even those of us that learned originally to design microchips and code at the assembly level sometimes are learning from ground zero when we switch platforms.  Linux just makes everything seem FAR more complicated than it needs to be for a multitude of reasons that I could write a book about.

>First, how are your system and data backups?  If the backups are 100% perfect, know-you-can-restore, then you aren't ready for RAID.  RAID solves 2 problems.  Backups solve >1001 problems, including a corrupted RAID array.
>No backups?  Don't even consider RAID.  Period.

I have a backup but it's not ideal.  I'm making mirror copies of the HD using Clonezilla to a USB HD.  Also, I do copy all my development files over to another computer that has RAID-1 storage via MDADM.  The problem with both these is they don't work well with SQL databases in the sense that tens of thousands of changes can occur in the database between backups even with just me using it for development.  That's why I was looking for a more realtime option.


>If they are new disks, this is easy, when you know how.  But Linux admin skills aren't point-n-click.  They build on prior skills, so you need to be intermediate with your Linux >skills before tackling more advanced admin skills.

I'm using MDADM already on other machines.  Setting up new disks was challenging at first but I figured it out now reliably.  Doing MDADM on an existing disk with all those partitions and GRUB has turned out to be terminally challenging.  


>You need to learn about RAID and perhaps LVM.  There are many storage techniques that normal users have never heard about.  Windows skills don't matter at all.

I noticed, and that's too bad because at least Windows and even the MacOS have great point and click interfaces that don't unnecessarily complicate things.  Linux has been extremely unnecessarily difficult (and I'm saying that as an engineer).  It's just very very immature from many standpoints that Linux developers don't consider (e.g. human factors, GUI design, architecture, etc.).  So I'm trying to use Linux but even guys like me who watch electrons flow in logic gates have a hard time with Linux.


>Best choice for HA needs for disks over 1TB in size.

I don't understand this sentence.


>Wrong.  Unless you are willing to buy 2 RAID cards - probably in the $300/ea range, you don't want HW-RAID.  Use SW-RAID, which is rock solid in Linux and often faster.

Is there a guide that walks me through how to use MDADM to do this?  I keep reading that MDADM should NOT be used on a boot partition/OS but they never say why (like usual).  Also, I can't seem to find any good documentation anywhere.  The best documentation I've found that is light years beyond anything else Linux is at Digital Ocean, but they don't cover MDADM.

>If you have a disk already and plan to add 2 more. Leave the 1st alone.  Mirror only the 2 new.

You misunderstood.  I have 2 disks.  One is the normal boot/OS drive.  The other has nothing on it.  My intent was to set up RAID-1 from the existing system across to the other disk which is not yet installed.


>smartctl.  However, HDDs fail about 22% of the time when SMART doesn't show anything wrong. 
 
I use SMARTCTL on my other Linux computers and I have it set to alert me by email of a degredation in any parameter.  Yes, I know it's not perfect but it's defense in depth.  The reason I mentioned it was because when I was reading Newegg reviews on the $30 Chinese RAID cards, they said they don't provide SMART data at the controller level for SMARTCTL to read.


>You don't need/want any hardware.  HW-RAID is netorious for not working without using the same, identical, version of the RAID cards.

I'm very hesitant to waste money on hardware too.... but I've also been warned away from MDADM for this.  No one can really tell me why but that's what 'they' say.


>I know ZERO, nothing, about Mint. You are on your own with that.

Isn't it the same thing as Ubuntu with a different GUI?  I thought they were both Debian.  They appear to be binary compatible.  

>You need to do your research on LVM, RAID, and Linux administration.  If you don't have perfect backups. Stop.  That is 1000x more important than RAID anything

I have researched.  I can't find good answers.  Posting here is part of the research.  Theoretically if the documentation were any good, and if the OS were more sophisticated, it wouldn't be such an effort to do such a simple thing, but unfortunately it is, so here I am.

>Remember the adage, "RAID is not a substitute for backups." 
 
I know... I've been hearing that for 20 years.  In fact, it's about the most help you ever get around here - most "sysadmins" just reflexively say that without even trying to understand that it is not a backup that is being sought in the first place.

>Rather than buying a RAID card, use [software RAID]("https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04"). Spend that money on a backup device. I use one of [these]("https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817").  I reformatted it to ext4 since I'm only backing up Linux systems.

I'm using MDADM on 2 other Linux machines and it was my first choice but I don't know how to make MDADM deal with the boot HD/partitions/GRUB.  The only guides I've found are ancient and probably no longer relevant.  Also, I do have a backup.  Two in fact.  However, they are not adequate for the realtime nature of the database work I'm doing which has too many transactions to back up like normal files.  

Is there a *good* guide written in the last 2 years that explains how to use MDADM for the boot HDD/OS for an *existing* system?  I've looked and looked but found nothing well written.

> **SeijiSensei said:**
> Remember the adage, "RAID is not a substitute for backups."  

Rather than buying a RAID card, use [software RAID]("https://www.digitalocean.com/community/tutorials/how-to-create-raid-arrays-with-mdadm-on-ubuntu-16-04"). Spend that money on a backup device. I use one of [these]("https://www.newegg.com/seagate-model-stea4000400-4tb/p/N82E16822178817").  I reformatted it to ext4 since I'm only backing up Linux systems.

BTW, I looked at the software RAID link... that's the same Digital Ocean guide I used (in concert with 2 weeks of additional other research) to get MDADM up and running.

Regarding the HD you showed me.... I'm actually backing up to one of those using Clonezilla (whole HD backup) and then hourly by using incremental file copies to another Linux server using RAID-1.  

I was originally using one of those USB 3.0 HDDs in MDADM but then I figured out that it didn't support SMART so I switched to regular internal HDs.  Some external USB HDDs do support SMART but the brand I was using didn't (Seagate?).

---

### Post by howefield on 2019-09-22
Thread moved to the "*MINT*" forum.

---

### Post by TheFu on 2019-09-22
Being crazy-flexible is what we gain with Linux solutions.  1-size doesn't fit everyone.   

Some existing posts about RAID.  
[https://ubuntuforums.org/showthread.php?t=2425255](https://ubuntuforums.org/showthread.php?t=2425255) 
[https://ubuntuforums.org/showthread.php?t=2422516](https://ubuntuforums.org/showthread.php?t=2422516) 
 
Almost every command is documented on the system already in the manpages.  Millions of admins use them daily, successfully, and have for 40+ yrs, so I'm inclined to think the manpages are fine.  Plus, manpages are THE documentation for the specific version of each command on YOUR system.  That's were webpages fail.
We all have gaps in our knowledge. If there is a new term that I don't understand, I'll research it, until the manpage makes sense. Not everything, in every detail, can be explained, in 1 place.  Manpages are laid out for experts with just the summary at the top. Deeper knowledge is provided farther down.

---

### Post by SeijiSensei on 2019-09-22
My solution is to partition the drives so that /boot is on a 512 MB partition of its own. I keep a spare copy on the other drive.  On traditional MBR systems I'll make the rest an extended partition.

I usually have a couple of virtual partitions in that extended one where I can put at least two copies of Ubuntu. That let's me experiment with another version of Linux while leaving the working one intact. The rest of the drive I use for /home, and it's there that I use RAID. So I'll have three un-RAIDED partitions that together occupy no more than 50 GB of each drive, and a fourth very large RAIDed one.

---

### Post by Skaperen on 2019-09-22
> I have a backup but it's not ideal.  I'm making mirror copies of the HD  using Clonezilla to a USB HD.  Also, I do copy all my development files  over to another computer that has RAID-1 storage via MDADM.  The problem  with both these is they don't work well with SQL databases in the sense  that tens of thousands of changes can occur in the database between  backups even with just me using it for development.  That's why I was  looking for a more realtime option.

such as?  RAID is not any kind of backup solution.

backing up a database is not anywhere even close.


>  noticed, and that's too bad because at least Windows and even the MacOS  have great point and click interfaces that don't unnecessarily  complicate things.  Linux has been extremely unnecessarily difficult  (and I'm saying that as an engineer).  It's just very very immature from  many standpoints that Linux developers don't consider (e.g. human  factors, GUI design, architecture, etc.).  So I'm trying to use Linux  but even guys like me who watch electrons flow in logic gates have a  hard time with Linux.

the power of Linux is that it can do all those things that can't be done through just point and click, such as well thought-out design decisions.  Linux doesn't do the thinking, of course.  but, Linux gives the experienced and educated administrator substantially more choices that the average user has never even heard the buzz-words for.  that allows designs to be correct.


> Is there a guide that walks me through how to use MDADM to do this?  I  keep reading that MDADM should NOT be used on a boot partition/OS but  they never say why (like usual).  Also, I can't seem to find any good  documentation anywhere.  The best documentation I've found that is light  years beyond anything else Linux is at Digital Ocean, but they don't  cover MDADM.

cloud providers provide the redundancy for you.  there is no need to run RAID in cloud services.  maybe you should run things there.


> You misunderstood.  I have 2 disks.  One is the normal boot/OS drive.   The other has nothing on it.  My intent was to set up RAID-1 from the  existing system across to the other disk which is not yet installed.

maybe the question should be why have you decided to do it this way?  the very first RAID i ever did was not like that, at all.


> Isn't it the same thing as Ubuntu with a different GUI?  I thought they  were both Debian.  They appear to be binary compatible.

they are mostly binary compatible.  some system settings are different, even with the same GUI.


> I have researched.  I can't find good answers.  Posting here is part of  the research.  Theoretically if the documentation were any good, and if  the OS were more sophisticated, it wouldn't be such an effort to do such  a simple thing, but unfortunately it is, so here I am.

Linux is far more sophisticated than Windows can ever hope to be.  but, like i said, earlier, it doesn't do the design thinking.  if you were looking for what to click on or even what command to type in, that explains why you didn't find what you were looking for.

i'm a command-line type of person.  but even for me, i had to think out what i wanted done before i typed in the command.  if i thought it out wrong (and that has happened, with terrible results), the command is not going to help.  buttons to click on can't do any better.


> Is there a *good* guide written in the last 2 years that explains how to  use MDADM for the boot HDD/OS for an *existing* system?  I've looked  and looked but found nothing well written.

If there was it would blank.  look around for why not.  look at blogs, maybe someone is willing to cry their heart out.  i didn't need to read this online.  it was one of the first things i figured out on my own.

---

### Post by SeijiSensei on 2019-09-23
> **turtle320 said:**
> The problem with both these is they don't work well with SQL databases in the sense that tens of thousands of changes can occur in the database between backups even with just me using it for development.  That's why I was looking for a more realtime option.
If you choose PostgreSQL as your database engine, it has extensive facilities for real-time replication.

[https://www.postgresql.org/docs/current/high-availability.html](https://www.postgresql.org/docs/current/high-availability.html)

[https://www.postgresql.org/docs/current/runtime-config-replication.html](https://www.postgresql.org/docs/current/runtime-config-replication.html)

I've used PG for years without any of this, but my databases have very low transaction rates.  I just use pg_dumpall to create a plain-text backup of all my databases and ship it to my backup server once each night.

---

### Post by TheFu on 2019-09-23
If you use LVM, then it is possible to quiesce the DB storage using LVM snapshots, then take the backup of the snapshot.  LVM has the ability to provide RAID, if the PV/VG and LV are setup on multiple disks at creation time. LVM uses mdadm internally.

Or you can do the mdadm stuff to make a RAID device, then layer LVM over it.

Or you can use ZFS which can do RAID-whatever and supports snapshots.

Alas, all the documentation for these is written for admins.

---

