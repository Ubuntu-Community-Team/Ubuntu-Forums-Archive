---
title: "Backing up MP3 collection"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by neverett on 2007-05-16
Question: How do you back up your mp3 collection (be specific)?

I'm asking this partly because I'm wanting to back up my collection and partly because I'm curious.  Let me know how you do it!  It only takes a moment... Thanks for any input in advance!

Cheers!

---

### Post by earobinson on 2007-05-16
I copy my songs to my laptop ```
scp -r 192.168.1.100:/media/music .
``` Note I run this command from my laptop and both boxis have the same user name.

You could copy your music to another hd or computer.

---

### Post by stchman on 2007-05-16
> **neverett said:**
> Question: How do you back up your mp3 collection (be specific)?

I'm asking this partly because I'm wanting to back up my collection and partly because I'm curious.  Let me know how you do it!  It only takes a moment... Thanks for any input in advance!

Cheers!

How many .mp3 files do you have?  I MP3 my audio CDs (that I bought) and then archive them on  a data DVD using K3B.

---

### Post by neverett on 2007-05-16
> **stchman said:**
> How many .mp3 files do you have?

Maybe 6000 songs or so.

---

### Post by newlinux on 2007-05-16
I have about 80Gigs of mp3s. I use sbackup to schedule regular backups  (incremental and full) of the music, my archived dvds and other shows, pictures, and all other important data files. Before using sbackup I used to do all manual backups using grsync (a GUI frontend to rsync).

---

### Post by stchman on 2007-05-16
> **neverett said:**
> Maybe 6000 songs or so.

Holy $h|t, that is a lot of MP3s.  I have about 5 data DVDs full (~20G) so you will have about 20 data DVDs full.  Happy backups.

---

### Post by newlinux on 2007-05-16
Although I have around 80G  mine amount to about 11000 mp3s. I did a lot of mine at a lower bitrate than I use today. So for me that makes DVD backups a little tedious, so I use an external hard drive.

---

### Post by mohnkern on 2007-05-16
At 80 GB you definitely want to think about tape backup and tar -M  You should be able to pick up a DDS-4 tape relatively easily, and you'll fit it on 4 tapes.


You'd back up to tape with this:
mt -f /dev/st0 rewind
tar -czfM /dev/st0 <mp3 directory>

Oh and you can pick up a dds-4 USB tape drive for around $50 on Ebay if you look hard it should work pretty well.

---

### Post by dannyboy79 on 2007-05-16
why would you want to go the tape route. you can get a 500gb hard drive right now from tigerdirect for $99.00 after $40 rebate. add and external enclosure for another 20 or so and you've got 500gb of backup storage with a 5 year warrenty. Unless you're going to tell me that tape drives or whatever have a better warrenty than 5 years than I suppose you could maybe consider it but you won't get the that amount of storage. Also, since it's only a backup, you won't be writing to it all that often so it'll last a very long time!

---

### Post by newlinux on 2007-05-16
> **dannyboy79 said:**
> why would you want to go the tape route. you can get a 500gb hard drive right now from tigerdirect for $99.00 after $40 rebate. add and external enclosure for another 20 or so and you've got 500gb of backup storage with a 5 year warrenty. Unless you're going to tell me that tape drives or whatever have a better warrenty than 5 years than I suppose you could maybe consider it but you won't get the that amount of storage. Also, since it's only a backup, you won't be writing to it all that often so it'll last a very long time!

A 500GB drive with an enclosure is actually exactly what I did (cause if you count all the other things I backup I'm up to about 350GB and growing). Cost me about $130  a couple months ago. sbackup tars and gzips, I believe, but not a lot of savings with mp3s. I think this is much more useful than a tape. And yeah, in a few years (maybe sooner) I'll probably buy another larger drive and if this one is still working, I'll use it for some other use, like adding it to my fileserver.

---

### Post by mohnkern on 2007-05-16
You do have a point about just putting in a second drive.

I found dds-4 tapes for sale at $1 a piece (TDK's) so that's basically 500 GB for $12 compress or $24 uncompressed, and you've got the option of expanding in virtually any increment set you want.

If you get the tape drive itself for $50, you've got a significant savings, and greater expandability.

It does however, depend on your long term needs.

---

### Post by newlinux on 2007-05-16
> **mohnkern said:**
> You do have a point about just putting in a second drive.

I found dds-4 tapes for sale at $1 a piece (TDK's) so that's basically 500 GB for $12 compress or $24 uncompressed, and you've got the option of expanding in virtually any increment set you want.

If you get the tape drive itself for $50, you've got a significant savings, and greater expandability.

It does however, depend on your long term needs.

I think we've given the original poster some good options. :)

---

### Post by neverett on 2007-05-16
See the only thing is, I'm trying to back up my external hard drive.  I want it on something material that I can take off site so that if either my internal or external fail I have another to restore from.  I don't really want to spend the money right now for another external hard drive and I figured backing up to DVDs would be fairly easy (mostly because they are so inexpensive, not that the price has anything to do with ease).  I've tried using partimage, but I've been having some issues burning the DVD images.  See [this]("http://ubuntuforums.org/showthread.php?t=446002") thread.  Thanks for all of your input though, I did hear some good ideas!  Some that I'll probably use in the future for sure.

---

### Post by dannyboy79 on 2007-05-17
well if you have already used partimage to back it up and you have several images because you would have had to use the split option of it was larger than 4.3 gb, then just burn those images to dvd's. when you look at the file is it an image or is it a tar or gzipped file? can you open it with archiver and see the contents? also, when you insert the dvd, just because it doesn't automount doesn't mean that it's not mountable or that it didn't burn right. when you put in the dvd, what does

dmesg | tail

say? also, do you have an entry in your fstab for your cdrom or dvdrom? if not, you should add one. if all else fails just mount it yourself using this command

sudo mkdir /media/mp3backuptest
sudo mount /dev/hdb /media/mp3backuptest
(NOTE: you'll need to change hdb to whatever your cdrom or dvdrom that you put the disc in is. you can find that out normally by issuing one of these  commands and you should end up seeing your cdrom or dvdrom listed and what device it's being mapped to.

dmesg | grep D

dmesg | grep d

dmesg | grep c

dmesg | grep C

all the letters are just because I forget exactly whether I used DVD or Dvd or dvd along with the grep to see where my dvdrom was

---

### Post by neverett on 2007-05-17
> **dannyboy79 said:**
> well if you have already used partimage to back it up and you have several images because you would have had to use the split option of it was larger than 4.3 gb, then just burn those images to dvd's. when you look at the file is it an image or is it a tar or gzipped file? can you open it with archiver and see the contents?

I have 3 image files (music.000, m*.001, m*.002).  I used gzip compression.  No I can not see the contents.

My drive will not mount when the disc is in, however, I have not tried to mount using the command line.  I went into /media/cdrom0 to attempt to mount it that way.

Let me know what you think.  I really like partimage, but if I can't back it up to DVD then it serves me no purpose.  Thanks for any help in advance.  I'm going to recreate the images again with partimage and then see if I can get the DVDs to mount.

---

### Post by dannyboy79 on 2007-05-18
ok, it's because the partimage files are actually image files compressed so even if the archiver program showed you the contents of the compressed file, it still should only be a single image file. you should be able to mount it just liek you mount an iso file within linux. that command is this:

sudo mount -o loop -t iso9660 partimagefilenameandpath /media/folderyouwanttomountitto

otherwise I am not sure what image type part image is creating.

---

