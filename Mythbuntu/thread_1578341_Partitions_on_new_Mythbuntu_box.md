---
title: "Partitions on new Mythbuntu box"
date: 2010-09-20
forum: Mythbuntu
---

### Post by Quadari on 2010-09-20
Hi All,

I'm setting up my first mythbuntu box on an old system with an 80GB hard drive.  Eventually this will probably get upgraded, but we're sticking with it for now just to see how things go.  My question is about partitioning and file systems.  Specifically I notice that the mythtv documentation [[COLOR="Blue"]strongly suggests[/COLOR]]("http://www.mythtv.org/docs/mythtv-HOWTO-3.html#ss3.1") using XFS or JFS.  So my questions are:

1)  Any particular reason to choose XFS over JFS or vice versa?

2)  Is there a reasons I should just format my entire drive as XFS/JFS?  I.e., are there problems running the operating system off of such a file system?  

This would be my preferred approach, since it avoids having to deal with partitioning issues.

3)  If the answer to #2 is "Nooooo.  You will cause a rip in the space-time continuum if you run the OS on XFS!", then my question is about what partitioning setup people would advise keeping in mind that I only have 80GB as of now and, obviously, want to keep as much for media files/recordings as possible.

Thanks!

---

### Post by bcg30506 on 2010-09-20
What I've done is create 4 partitions and it has worked really well.  In your case with just 80GB I might suggest:

1. / partition (for OS) as ext3 for 5GB
2. /home partition (for user home) as ext3 for 5GB
3. /var partition for recordings & database as xfs for 50GB
4. /data partition for user media (photos,videos,music) as xfs for 20GB

Of course, it all depends on your use.  My mythbuntu living box is our home's media center where we store music, all our digital pictures, and our camcorder videos.  I have a large 2nd HD mounted as /data for these.  I have roughly 5GB each for both the OS and my home directory.  Then the remainder of my primary drive is set to /var for mythtv to use recording TV and keeping the database and logs.  Of course, it's much larger than 80GB.

Your mileage may vary but we've been happy with this setup for years.

---

### Post by LowSky on 2010-09-20
1)No both are very similar
2)Both JFS and XFS are made for easy deletion of large files, but can be very slow for mass deletion of small files. You cannot shrink J/XFS partitions and I believe Ubuntu cannot be formatted using either by default. EXT4 is Ubuntu's default and is very well rounded for all tasks. EXT4 fixed many issue that EXT3 had, and delete performance is fine. If it wasn't the developers of Mythbuntu wouldn't use it.

3)Just do the normal Mythbuntu install. It will create a root partition and SWAP partition. This way you won't have to later edit the mythtv recording destinations or worry of not having enough room for installing software.

---

### Post by Quadari on 2010-09-20
> **LowSky said:**
> 
3)Just do the normal Mythbuntu install. It will create a root partition and SWAP partition. This way you won't have to later edit the mythtv recording destinations or worry of not having enough room for installing software.

Ahha.  So does the mythbuntu installer do some disk partitioning for you?  I guess I was under the (probably mistaken) impression that I should do the partitioning/formatting of my drive before running the installer.

Thanks for all the advice.

---

### Post by LowSky on 2010-09-20
well you can do it either way, but yes it can handle it during the install.

---

### Post by superm1 on 2010-09-20
> **Quadari said:**
> Ahha.  So does the mythbuntu installer do some disk partitioning for you?  I guess I was under the (probably mistaken) impression that I should do the partitioning/formatting of my drive before running the installer.

Thanks for all the advice.

Now how unuser friendly would that be if you were forced to do it before starting the installer? :)

The primary goal of the project is to simplify the setup and configuration experience of an otherwise vanilla mythtv install.

---

### Post by alien878 on 2010-09-21
1.  I run ext4 without any problems.  I think that recommendation is out dated.

2.  I would recommend putting the OS on a separate partition so that you won't have to worry about losing all of your user data if you reinstall.  The other advantage is that the OS partition can be cloned before an upgrade in case there are any surprises.  The downside is that it takes a little planning and tweaking to set up the separate partitions.  It's too bad that mythbuntu's default install isn't a little bit smarter about it's default partitions.  I think that is one thing LinHES has done well with it's /myth partition instead of mixing things into /var.

---

### Post by novellahub on 2010-09-21
> **Quadari said:**
> Ahha.  So does the mythbuntu installer do some disk partitioning for you?  I guess I was under the (probably mistaken) impression that I should do the partitioning/formatting of my drive before running the installer.

Thanks for all the advice.
The installer is quite flexable if you choose of custom partitioning scheme.

---

### Post by novellahub on 2010-09-21
My setup is similar to the Knoppmyth / Linhes setup:

Drive 1 (OS):
/ ext3 (8 gb)
/swap (2 gb)

Drive 2 (Storage):
/myth  XFS

In my /myth partition, I copied over the directories that were in /var/lib/mythtv

---

### Post by superm1 on 2010-09-21
> **alien878 said:**
> 1.  I run ext4 without any problems.  I think that recommendation is out dated.

2.  I would recommend putting the OS on a separate partition so that you won't have to worry about losing all of your user data if you reinstall.  The other advantage is that the OS partition can be cloned before an upgrade in case there are any surprises.  The downside is that it takes a little planning and tweaking to set up the separate partitions.  It's too bad that mythbuntu's default install isn't a little bit smarter about it's default partitions.  I think that is one thing LinHES has done well with it's /myth partition instead of mixing things into /var.
Actually the installer is smart in this regard.  It will only remove data included in the live cd image from an existing partition.  So you should just need to backup your database, and then you would be able to reinstall directly over the same partition and restore the database.

If it's not working that way, that's a bug.

---

### Post by canga on 2010-09-21
I had a mythbuntu 9.04 system with the mythtv directories on a separate disk that was formatted with an XFS file system,and it worked fine until the disk developed a few bad blocks.  I was not able to create a bad blocks list for the file system to ignore (maybe I didn't do enough research, maybe it can't be done!).  As a result I lost some of my recordings.

Subsequent incarnations of my mythbox (9.10 & 10.04) have used ext3 or ext4 filesystems for the mythtv directories with no problems.

There is a lot to learn with a mythtv system and having a go is the best way to start the education.  I am up to my fourth generation and so far have re-built my system from scratch each release incorporating lessons learned as I go.  So I suggest that you just install with one partition (plus a swap), using install defaults, and run it for a while.  Then you can look to improve your system by installing the next release, when it comes out next month, so that your system better meets your needs.  You will just need a plug-in external drive to back-up all of your recordings and the database prior to the upgrade.  Good luck and enjoy!

---

### Post by alien878 on 2010-09-22
> **superm1 said:**
> Actually the installer is smart in this regard.  It will only remove data included in the live cd image from an existing partition.  So you should just need to backup your database, and then you would be able to reinstall directly over the same partition and restore the database.

If it's not working that way, that's a bug.For an upgrade, yes.  However, for a clean install, last time I did it, it formatted /.  I also tried mounting my old myth directory (from LinHES) into /var/myth during the install and it warned me that anything mounted in /var would also be formatted.  I didn't try it, but from another post from someone, it does.

Maybe I missed an option somewhere.... but separating data from OS is an often accepted recommendation.  It's too bad mythbuntu doesn't do that on the default as the custom partition menus can be confusing to a first time installer.

---

