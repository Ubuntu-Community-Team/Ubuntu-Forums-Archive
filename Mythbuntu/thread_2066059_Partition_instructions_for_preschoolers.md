---
title: "Partition instructions for preschoolers?"
date: 2012-10-03
forum: Mythbuntu
---

### Post by RTIInstaller on 2012-10-03
I am about to stick a gun in my ear over this, I have for hours been trying to figure out the how to partition a front end machine.

new 160 gig wd drive.  Ran through the basic set up and got the /dev/sda error so I read through the forums, everyone said do a manual partition so I did that with multiple partitions as instructed but am constantly confronted with a no root found error.  I am a wiz with mac and PC but this has got me stumped dead.

How the hell do you correctly partition a drive for mythbuntu?

---

### Post by RTIInstaller on 2012-10-03
> **RTIInstaller said:**
> I am about to stick a gun in my ear over this, I have for hours been trying to figure out the how to partition a front end machine.

new 160 gig wd drive.  Ran through the basic set up and got the /dev/sda error so I read through the forums, everyone said do a manual partition so I did that with multiple partitions as instructed but am constantly confronted with a no root found error.  I am a wiz with mac and PC but this has got me stumped dead.

How the hell do you correctly partition a drive for mythbuntu?


if someone could point me to a link on this site regarding basic partitioning that would also be super appreciated :)

---

### Post by tgm4883 on 2012-10-03
What /dev/sda error?

---

### Post by RTIInstaller on 2012-10-03
> **tgm4883 said:**
> What /dev/sda error?

When installing a fresh copy of mythbuntu the install progresses all the way up to where you select you time zone and then hangs with a banner that says /dev/sda error   "ignore, retry, cancel". I have 5 identical machines I will be using as front ends they all give the same error. I finally just got past this 15 minutes ago on one of the machines I have no idea why it finally worked this time. I am going to clone that drive to the other machines so I can hopefully avoid this problem with the remaining 4

Thank for the reply

---

### Post by oldfred on 2012-10-03
Some links, I always use gparted to partition and then use manual install to choose which partition is / (root), swap is normally found automatically if created in advance.

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by RTIInstaller on 2012-10-03
> **oldfred said:**
> Some links, I always use gparted to partition and then use manual install to choose which partition is / (root), swap is normally found automatically if created in advance.

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Thank you!

---

