---
title: "HD clonning with dd"
date: 2008-10-22
forum: Maryland Team - US
---

### Post by mazato on 2008-10-22
Ok this is my setup
2 HDs with lots of space.
HD 1 have Ubuntu and XP. NTFS partitions, ext3, etc.
HD 2 is used for data for XP and Ubuntu

I want to store my HD image to a file. But, I don't want to have in my image the same free space that exits in my HD.
I know i can resize them before clonning them. 
What happens if I resize them then clone. What will happen whenI restore the image. I guess the other space will be unpartitioned?
Is there any other way to leave out all that free space in my HD.
Thanks!

---

### Post by C.S.Cameron on 2008-10-22
I have heard in these forums that partimage will leave out the free space, have not tried it myself yet.

---

### Post by caljohnsmith on 2008-10-22
If you really want to use the dd command, you could clone your HDD and pipe it to a zip file so that the free space will be compressed:
```
sudo dd if=/dev/[COLOR="Blue"]sda[/COLOR] bs=10M conv=notrunc | gzip -c > /media/sdb1/sda_image.gz
```
The above command will copy the entire sda drive and save it to a file "sda_image.gz" on the sdb1 partition if you first mount the sdb1 partition to /media/sdb1 (just an example). If you need more specifics, let me know, but I think the above command would work well to compress the HDD image.

---

### Post by mazato on 2008-10-24
caljohnsmith: I had already  had that in mind. But I dont understand the part that you said:"so that the free space will be compressed".
I know that the image will be compressed with gzip,but, what free space are you refering to?!
Also the bs operand, is that indicating the blocksize. 
I read the man but i cant get it yet!

---

### Post by caljohnsmith on 2008-10-24
> **mazato said:**
> caljohnsmith: I had already  had that in mind. But I dont understand the part that you said:"so that the free space will be compressed".
I know that the image will be compressed with gzip,but, what free space are you refering to?!
Also the bs operand, is that indicating the blocksize. 
I read the man but i cant get it yet!
All I was saying is that the entire HDD image will be compressed with gzip if you use the command I gave, so you can store the HDD image as a smaller file than the entire HDD size. But when you uncompress the HDD image and restore it to a HDD, the image will of course be the full size as the HDD you originally compressed. I don't know of any way to use dd to "leave out all the free space on my HDD" like you originally mentioned, unless the free space is unallocated space that is not part of the partitions. If that were the case, you could use dd to just copy the partitions and not copy the unallocated space. The only way I know of to "leave out the free space" in a partition would be to shrink the partition prior to cloning it with dd. 

And about the "bs" option with dd, it is basically how big of a chunk of data (block size) dd copies at one time before writing to its output file. "dd" normally defaults to a bs of only 512 bytes or one sector, so copying an entire HDD one sector at a time can  be really slow; that is why I used the "bs" option to specify a larger block size.

---

### Post by mazato on 2008-10-24
caljohnsmith:
Thanks a lot for explaining. I see everything clearly now!
I know what to do now!

---

### Post by tcpjack on 2009-04-20
Wow thanks.  A lot of useful information =)

---

### Post by dark_religion on 2009-11-13
Partimage should leave out the free space

---

### Post by Oceola on 2009-11-14
Cloning an image is OK but if you have more than one large drive why not set up a doppelganger?

I run two drives with two complete operating systems of the same version on each. When you boot or reboot you have the option of loading either one. One can be a complete or just a necessary version of the other one or a completely different version which you transmit important (same OS) file to or from.
This can usually be done by leap-frogging the versions of Ubuntu or XP/Windows. I don't dual boot Windows  and do this only with Ubuntu versions.

Only time it gets a little strange is when the secondary drive gets Grub updated and this update does not go to the primary. The primary drive Grub can be edited using gedit so the secondary drive loads the appropriate kernel. I've been doing this leap frogging since Breezy and it comes in handy.

As to general empty drive space, Linux as an OS does not have a defrag like some systems since most of the software is address specific and defrag could compromise the system. There was a defrag package in the repositories a few years ago but it never really seemed to work properly.

---

### Post by dokma on 2010-09-13
What I do is backup my dedicated web server to my home desktop PC using this dd trickery : [linux backup script]("http://www.docplanet.org/linux/backing-up-linux-web-server-live-via-ssh/"). You can modify this to backup one drive to the other during the night. I'm wondering is it possible to unmount the root partition, back it up and mount it again without booting a live CD. If not is it possible to have the machine boot it self automatically from a live CD, perform the backup and boot back to the OS all on autopilot. This way I would have a good backup of my machine every day when I wake up. Any ideas?

---

