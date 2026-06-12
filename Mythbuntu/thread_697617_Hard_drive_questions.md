---
title: "Hard drive questions"
date: 2008-02-15
forum: Mythbuntu
---

### Post by Caps18 on 2008-02-15
It looks like I will be getting a new hard drive.  I am thinking of getting a 320GB or 500 GB 7200 rpm drive.  There is a possibility that the 5400 rpm one in the computer right now is what is causing some slow down with on-screen menus in MythTV, I don't know.  

Now the question is, how should I setup these hard drives?  I have a NTFS (160GB) one that I wouldn't trust 100% (I upgraded my external usb drive and use this as a second backup because it started to make some noise).    It does have some videos and mp3s on it, but I could transfer them over to the new drive.

What file system should I use?  I used xfs3 for the current 40GB drive that I tested things out with.  It seems to work.  I only worry that if I had to use it as an external hard drive for some reason, Windows wouldn't recognize it.  The only other option is FAT32.

The other question is would it be wise to use my current 40GB drive for the OS and Mythbuntu, and use the new hard drive as the place for all the media and Live TV stream?  Would the bus be able to handle two drives at the same speed of one drive?  What is the chance of a old hard drive failing if it is just running MythTV and not being used to write and read Live TV video and big files?  And would it take longer than the one hour to setup a new Mythbuntu install?  I would also know that the OS could load faster being on a 7200 rpm drive as well.

Any insight would be helpful, but I will probably go for the 500GB drive this weekend.  (Or do I need more space?)  How big of a drive are you guys using?

---

### Post by stevanbt on 2008-02-24
Hi,
Quote from [http://www.mythtv.org/docs/mythtv-HOWTO-3.html]("http://www.mythtv.org/docs/mythtv-HOWTO-3.html") [I]
MythTV creates large files, many in excess of 4GB. You must use a 64 or 128 bit filesystem. These will allow you to create large files. Filesystems known to have problems with large files are FAT (all versions), and ReiserFS (versions 3 and 4).[/I]

So it looks like FAT is out, see further down that page for recommended filesystems.

There are windows applications that will let you read a linux file system - have a google.  

It sounds like the best option would be to go for a new drive and not bother with any existing ones as they sound like they may be about to fail - but it's your call.

Our Myth box runs with 2 x 500 gig drives, but to be honest that's excessive - if we managed our recordings a little better we could easily survive on a single 500 gig drive... But we don't have any HD content!

Hope this helps, Steve.

---

### Post by Caps18 on 2008-02-25
I ended up splurging and got 1 750GB SATA drive (7200rpm) (and 3G PCI card).  It ruled out the hard drive as a slow down problem.  I recently found that my CPU was set to run at 1.2Ghz in the BIOS, but I now have a 2.0Ghz one, so that should solve any of my slow down issues.

I do have HD videos/TV shows, so I figure that I can get 100 hours of HD content on there now.  And if I ever got up to that much, it would either be time to clean up some stuff or buy a second hard drive.

---

### Post by newlinux on 2008-02-25
XFS or JFS would be best if the drive were linux only, but if you want to be able to attach the drive to a windows computer you might want to go with ext3 (you could use fs-driver in windows to access it). If you do go with ext3, I recommend you turn on the "delete files slowly" option on your backend (in mythtv-setup). I have 3 250 GB drives spread across 3 backends, and then another Terabyte for archived recordings, home-movies, music, archived movies, photos, etc.

---

### Post by Caps18 on 2008-02-26
I did a 10GB ext3 partition for the OS, 2GB swap, and a ~720GB JFS partition for the HDTV media.  I read someplace that JFS was better at handling large files.  

And I am slowly (read 1+ years) trying to get off Windows and move to Linux, so as long as I can network the computer, I'm not too concerned about which file system it has.

---

