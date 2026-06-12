---
title: "Installing using 2 hard drives"
date: 2011-01-10
forum: Mythbuntu
---

### Post by cander611 on 2011-01-10
When I first set up Mythbuntu I don't remember what version I had, but I had two hard drives and it installed the OS over both drives.  I'm trying to set up a new Mythbuntu backend using version 10.10 and there are two drives in the PC.  When I get to the partitioning screen in the installer it forces me to choose which hard drive I want to use.  It doesn't format both drives and combine the space like the older version did.  There is no data on the drives I want saved.  Am I not selected the correct options somewhere?  Do I have to manually format the drives with version 10.10?

---

### Post by davec99 on 2011-01-15
Now nobody make fun of me if this doesn't sound right - I'm trying to learn.  When I had 2 drives and one was fairly smallish, I would put (mount point) "/var/lib" on the second larger drive and "/ " on the smaller drive.  I have read more recently advice to put "/home" on the larger drive.  Possibly GParted or some related program allows for making one 'volume' out of 2 disks and showing it to the system as one large drive.  I do understand your question and realize you are wondering why this option is not offered in the setup.  Hope this helps or at least gets you on a path to success.

The reasoning with the choices, in case it isn't obvious, is that most of the added files will get saved within "/var/lib" or "/home" as you record and save video and other files.

A quick search I just did shows that these options and related issues have been discussed a bunch of times already, so the real question is most likely why there isn't a simple option for combining the two drives virtually to appear as one to the system.  I have been installing Mythbuntu (way too many times)for the past few years and don't recall seeing this as an option.

---

### Post by davec99 on 2011-01-15
Another one not to make fun of (please):  search "jbod" and "LVM" for some information on combining disks.   I guess this would get the best efficiency using automatic 'rollover' to the next disk as opposed to just mounting certain parts of the system on each disk.  I think you can even add to them later (possible only LVM).  Some forms of RAID will stripe to multiple disks, but you risk losing data more if there is a physical failure (apparently).

---

### Post by nickrout on 2011-01-16
Do not use LVM, if you lose one disk you lose the lot.

You can easily install to one disk and then add the other as a Storage Group. That's what storage groups are designed for.

---

### Post by blkbx on 2011-01-16
I've recently installed mythbuntu 10.10 frontend and a separate backend. I used a 8gig sd card for the front end and two one tb hard drives on the backend.  I wondered about how best to setup the two drive and used the advice that was someone posted to me about this query.
I partitioned the 1st drive with a 10gig / directory, the rest of the drive I partitioned /var/lib/mythtv. The secound drive was partitioned /var/lib/mythtv/recordings.
It's worked great for me

---

### Post by vidtek on 2011-01-17
> **davec99 said:**
> Now nobody make fun of me if this doesn't sound right - I'm trying to learn.  When I had 2 drives and one was fairly smallish, I would put (mount point) "/var/lib" on the second larger drive and "/ " on the smaller drive.  I have read more recently advice to put "/home" on the larger drive.  Possibly GParted or some related program allows for making one 'volume' out of 2 disks and showing it to the system as one large drive.  I do understand your question and realize you are wondering why this option is not offered in the setup.  Hope this helps or at least gets you on a path to success.

The reasoning with the choices, in case it isn't obvious, is that most of the added files will get saved within "/var/lib" or "/home" as you record and save video and other files.

A quick search I just did shows that these options and related issues have been discussed a bunch of times already, so the real question is most likely why there isn't a simple option for combining the two drives virtually to appear as one to the system.  I have been installing Mythbuntu (way too many times)for the past few years and don't recall seeing this as an option.

davec99 - You are absolutely spot on - the partitioning and boot choices presented with almost
all Linux distros are diabolical and very amateurish.  

I have found that using custom partitioning (with 3 hard drives and 10 partitions)and I changed anything with my choices, 
the partitioning in Ubuntu would suddenly revert the boot loader back to SDA1 every time, and if I forgot to change it back I would then have to do the Windows MBR thing 
with my 1st drive which is a real pain as I have Windows XP Media 2005 and W7 on that drive, so I have to do it twice!

Tony.

---

### Post by declanmullen on 2011-05-02
How do I install mythbuntu 11.04 (combined backend/frontend) with software RAID 1 on the root disks ?

Most modern Linux distributions allow one to setup software RAID 1 on the root file system's hard drives, but mythbuntu 11.04's installation GUI does seem to allow this option. 

For Ubuntu this can be achieved by using the Alternative installer CD [http://www.ubuntu.com/download/ubuntu/alternative-download]("http://www.ubuntu.com/download/ubuntu/alternative-download"). Is there an equivalent Alternative installer CD for Mythbuntu ?

---

### Post by declanmullen on 2011-05-03
> **declanmullen said:**
> How do I install mythbuntu 11.04 (combined backend/frontend) with software RAID 1 on the root disks ?

I've solved my issue by installing Xubuntu 11.04 via its Alternative CD and setup my RAID via its installer. And once installed then I added the Mythbuntu Control Centre from [http://mythbuntu.org/existing-ubuntu]("http://mythbuntu.org/existing-ubuntu")

---

