---
title: "Large files - disk ideas"
date: 2008-10-07
forum: Multimedia Software
---

### Post by celtic426 on 2008-10-07
I have a bunch of video files about 8 gigs each and I wanna put them on my external drive which is a FAT32.  This failed the first time because FAT32 can only take files up to 4 gigs in size.  So I was gonna try to shrink and then reformat part of the drive with GParted but that did not work.  It did not give me the option of resizing it.  Do I have to do this with the livecd?  I do not see how that would matter because it is an external drive but I could be wrong there.

If that does not work is there a way to convert the FAT32 drive into something else and what do format do you recommend (this is just a 500 gb storage drive for multimedia).  

If that is not option then can anyone recommend a program for splitting .mkv files?

Any other ideas on how I could get these files onto my external drive would be great too.  Thanks!

---

### Post by mrtomservo on 2008-10-07
Resizing shouldn't be a problem with Gparted. :)  Try following the guide at the sourceforge site.  

[http://gparted.sourceforge.net/larry/resize/resizing.htm]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

---

### Post by celtic426 on 2008-10-07
Thanks for response and in writing my response to you I found something out.  The drive is locked and there are pictures of keys next to the drive in GParted.  

Whats the best thing to do now?  I found that if I unmount it in nautlius that I can resize it but GParted doesn't display the disk space taken up, only the total size.  Will this hurt my data?

---

### Post by haydnc on 2008-10-07
If you unmount the FAT32 drive from Nautilus then refresh the view you have in gparted it might show up the used space of the drive.

Unfortunately that is your only option because there is apparently no way to convert from FAT32 to Ext3 without altering /losing the data on the FAT32 drive.

Or - I should amend that to there was no way last time I looked into it. I don't believe it has changed since then.

---

### Post by gpsmikey on 2008-10-07
There are utilities to convert from FAT32 to NTFS though and NTFS can handle the large files.  Not sure under linux (I'm new here too ! ), but there are a number of ways under windows to do it.  You might want to check out the ntfsprogs package also (although it doesn't seem to have a fat32 to ntfs conversion utility in it) at [https://launchpad.net/ubuntu/hardy/+package/ntfsprogs](https://launchpad.net/ubuntu/hardy/+package/ntfsprogs)

mikey

---

### Post by celtic426 on 2008-10-07
Ok so Im using GParted again and I got it to resize the disk.  So I know have a bunch of unallocated space on the drive.  However, it won't let me convert it to NTFS and I would like to have this drive readable by windows.  NTFS is there but it won't let me click on it.  Why ?

---

### Post by haydnc on 2008-10-07
It has been a long time since I so much as looked at NTFS but I seem to recall you need to install some additional packages to get gparted working with NTFS.

I'd open up Synaptic Package Manager, search for gparted and see if, when you click on it, there are any 'recommended / suggested packages and any 'optional packages' you can install to go with it.

It wouldn't surprise me to find that one of them was necessary to let gparted do anything ntfs related.

---

### Post by gpsmikey on 2008-10-07
Hmmm -- I remember reading about someone else not able to select the NTFS format option but don't remember the post.  A couple of things to look at -- check out this post which sort of the same thing you are looking for I think: [http://ubuntuforums.org/showthread.php?t=917242](http://ubuntuforums.org/showthread.php?t=917242)

I was able to do basically whatever I wanted to various partitions using the GParted LIVE boot CD -- there was a new version released just recently - just grab the iso of that and burn a new CD - boot from that and it seems to have the extra stuff needed to talk to NTFS etc.  Version 0.3.9-4 -- you can get it from [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

mikey

---

