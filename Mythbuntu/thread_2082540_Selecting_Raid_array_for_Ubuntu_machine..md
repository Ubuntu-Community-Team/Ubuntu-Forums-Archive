---
title: "Selecting Raid array for Ubuntu machine."
date: 2012-11-09
forum: Mythbuntu
---

### Post by BavidDowman on 2012-11-09
Hi, I am considering buying the following RAID Array for my storage needs:
[http://www.lacie.com/us/products/product.htm?id=10601](http://www.lacie.com/us/products/product.htm?id=10601)

Now I'll hook-up this array to my machine running Ubuntu 12.04, but I am not sure how RAID works in Ubuntu. Of course, the manufacturer's firmware is for Windows/Mac only. Will I be able to use the RAID from Ubuntu? I don't want the array to be reduced to individual drives, since I am paying for the cabinet and the RAID functionality.

Another question along the same lines: could it be better to just get a cabinet of disks and set software RAID on them?  What are the pros and cons of hardware-RAID vs. Software RAID?

Thanks for your time.

---

### Post by AlecJ on 2012-11-10
Can't see any Linux drivers for it yet, looks like it aimed at Mac,

Raid info here
[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by BavidDowman on 2012-11-11
Umm, it appears that most manufacturers do not provide dedicated linux drivers for their drives. 

Sorry if this sounds stupid, but is it a 'waste' to buy a drive with hardware raid and then reconfigure it in Ubuntu to use software RAID? That is, is Hardware RAID better in some ways? I doubt I can find a Drive with Linux support so was wondering if all these drives that support mac/pc will work at all with Ubuntu.

---

### Post by NewAmercnClasic on 2012-11-13
Why not build yourself a back-end raid solution?

---

### Post by madverb on 2012-11-13
I definitely wouldn't recommend that LaCie RAID device for use with Linux. If you are setting this up on a Desktop machine I would recommend you purchase a couple of HDDs, put them in and set them up in a software RAID mirror.
Hardware RAID is not better than software RAID. Often hardware RAID is fake RAID (using onboard fakeRAID chips) and this will be less efficient than a software RAID in Linux.
If you are looking for an external RAID solution for a laptop or similar I would recommend something like a Synology NAS that you can connect to a network and use iSCSI or similar.
P.S. Do NOT use RAID5

---

### Post by nickrout on 2012-11-13
> **NewAmercnClasic said:**
> Why not build yourself a back-end raid solution?There is little point in using raid with mythtv. Unless you value TV recordings very highly, the redundancy is unnecessary. Also any performance advantage is usually unnecessary.

Just buy lots of 3GB hard drives and use storage groups if you want to do it in the backend. If one dies, well it's only TV and you'll recover most of it.

---

### Post by BavidDowman on 2012-11-13
Thanks for you answers

Ok, I do not intend to store movies or anything. I have critical scientific data in rather large  (>2-3 GB) text files. I am the only one in my entire building who uses Ubuntu and the computer support of my organization refuses to help with anything that is not windows/mac (although they do it for clusters and servers so I don't quite get why). 

Disregarding for a while the fact that building an HDD array and setting up software RAID will be cheaper, can I just buy the LaCie product specified, format it with software RAID (I suppose I could use GParted to do that) and be good to go?  

Also, What's wrong with RAID 5?

---

### Post by nickrout on 2012-11-13
> **BavidDowman said:**
> Thanks for you answers

Ok, I do not intend to store movies or anything. I have critical scientific data in rather large  (>2-3 GB) text files. I am the only one in my entire building who uses Ubuntu and the computer support of my organization refuses to help with anything that is not windows/mac (although they do it for clusters and servers so I don't quite get why). 

Disregarding for a while the fact that building an HDD array and setting up software RAID will be cheaper, can I just buy the LaCie product specified, format it with software RAID (I suppose I could use GParted to do that) and be good to go?  

Also, What's wrong with RAID 5?I am not sure why you are asking in the mythbuntu forum then! Not that you are unwelcome here, but the participants tend to be focussed in a particular area :)

And sorry I don't know the answer to your questions. But there is at least one answer that says these devices aren't great with linux.

I also know that RAID does not equate to backup. I have been through a serious natural disaster and can tell you that the only good backup exists at least 100 miles from where you are, is automated, and doesn't rely on the trusted backup person picking up the backup drive on the way out of the building! Sure redundancy might lessen the chances of a single hard drive failure causing you to lose the data you have on it, but it is not everything proof by any stretch of the imagination.

Also I query the sense in scientific data in 2-3GB files. Lose one block of 512b/4k (depending on the disk) and you lose the whole 2-3G. Break it down into smaller files if you can. But I say that without knowing the parameters of your problem :)

You have a totally different problem than the average mythtv user. If I lose a 2-3GB file then it's probably something the children recorded, or last weeks news. I care slightly, but not much. You have the opposite situation!

---

### Post by BavidDowman on 2012-11-13
Oops, I am really sorry. I don't know how I ended up posting in this forum.. I meant to ask this in the main forum. I am sorry if I was rude, and thanks for the help anyway.

---

