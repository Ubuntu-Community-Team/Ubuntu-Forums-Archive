---
title: "Can't Mount Data DVD's"
date: 2010-11-02
forum: Mythbuntu
---

### Post by grandpaken on 2010-11-02
I was backing up some of my video content to DVD's and found that although Brasero burned the disks fine I can not read them in Lucid.  I can take the same disk and read it fine on my Windows machine.  I can mount DVD's burned on my Windows machine in Lucid.  The drive is being accessed every few seconds like it can't determine what the disk is.  I tried one solution of uninstalling Brasero then reinstalling it along with Gnomebacker but a data disk I made in that program doesn't work either.  I could see an issue mounting the disk if they were toaster but since I can copy and play the disk content in Windows the disk should be good.  The drive, if it makes a difference, is a Sony SATA internal and usually mounts as
/dev/sr0. 

dmesg extract

54.581008] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  854.581014] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  854.581021] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  854.581034] end_request: I/O error, dev sr0, sector 0
[  854.582850] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  854.582855] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  854.582860] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  854.582867] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  854.582879] end_request: I/O error, dev sr0, sector 0

---

### Post by nickrout on 2010-11-02
> **grandpaken said:**
> I was backing up some of my video content to DVD's and found that although Brasero burned the disks fine I can not read them in Lucid.  I can take the same disk and read it fine on my Windows machine.  I can mount DVD's burned on my Windows machine in Lucid.  The drive is being accessed every few seconds like it can't determine what the disk is.  I tried one solution of uninstalling Brasero then reinstalling it along with Gnomebacker but a data disk I made in that program doesn't work either.  I could see an issue mounting the disk if they were toaster but since I can copy and play the disk content in Windows the disk should be good.  The drive, if it makes a difference, is a Sony SATA internal and usually mounts as
/dev/sr0. 

dmesg extract

54.581008] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  854.581014] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  854.581021] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  854.581034] end_request: I/O error, dev sr0, sector 0
[  854.582850] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  854.582855] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[  854.582860] sr 1:0:0:0: [sr0] Add. Sense: Logical block address out of range
[  854.582867] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 00 00 00 01 00
[  854.582879] end_request: I/O error, dev sr0, sector 0

googling the error messages you are getting offers a number of solutions, eg

[http://forums.fedoraforum.org/archive/index.php/t-238473.html](http://forums.fedoraforum.org/archive/index.php/t-238473.html)

I have always had good results from k3b.

---

### Post by grandpaken on 2010-11-02
> **nickrout said:**
> googling the error messages you are getting offers a number of solutions, eg

[http://forums.fedoraforum.org/archive/index.php/t-238473.html](http://forums.fedoraforum.org/archive/index.php/t-238473.html)

I have always had good results from k3b.

  I did spend a couple of hours on Google before posting here and found a few solutions but not much for Ubuntu...Fedora, OpenSuse etc.Tried most of them to no avail.  Searching on the error codes brings up mostly problems with not being able to burn a DVD which is not my problem.   I would think that if a drive loads and  burns the empty DVD using the default settings in the burning app that the same computer would be able to read the disks.  I also don't have any issues with playing commercial DVD's..just the data ones I make so it makes me believe that something is wrong in the formatting.  If I burn a data DVD on my windows box it works fine on this one.

---

### Post by nickrout on 2010-11-02
> **grandpaken said:**
> I did spend a couple of hours on Google before posting here and found a few solutions but not much for Ubuntu...Fedora, OpenSuse etc.Tried most of them to no avail.  Searching on the error codes brings up mostly problems with not being able to burn a DVD which is not my problem.   I would think that if a drive loads and  burns the empty DVD using the default settings in the burning app that the same computer would be able to read the disks.  I also don't have any issues with playing commercial DVD's..just the data ones I make so it makes me believe that something is wrong in the formatting.  If I burn a data DVD on my windows box it works fine on this one.

did you try either of the solutions i pointed to, which were:

1. try DAO instead of TAO; or

2. k3b

---

### Post by grandpaken on 2010-11-03
> **nickrout said:**
> did you try either of the solutions i pointed to, which were:

1. try DAO instead of TAO; or

2. k3b

  Yes, I tried K3b which, from my reading, defaults to DAO. I looked through the config and also viewed the .kde/share/config/ file to see if there was a DAO setting.  I also tried setting the disk to UDF with the same result but haven't checked that disk on my windows machine yet.  One other possible solution was to set the disk type to linux instead of linux/windows which is now running....same result.  Funny thing is K3b read and verified the disk as OK then when I ejected and reloaded the drive K3b says No Media. I just hooked up an external USB CDR/DVD drive to the same Linux box and it can read ALL the disks fine.  I guess the kernal doesn't like SATA data disks.

---

