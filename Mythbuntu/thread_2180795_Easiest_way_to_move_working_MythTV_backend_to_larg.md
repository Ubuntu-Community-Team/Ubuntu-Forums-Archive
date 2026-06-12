---
title: "Easiest way to move working MythTV backend to larger hard drive?"
date: 2013-10-14
forum: Mythbuntu
---

### Post by bullwinkle2 on 2013-10-14
I have installed Mythbuntu 12.04.3 LTS on a repurposed Mac Mini (no longer using OS X on that machine, just Mythbuntu).  The MythTV backend version, according to Synaptic, is 2:0.25.3+fixes20130813… And I would like to keep that version because it has proven to be stable and reliable.  I keep seeing threads where people have upgraded MythTV and then have regretted it because some important feature stopped working, so I don't want to do that.  I'm happy to stick with the old, reliable version I am running now, since it does everything I want and doesn't give me any problems.  

The problem is that the Mac Mini only has a single 80 GB hard drive which obviously is not a lot of storage.  I can apparently replace it with a 1 TB internal drive, but since my entire installation is on the smaller drive, I was wondering what is the best way to simply copy the entire installation from the old drive to the new drive with maximum reliability and the minimum amount of hassle.  The Mac Mini has a CD/DVD drive that can be used for booting but as far as I know there is no way to boot from a USB stick.  The ideal situation would probably be some software that can be burned to a CD, that would copy the existing installation to another share on the local network (on a different machine), and then after the new drive is installed, that same CD could be put back in and it would format the new drive, then set up the network connection and go out and get the saved copy, and copy it back to the larger drive, adjusting the partition sizes automatically (I know almost nothing about partitions other than that they exist).  Does such a piece of software exist, or is there perhaps a better solution that I have not considered? 

Please understand that any solution has to be relatively simple for me to use it - if you have to specify a bunch of obscure options on a command line I probably won't be able to figure it out, and I really prefer to work with a GUI-based solution anyway.

---

### Post by azmyth on 2013-10-15
The easiest thing to do is install the HD and then format it and then create a mount point on your other HD and then mount the new hard drive there. You can edit the fstab to have it mount on every boot.

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

You can then have mythtv point to the new hard drive to save recordings/

---

### Post by uteck on 2013-10-16
Or you could backup the database and recordings, then just build the new system and copy the recordings over and import the database.
The really import thing is the database and recordings, everything else you can reinstall, so back them up no matter what you do.  For extra protection clone the hardrive so you can restore it entirely, that way you could experiment with with .27.

---

### Post by dannyboy79 on 2013-10-18
why not just hook up the 1TB drive to the mac mini usb port and add another storage directory? thats the easiest IMO.

---

### Post by uteck on 2013-10-18
Adding the drive via USB is easy, but will have problems when you try to record and play back a recording, or wathc live TV.  The USB2 buss will not do simultaneous read/write so that causes a problem with videos which take a lot of bandwidth.

---

### Post by bullwinkle2 on 2013-10-26
Thanks for the suggestions.  The USN drive is out due to speed considerations.  Really what I would like to do is exactly clone the existing drive, then transfer that to the new drive, but with correctly resized partitions. I found a program called Redo Backup and Recovery that might do what I need, so I'm thinking about trying that first.  Sorry I don't reply in a more timely manner but logging into the Ubuntu Forums tends to be a little bit of a pain now, so I have a tendency to put it off and then I forget for a few days.

---

### Post by neutron68 on 2013-10-28
For the last 5 years, I've been using Acronis True Image 10 to make bootable hard drive clones to bigger hard drives.

The high points:
- runs from a bootable CD
- GUI interface, with mouse support (click-click-DONE)
- can resize a drive partition as it clones it
- clones both Linux and Windows file systems
- makes fully-bootable clone of source hard drive

[http://en.wikipedia.org/wiki/Acronis_True_Image](http://en.wikipedia.org/wiki/Acronis_True_Image)

---

### Post by bullwinkle2 on 2013-10-30
Two problems with that one.  First, it appears to be a commercial solution that only gives you a 30 day trial, and they don't specify what happens after the 30 days are up.  Second, it appears that the software has to be installed on a computer running Windows, and we don't have any such animal here.  And even if we did, I'm not sure how installing that software on a Windows computer would help in backing up a Ubuntu box - I'm not say there isn't a way (maybe the software lets you burn a bootable disk?) but whatever it is, if it has to be installed under Windows first it won't work here.  In looking over their site, I get the impression that they might have had better support for Linux at some time in the past, but not so much in the latest versions.  Also, I downloaded their manual and it seems like a really complicated piece of software, though I suppose it's like anything else, if you use it a lot you know exactly what to click on. 

So far, the two most likely candidates I have found appear to be Clonezilla Live ([http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)) and Redo Backup ([http://redobackup.org/download.php](http://redobackup.org/download.php)).  Not sure which is better at this point but both can be downloaded as ISO's and burned directly to a CD, without the hassle of installing anything on any system.

---

### Post by neutron68 on 2013-10-30
> **bullwinkle2 said:**
> Two problems with that one.  First, it appears to be a commercial solution that only gives you a 30 day trial, and they don't specify what happens after the 30 days are up.  

I don't see that as an issue.  You simply buy it, and it works forever.  I'm still using the copy I bought in 2007!

> **bullwinkle2 said:**
> Second, it appears that the software has to be installed on a computer running Windows, and we don't have any such animal here.  And even if we did, I'm not sure how installing that software on a Windows computer would help in backing up a Ubuntu box.  

I referenced using Acronis as a bootable CD (a Live CD). 

> **bullwinkle2 said:**
> 
 - I'm not say there isn't a way (maybe the software lets you burn a bootable disk?) but whatever it is, if it has to be installed under Windows first it won't work here.  

Granted, to create the Acronis Live CD, you do need to load Acronis on a Windows machine first.  That isn't an issue in my world.  While I like Linux machines, there are still Windows machines at work and at home.

> **bullwinkle2 said:**
> In looking over their site, I get the impression that they might have had better support for Linux at some time in the past, but not so much in the latest versions.  Also, I downloaded their manual and it seems like a really complicated piece of software, though I suppose it's like anything else, if you use it a lot you know exactly what to click on. 

Hummm....I'll have to look at the most recent versions to see what you mean.  
In version 10, the Live CD could not be easier.  The Live CD boots to a GUI interface and you click to select your source hard drive, click to select your target hard drive and click the GO button.

> **bullwinkle2 said:**
> So far, the two most likely candidates I have found appear to be Clonezilla Live ([http://clonezilla.org/clonezilla-live.php](http://clonezilla.org/clonezilla-live.php)) and Redo Backup ([http://redobackup.org/download.php](http://redobackup.org/download.php)).  Not sure which is better at this point but both can be downloaded as ISO's and burned directly to a CD, without the hassle of installing anything on any system.

I have tried a Clonezilla Live CD in the past.  I found it's interface confusing, and was afraid of accidentally writing over my source hard drive (rather than backing up or cloning it).   I'll be curious to see what you think of it.
Be aware, Clonezilla isn't able to resize your source partitions as it clones to the new, bigger hard drive, like Acronis can.  You'll need to use something like the Gparted Live CD after the clone is done, to resize the partitions to fill the bigger hard drive.

Eric

---

### Post by bullwinkle2 on 2013-10-31
> **neutron68 said:**
> I don't see that as an issue.  You simply buy it, and it works forever.  I'm still using the copy I bought in 2007! 

I'm sorry, I thought this was the Ubuntu forum.  Not the "push commercial software when there are perfectly good free solutions available" forum (and also, not a Mac OS X forum, where people seem eager to empty their wallets, particularly if it's something Apple sells).  Maybe you were genuinely trying to be helpful, but to me, taken together your comments sound a bit spammy.  Sure you don't work for Acronis? 

> **neutron68 said:**
> Granted, to create the Acronis Live CD, you do need to load Acronis on a Windows machine first.  That isn't an issue in my world.  While I like Linux machines, there are still Windows machines at work and at home. 

I suppose you do have Windows machines there at your workplace at Acronis. (Just kidding - *I hope*).  But I honestly don't have any here, unless you count one really old system that has Windows 2000 on it and hasn't been turned on in many months, and it's been so long since I have used Windows that I can't even remember how you install software on it anymore.  Not everyone lives in a Windows-centric world. 

> **neutron68 said:**
> I have tried a Clonezilla Live CD in the past.  I found it's interface confusing, and was afraid of accidentally writing over my source hard drive (rather than backing up or cloning it).   I'll be curious to see what you think of it. Be aware, Clonezilla isn't able to resize your source partitions as it clones to the new, bigger hard drive, like Acronis can.  You'll need to use something like the Gparted Live CD after the clone is done, to resize the partitions to fill the bigger hard drive. 

Disparaging the (free) competition? Anyway, I don't know about Clonezilla (other than that it's recommended for this purpose in several articles I've read) but I do note that the Redo Backup site says this: 

[b]Q: Can I restore a backup to a smaller drive? 

A: No. Doing so likely would require modifying the bootloader, which defeats the simplicity of Redo Backup. Backups must be restored to a drive of equal or greater size. 

However, you can always restore to a larger drive, resize the partition, and back up the smaller partition if needed. Partitions can easily be resized using the included partition editor utility (GParted).[/b] 

So, it seems that they give you GParted right on the Redo Backup CD, and they might do that on the Clonezilla disk as well. 

Actually, there is another program I have used in the past that I really like, called Mondo Rescue ([http://www.mondorescue.org/](http://www.mondorescue.org/)).  The problem with it is that it is intended for use in backing up a "live" system (you can run it as a cron job) and it creates .iso files that you use to restore your system if something goes wrong.  That is very handy if, for example, you are running on a virtual machine, or if you have a computer that can boot from the network or an external hard drive, but the computer in which I want to replace the hard drive can only boot from its internal hard drive, which is the one being replaced, or from a CD/DVD.  Since I don't want to burn a bunch of CD's or DVD's, that one is kind of out for this project.  But I mention it because it's also free, and also able to resize partitions if you increase the volume size. 

I guess I just don't understand what would possibly make you think that a program that costs money AND has to be installed on a Windows system before the "live" CD can be created would in any way be an acceptable solution for backing up a Ubuntu system.  If it works for you, great, but it's not something that I would consider in a million years.  In fact, on this particular system I would simply format the new drive and start completely over from scratch before I'd do something like that, since none of the data on it is that valuable to me, and if any of it was, I can easily copy it to another drive on the network before installing the new disk.  All I was really wanting was to save myself a small bit of time reinstalling software.  And I can quite likely do that with either of the pieces of software I mentioned, and if one seems too complicated I will just try the other (I have already burned both to CD's).  And if it turns out I have to run GParted to grow a partition, well that is really not a big deal, now is it? 

If you have no connection whatsoever to Acronis then I apologize for my snarkiness, but I have seen too many cases where people come into a forum and try to push some commercial product and then if you do some digging, you find out that they are in some way connected to that company and a really just spamming on behalf of the company.  And anyway, IMHO you really should have mentioned up front that it's a commercial product AND that you need to have at least one system running Windows to utilize it.

---

### Post by one30nav on 2013-10-31
My $0.02 ... Clonezilla is awesome for this: Just follow the numerous howtos; you can image your current, installed hard drive to a USB "toaster," then use Gparted to extend the partition to encompass the entire new drive's capacity; move the swap file to the end of the newly expanded partition; finally, activate the swap file. Done.

Disclaimer: I only use Linux, but I think this should be the same for a Mac.

Clonezilla is really simple to use and I've recently donated to its creators (but it's really priceless).

---

### Post by neutron68 on 2013-10-31
> **bullwinkle2 said:**
> If you have no connection whatsoever to Acronis then I apologize for my snarkiness, but I have seen too many cases where people come into a forum and try to push some commercial product and then if you do some digging, you find out that they are in some way connected to that company and a really just spamming on behalf of the company.  And anyway, IMHO you really should have mentioned up front that it's a commercial product AND that you need to have at least one system running Windows to utilize it.

No, I don't have any connection with Acronis.  I simply bought their product, and found it to be a 1-step, GUI solution for cloning and resizing hard drive contents.  

In fairness, you didn't say you were looking for a totally free solution.  You asked for "Easiest way to move working MythTV backend to larger hard drive".  Acronis is the easiest way I know.  
I usually start it cloning before bedtime and check on it the next morning. 

I have been learning how to do more and more with Linux over the last 7 years, but I've not been able to totally replace Windows for EVERYTHING I do.  So, there are Linux machines and Windows machines in my life.

Please, let the forum know what method you end up using, and how the clone went.

Eric

---

### Post by bullwinkle2 on 2013-11-02
> **neutron68 said:**
> No, I don't have any connection with Acronis.  I simply bought their product, and found it to be a 1-step, GUI solution for cloning and resizing hard drive contents.    In fairness, you didn't say you were looking for a totally free solution.  You asked for "Easiest way to move working MythTV backend to larger hard drive".  In that case I retract some of my criticisms, but still I would think it somewhat obvious that if I'm posting in a Ubuntu forum, asking about about the easiest way to clone a Ubuntu derivative, I am NOT looking for a solution that requires Windows.  I still don't like it when you ask how to do something and people start offering for-pay solutions - that might be appropriate on a Mac OS X forum. because those folks are used to be treated that way, but many if not most Ubuntu and Linux users love their free software, particularly when it comes to utility software.  But I was really more put off by the fact that Windows was involved in any way, shape or form.  > **neutron68 said:**
> Acronis is the easiest way I know.   I usually start it cloning before bedtime and check on it the next morning.  I get that it works for you, just saying that it couldn't be more wrong for me.  > **neutron68 said:**
> Please, let the forum know what method you end up using, and how the clone went.  Actually, just as a test I wound up backing up using both Redo Backup and Clonezilla Live.  While both worked to make a backup, I wound up using Redo Backup to restore.  Personally, I just liked that program better, although either would likely have worked.  But I encountered a few issues with Clonezilla Live.  First, it offers three different versions for different systems, and the first I picked wouldn't boot, and I finally had to download and burn a CD with the "lowest common denominator" i486 version (I had originally picked the i686 version).  Redo Backup didn't give me any problems in that regard, it offered one version that just booted right up. 

Also, Clonezilla Live asked a few annoying questions during bootup (questions you would normally be asked when installing an operating system), and when it finally did boot it was a bit more difficult to figure out what to do.  Redo Backup makes it very clear how to proceed, and their user interface is more pleasing. 

Both would let me back up to the network, but neither could see my shared directory on the computer I wanted to send the backup to.  Redo will let you backup to an FTP server, so I set up an FTP server temporarily and let it backup to that.  Clonezilla Live gave the the option of backing up via SSH, so I used that to back up to a different computer on the network.  On that score I would tend to give Clonezilla Live the point.  And Clonezilla Live does offer to verify the backup after it's finished, which Redo Backup didn't.  But ultimately, when it came time to do the restore, I decided to try Redo Backup first, because I knew it would be less hassle and let me get the job done quickly, and besides, I'm a bit of a sucker for a nice-looking GUI. 

And Redo delivered - the restore worked with no hassle at all.  But what it did not do, and what the version of Clonezilla Live probably would not have done either, is to resize the partitions so that the extra space on the new drive would be used.  So, I downloaded GPartEd Live and burned it to a CD.  And GPartEd is one of those programs that if you've ever used it a few times, you know exactly what you need to do and could probably accomplish it quickly.  But as a first-time user I was mystified as to why I could not grow my data partition to use the new space on the drive.  GPartEd would allow me to shrink it, but not grow it.  It took looking at a few web pages to understand that the swap partition, which normally sits at the far end of the drive, was right after my original data partition and had to be moved to the end of the unallocated space - something that GPartEd can easily do, but they don't exactly make it intuitive for a new user.  This is a case where a simple popup informing the user of why the partition cannot be expanded would make a huge difference.  Anyway, after I got the swap partition moved out of the way, I was then able to grow my data partition with no problem, and then the new drive worked great, and everything was as it had been except I had a lot mode storage.

---

### Post by neutron68 on 2013-11-03
Thanks for the update.  Your impressions of Clonezilla are line with what I thought.

I usually clone from one physical hard drive to another physical hard drive.
I'll have a look at Redo Backup and see how I like it.

---

### Post by topcat5 on 2013-11-03
My recommendation, for anyone building a future system is to put everything,  except the MythTV storage stuff, on one small SSD.  Put MythTV's storage -  video,recordings,liveTV, music, banners, etc (anything defined on the storage groups page) on a large mechanical drive.   This way in the future, you can move everything (if you need to) simply by using the tar command. You won't need to worry about affecting the OS, bootloaders, whatever.    No special software needed as tar will do it all.   Of course is you are building a system, use a case that can take more than one drive.  Then you can add it to the storage group as suggested above.  

A couple of other comments about the SSD/Storage Drive 2 disk solution. 
I'd keep the DB and and Mythtv or Mythtv user home drive on the SSD.   Make sure the SSD is mounted with the options for SSD.   

I'd also recommend formatting the large storage drive with XFS as described in the MythTV wiki.   If you are buying a new mechanical drive then something slower like a WD Green drive works fine with Mythtv.   It uses less power and is quiet.

-------------------

Though I wouldn't expect that a Myth system would have one, IF there is a Windows 7 partition on your system, take care not to resize or move it with gparted.   If you do, you might find that it will no longer boot and there isn't a clear way to fix it.

---

### Post by novellahub on 2013-11-04
> **topcat5 said:**
> My recommendation, for anyone building a future system is to put everything,  except the MythTV storage stuff, on one small SSD.  Put MythTV's storage -  video,recordings,liveTV, music, banners, etc (anything defined on the storage groups page) on a large mechanical drive.   This way in the future, you can move everything (if you need to) simply by using the tar command. You won't need to worry about affecting the OS, bootloaders, whatever.    No special software needed as tar will do it all.   Of course is you are building a system, use a case that can take more than one drive.  Then you can add it to the storage group as suggested above.  

A couple of other comments about the SSD/Storage Drive 2 disk solution. 
I'd keep the DB and and Mythtv or Mythtv user home drive on the SSD.   Make sure the SSD is mounted with the options for SSD.   

I'd also recommend formatting the large storage drive with XFS as described in the MythTV wiki.   If you are buying a new mechanical drive then something slower like a WD Green drive works fine with Mythtv.   It uses less power and is quiet.


I agree with this.  My master backend uses a 64GB Samsung 830 series SSD with the Database and home directory on it.  All the recordings, videos, backups reside on 4 mechanical drives (Two 2 TB and two 1 TB drives).   The mechanical drives use XFS file systems and the SSD uses EXT4 with options enabled (noatime,discard).

I also use the same SSD on a separate frontend with fantastic results. Fast booting on both machines and no lag bringing up recordings or videos.

---

### Post by neutron68 on 2013-11-10
> **novellahub said:**
> I agree with this.  My master backend uses a 64GB Samsung 830 series SSD with the Database and home directory on it.  All the recordings, videos, backups reside on 4 mechanical drives (Two 2 TB and two 1 TB drives).   The mechanical drives use XFS file systems and the SSD uses EXT4 with options enabled (noatime,discard).

I also use the same SSD on a separate frontend with fantastic results. Fast booting on both machines and no lag bringing up recordings or videos.

How do you accomplish this?  
1. Can you do this to an already-installed Mythbuntu system, or must it be done at the time of install?
2. What steps (typed commands) and software tools do you need to accomplish the move?  

Thanks.

---

### Post by novellahub on 2013-11-18
> **neutron68 said:**
> How do you accomplish this?  
1. Can you do this to an already-installed Mythbuntu system, or must it be done at the time of install?
2. What steps (typed commands) and software tools do you need to accomplish the move?  

Thanks.

I did the partitioning at the time of install.  I did it as part of my migration from Mythbutu 10.04 to 12.04.

Here is a overview of my system partitioned on with the mount points:

64 GB SSD - / 
1 TB HD - /myth 
2 TB HD - /myth2
1 TB HD - /myth3
2 TB HD - /myth4

Under each mount point I keep my recordings under a folder named "tv" (Except for the SSD).  I did this using the advanced partitioning tool built into the Mythbuntu installer.  I keep my backups under the "backup" folder under  /myth (Backup of my custom scripts, tuner firmware, and database backups).


Here are the steps I did migrating from Mythbuntu 10.04 to Mythbuntu 12.04 (I was previously using a 500 GB drive for the OS install):

1. First I did a backup of the database [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore) and saved it on my backup folder under the /myth mount point.
2.  I removed the old 500 GB hard drive
3.  Installed new 64 GB SSD
4.  Started the Mythbuntu install and chose the advanced partitioning option
5.  I set up the partitioning as stated above.  I chose ext4 for the SSD and left the /myth type mount points using XFS.
6.  After the install was completed I did the restore of the database [http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)
7.  I then had to do some ownership chown for the /myth type partitions using the following command "chown -R mythtv:mythtv myth" (without quotes)
8.  I also had to do some chmod of the files so mythtv can write to the tv folders  "chmod -R 775 /mythv/tv" (without quotes)

---

### Post by neutron68 on 2014-10-18
> And Redo delivered - the restore worked with no hassle at all. But what it did not do, and what the version of Clonezilla Live probably would not have done either, is to resize the partitions so that the extra space on the new drive would be used. So, I downloaded GPartEd Live and burned it to a CD. And GPartEd is one of those programs that if you've ever used it a few times, you know exactly what you need to do and could probably accomplish it quickly. But as a first-time user I was mystified as to why I could not grow my data partition to use the new space on the drive. GPartEd would allow me to shrink it, but not grow it. It took looking at a few web pages to understand that the swap partition, which normally sits at the far end of the drive, was right after my original data partition and had to be moved to the end of the unallocated space - something that GPartEd can easily do, but they don't exactly make it intuitive for a new user.
I'm in the process of cloning Mythbuntu 12.04 to a larger hard drive and using gparted to stretch the partitions to fill the disk. 
In this case, Acronis True Image 2011 would not see my destination hard drive, so I had to try something else.  
Redo Backup 1.0.4 could not see my destination hard drive either!  But, Clonezilla 2.2.4-12 could.  Since Clonezilla can't clone and stretch in one automatic operation, I have to use gparted for the partition stretch portion of the task. 
I'd like to fill in the blanks of what was referenced above, in regard to using gparted to move the swap partition to the end of the disk.

In a default (single hard drive) install of Mythbuntu, the Linux swap partition is within an extended partition (2GB on my system), not inside the primary partition (EXT4 in my system).
When you clone a 1TB drive to a 2TB drive, there is a lot of allocated space after the swap partition of the 2TB drive.  In order to get the swap partition to the very end of the disk, you need to perform the steps listed below.

NOTE:  If you don't perform the disk tasks 1-at-a-time in gparted, the time needed to complete will be in the HOURS.  
**Perform tasks 1-at-a-time in gparted.**

1) Select the extended partition (2GB on my system) and grow it to end of the disk.  Click Apply and let the task finish.
2) Drag the swap partition to the end of the enlarged extended partition.  Click Apply and let the task finish.
3) Resize the extended partition so that it is the original size again (2GB on my system), by sliding the left boundary, to the right.  Click Apply and let the task finish.
4) Select the primary partition, and grow the primary partition to fill the unallocated space.  Click Apply and let the task finish.

If you do this as I suggest, the process will take around 10 minutes.

Speaking from experience, if you select a bunch of tasks (7, for example), gparted, will take HOURS to perform them.  
I tried the same list of tasks I detailed above to be performed after a single APPLY button press.  
It took 6 hours!  
see:
[http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/20141018_090546_zps0715ca4a.jpg](http://i870.photobucket.com/albums/ab264/neutron68/Mythbuntu/20141018_090546_zps0715ca4a.jpg)

The difference doing it 1-task-at-a-time is striking!

---

### Post by whosmatt on 2014-10-18
I just did this with my combined frontend/backend.  It was easy.  I booted with a gparted livecd with both drives attached.  First thing is to identify which drive is which.  gparted can tell you this.  Then, just use dd to copy the old drive to the new drive.  Once that finishes, reboot with the livecd once more with just the new drive attached.  You can then grow the / partition to the size of the new drive.  In my case, I had to remove the swap partition and re-create it.  That will require you to edit /etc/fstab to mount swap, but other than that, no issues.

I can give more info if necessary.
Matt

---

### Post by neutron68 on 2014-10-18
I'm in good shape, thanks.  I'm just waiting for the gparted process to complete.

The purpose of my last post was to help others in the future, by filling in the blanks that were left out previously.  
Quite often, people on forums do not detail all the steps they took in a process or procedure.  
I know I like to see all the steps laid out, and I bet others do, too.
An example of a good post, with all steps listed, is novellahub's, in this thread - bravo!

Cheers!
Eric

---

