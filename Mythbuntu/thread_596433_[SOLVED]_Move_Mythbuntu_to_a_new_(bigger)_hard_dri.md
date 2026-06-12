---
title: "[SOLVED] Move Mythbuntu to a new (bigger) hard drive"
date: 2007-10-29
forum: Mythbuntu
---

### Post by elliott6 on 2007-10-29
Hello all!

Looking to move my current Mythbuntu (Gutsy) FE/BE (master) to another hard drive, and breakout the master BE.  I will retain all other hardware, stash away the BE, and put a new FE install in my good, modded HTPC case.  Any good guides, as I was not able to clone the drive and grow the XFS partition that has all of the recordings.

My current setup has a 60GB laptop HD partitioned as follows - 

6GB   / ext3
1.5GB swap
50GB /var xfs

I am looking to move everything to a 300GB hard drive, and basically grow the recordings partition (xfs didn't like this).

Should I reinstall and hope for the best copying things over?  Is there an easy way to move things that I don't know/remember?  Any guides available?

Mythbuntu is working quite swimmingly.  However, as I refresh my Linux skills, I am attempting a few more things.  Basically, I thought I might put everything in one box in the living room.  However, problems with the power supply and case, have brought me to reevaluate.  

Thanks for your help!  I am sure I am making this out to be harder than it is.  This Mythbuntu has been a wonderful solution, and like another poster, the WAF has been high!

-------
Abit AV8-3rd Eye, AMD64 3000+, 1GB, 6600GT, PVR150, 60GB HD, Mythbuntu 7.10

---

### Post by superm1 on 2007-10-29
> **elliott6 said:**
> Hello all!

Looking to move my current Mythbuntu (Gutsy) FE/BE (master) to another hard drive, and breakout the master BE.  I will retain all other hardware, stash away the BE, and put a new FE install in my good, modded HTPC case.  Any good guides, as I was not able to clone the drive and grow the XFS partition that has all of the recordings.

My current setup has a 60GB laptop HD partitioned as follows - 

6GB   / ext3
1.5GB swap
50GB /var xfs

I am looking to move everything to a 300GB hard drive, and basically grow the recordings partition (xfs didn't like this).

Should I reinstall and hope for the best copying things over?  Is there an easy way to move things that I don't know/remember?  Any guides available?

Mythbuntu is working quite swimmingly.  However, as I refresh my Linux skills, I am attempting a few more things.  Basically, I thought I might put everything in one box in the living room.  However, problems with the power supply and case, have brought me to reevaluate.  

Thanks for your help!  I am sure I am making this out to be harder than it is.  This Mythbuntu has been a wonderful solution, and like another poster, the WAF has been high!

-------
Abit AV8-3rd Eye, AMD64 3000+, 1GB, 6600GT, PVR150, 60GB HD, Mythbuntu 7.10
I think your best bet is to do this:

1) Boot a live disk
2) Format the new drive as xfs for the full size
3) sudo rsync -avz /mount1/ /mount2/
3) sudo grub-install /dev/sdX

---

### Post by elliott6 on 2007-10-29
Thanks for the reply.  I have been able to sort out the formatting issue, but I do have a question, if you wouldn't mind clarifying for me.

> **superm1 said:**
> 
2) Format the new drive as xfs for the full size


Is this format the entire space on the drive as XFS?  Or format it the way I have (3 partitions), and the last format for the leftover empty space as XFS?

> **superm1 said:**
> 
3) sudo rsync -avz /mount1/ /mount2/


Is it /mount1/ and /mount2/, or do I need to replace this with sda1 and sdb1, or / and /var/lib, or something?

> **superm1 said:**
> 
3) sudo grub-install /dev/sdX


And would I be correct here if I were to replace X with the appropriate drive I am transferring TO.. in this case 'b'?!

I have been reading up on rsync, just want to make sure I do it right once, then to fumble through and create more errors.  Thanks for the response, this project truly is worth it!

---

### Post by superm1 on 2007-10-29
> **elliott6 said:**
> 
Is this format the entire space on the drive as XFS?  Or format it the way I have (3 partitions), and the last format for the leftover empty space as XFS?

If you had 3 partitions previously, you will need to rsync all partitions and format the new drive accordingly.  Adjust the other steps

> 
Is it /mount1/ and /mount2/, or do I need to replace this with sda1 and sdb1, or / and /var/lib, or something?

That was assuming that you would mount them in certain areas.  Choose your own areas to mount them.

> 
And would I be correct here if I were to replace X with the appropriate drive I am transferring TO.. in this case 'b'?!

Yes, rsync -avz blah blah2
where blah is from and blah2 is to.

> 

I have been reading up on rsync, just want to make sure I do it right once, then to fumble through and create more errors.  Thanks for the response, this project truly is worth it!
Good Luck!

---

### Post by elliott6 on 2007-10-31
Hey Superm...

Thanks for your help thus far.

I was able to partition and rsync the drive over to the newer, larger drive.  However, when I ran the sudo grub-install /dev/sda command, I was greeted with the following message - "Probing devices to guess BIOS drivers.  This may take a long time.
"Could not find device for /boot.  Not found or not a block device."

When I reboot with the live disk, all seems well.  When I reboot to hard drive, it does allow me to go into the grub menu, but upon trying to load, I get stuck at the Mythbuntu splash screen, with but a sliver on the progress bar.  This hangs for quite some time.

Any thoughts as to what I might have hosed up?  Hope you don't mind me coming to the source.  I have read up a bunch on partitioning and rsync.  Now I am looking to grub installs.  Just want to stay the course and get this solved (and learn along the way).  Thanks!

---

### Post by superm1 on 2007-10-31
> **elliott6 said:**
> Hey Superm...

Thanks for your help thus far.

I was able to partition and rsync the drive over to the newer, larger drive.  However, when I ran the sudo grub-install /dev/sda command, I was greeted with the following message - "Probing devices to guess BIOS drivers.  This may take a long time.
"Could not find device for /boot.  Not found or not a block device."

When I reboot with the live disk, all seems well.  When I reboot to hard drive, it does allow me to go into the grub menu, but upon trying to load, I get stuck at the Mythbuntu splash screen, with but a sliver on the progress bar.  This hangs for quite some time.

Any thoughts as to what I might have hosed up?  Hope you don't mind me coming to the source.  I have read up a bunch on partitioning and rsync.  Now I am looking to grub installs.  Just want to stay the course and get this solved (and learn along the way).  Thanks!
Yeah.

You will need to find the UUID for your partitions on the new drive.  Boot back up the live disk.  Mount your new drive.  

Check out the UUIDs.  For example, this is what I see:
```
supermario@portablemario:/dev/disk$ ls -alh /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 100 2007-10-31 08:36 .
drwxr-xr-x 5 root root 100 2007-10-31 08:36 ..
lrwxrwxrwx 1 root root  10 2007-10-31 08:36 356a8625-426a-457e-9174-b2b05585abfb -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-10-31 08:36 c5da5eee-0fff-4e15-92a7-057696bf493f -> ../../sda2
lrwxrwxrwx 1 root root  10 2007-10-31 08:36 ce17be0d-2cbf-4cb6-b729-30998993f938 -> ../../sda3

```

Edit /etc/fstab
There will be a UUID=some_long_number_letters
Replace that with the proper UUID that is that you found in /dev/disk/by-uuid.

Edit /boot/grub/menu.lst
The root partition's UUID needs to be replaced here too.

---

### Post by elliott6 on 2007-10-31
Thanks again Super Mario!

I sort of knew it had to do with the id of the drive, but wasn't sure how to get to them, and my searches were both incomplete and not relevant.

I will do this when I get home.  Hopefully this backend will be up and running before the trick o' treaters come hollerin'.  Then I can move on to setting up my new frontend.  

You'll hear back from me this evening!

Thanks and Happy Halloween!

---

### Post by elliott6 on 2007-10-31
And as you probably guessed/knew, it worked like a champ!

Able to lookup my UU-ID, find and replace in the appropriate files, and she is up an running.  Recorded all of primetime while watching a few of the transferred videos I had!  Space is back to 84% free.

This can be marked as solved... and learned.  Picked up quite a bit (as always).  Now on to the separation of the backend from the frontend, and what else I might do.  

Thanks!!!

---

### Post by EasyRiderOnTheStorm on 2008-12-08
Thank you Superm for the guidance. I found myself in the almost exactly same situation, even about the HDD sizes and partitions, and thanks to you I'm now enjoying my new drive, without a hitch.

I've also seen the "Could not find device for /boot. Not found or not a block device." message for the "sudo grub-install /dev/sdb" command (my new disk was the _second one_ beside the original one at the time), but I missed it in this thread, so I also did...

```
sudo grub
root (hd1,0)
setup (hd1)
exit
```

...just to be sure. Either way, it booted right up and away. Thanks again. This really should be a guide/howto/sticky... ):P

---

### Post by bmwman on 2008-12-09
Would just copying the old drive to the new drive with Ghost similar work? I do it all the time at work with Windows and it works fine. Ghost copies sector by sector and just adds the extra space from the bigger drive.

---

### Post by EasyRiderOnTheStorm on 2008-12-09
> **bmwman said:**
> Would just copying the old drive to the new drive with Ghost similar work? I do it all the time at work with Windows and it works fine. Ghost copies sector by sector and just adds the extra space from the bigger drive.

I'm no Ghost expert by any means, but it's my understanding that if you have non-ext2/3 partition (such as XFS, as recommended for recording partitions) you'd have problems since Ghost does not seem to support them. Also, I don't think Ghost would rewrite the necessary UUID's (as detailed in earlier posts) for your new disk, if your disk is being mounted by UUID. Other than that, it might work fine, I have no idea.

---

### Post by bmwman on 2008-12-09
I'm using Ext3 rightnow for storage and recordings. Is XFS any better? And if so, is this method going to work since I would be syncing Ext3 from the old drive to XFS on the new drive?

---

### Post by EasyRiderOnTheStorm on 2008-12-09
> **bmwman said:**
> I'm using Ext3 rightnow for storage and recordings. Is XFS any better?

There is a detailed discussion of XFS vs. MythTV [[here]("http://www.mythtv.org/wiki/index.php/XFS_Filesystem")]. I'll quote the part regarding it's advantages:

> Major advantages of XFS

   1. Handles large files much better and more efficiently than ext3.
   2. Minimizes both storage access time (HD read/write) and processing power (very low CPU usage).
   3. Allows users to defrag files to further minimize read/write times.

> **bmwman said:**
> And if so, is this method going to work since I would be syncing Ext3 from the old drive to XFS on the new drive?

I don't know what file-level syncing Ghost can do, but I understand it wouldn't do partition-level cloning on XFS; probably not even a file-level one. It would obviously work with the "rsync" command from the earlier posts since that works at file level, and as such, it might even be ok to just copy everything over, considering that XFS is recommended as the "recording" / data partition, which probably only holds music, photos and videos anyway. I only tried the way presented in this thread, though, so...

---

### Post by bmwman on 2008-12-09
OK,I will use XFS when i buy my new HDD. So does the OS need to be on separate  Ext3 partition or everything can be XFS. Also I have 500gb Ext3 which is full with movies and music. It's only for storage. Can I convert it to XFS without formatting it or need to take all the data off and format it to XFS?

Thanks

---

### Post by EasyRiderOnTheStorm on 2008-12-11
> **bmwman said:**
> So does the OS need to be on separate Ext3 partition or everything can be XFS. Also I have 500gb Ext3 which is full with movies and music. It's only for storage. Can I convert it to XFS without formatting it or need to take all the data off and format it to XFS?

Well, I see no reason why both could not be on the same XFS partition, but, the darndest thing, XFS is not particularly robust against system crash (power loss). That may not be a big issue for the last bit of LiveTV you were watching, but I think it would be definitely aggravating to end up with a corrupted system or MythTV database.

I didn't find easy ways to convert to XFS on-the-fly; 'anyfs-tools' may or may not be able to do it, but it's not in the Ubuntu repository as far as I can tell, so it might be easier and safer to just save, format and copy back the files if possible...

---

