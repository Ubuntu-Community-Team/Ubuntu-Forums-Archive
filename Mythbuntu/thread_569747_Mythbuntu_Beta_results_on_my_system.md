---
title: "Mythbuntu Beta results on my system"
date: 2007-10-07
forum: Mythbuntu
---

### Post by carlb on 2007-10-07
I installed Mythbuntu on my AMD 64 based system. I have had this system running Ubuntu and Mythtv so this system is a functioning PVR configuration.   Here are the results that I have observed:

1.  Wireless was detected but it is now showing three signal icons.  It did not connect automatically and required me to prompt to connect to the router.  After that three signal bar icons started showing up.  The connection does work.

2.  No sound.   Not sure why yet.

3.  Still no remote.  I tried to configure Mythbuntu to support a Soundgraph IMON knob (IR + remote) config.  The IR is connected via USB and is powered.  The LED flashes on the knob when a remote button is pressed but no actions occur.  I have never been able to activate this remote on previous system installs so I can't say I am surprised.  

My other observation is around the disk configuration.  I have a 500MB and 250MB drive in this system.  But I am never sure how to partition the disks correctly with the present installer to maximize the two disks in an Mythtv setup.

Hope this feedback is useful.

Carl

---

### Post by rusty0101 on 2007-10-07
If the 250 and 500 gig drives are both going to be dedicated entirely to mythtv, my own experiance or recommendation is to initially create a 20 to 50 gig partition that will be root, (/) and a second partition that will be for swap. usual practice is to set this up as 2 times the physical memory, however if you have 2 gig, you may wish to set it up with just an additional 2 gig. that's up to you.

Personally I would recommend setting that on the slower of the two hard drives. The reason for that is that I would expect that drive to give you greater reliability, which is good for a root file system

When I set mine up I used 100 gig for the root, but then I set up three 400 gig hard drives for the system, and had a little more to play around with in the drive. 

Going with a 20 gig partition will allow you to set up your system so that you can test, make a few recordings, see how they play, etc. You will also have space to try out some things in your hom directory later on if you would like, but that's not as important.

Once you have tested things to your satisfaction, install the lvm package. ('sudo apt-get install lvm2' if I recall correctly) and follow the appropriate instructions to build a file system on the remaining space on the drives. (which ever drive you set up as having your root partition you would like to have told gpartd to set up a remaining partion as an lvm type at that time, otherwise reformating may give you problems. You may be able to do that from a boot cd later on, have a look st the gparted drivezilla cd for one option. The general solution is to follow the instructions and build the lvm 'partition' out of the disk space you set asside, put a file system on it, (ext2, or ext3, others possibly) mount that to a temporary folder (/mnt/holding/) stop the back end for mythtv,  move all the folders and files from /var/lig/mythtv into /mnt/holding, unmount the /mnt/holding partition, and mount it to /var/lib/mythtv, then add the appropriate entries to /etc/fstab to make sure that the lvm partition gets mounted on reboot. restart mythbackend, and you should now have 600 or 650 gig of space to capture video to

There are othe rpossible solutions, involveing other tools. Some that are well documented, others that are not. I presume that someone else will pipe up with their preferred solution. It's one of the beauties of Linux, in that what works for me, may not work all that well for you, but who knows.

This is a fairly high level overview of the process the instructions and tools are out there in a few different wiki's and the like.

-Rusty

---

### Post by dannyboy79 on 2007-10-08
LVM is no longer required if you want to use Mythbuntu weekly builds from Trunk, it has Storage Groups available in it, You just tell it various mount points (can be different hard drives) and it uses them as one.

---

### Post by superm1 on 2007-10-08
> **dannyboy79 said:**
> LVM is no longer required if you want to use Mythbuntu weekly builds from Trunk, it has Storage Groups available in it, You just tell it various mount points (can be different hard drives) and it uses them as one.
This is entirely accurate, but please do take it with a grain of salt.  Even though these packages are very easy to install and upgrade to, we can't guarantee stability of them.

---

### Post by dannyboy79 on 2007-10-10
fair enough

---

