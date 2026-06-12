---
title: "Can't log in!"
date: 2010-01-13
forum: Mythbuntu
---

### Post by jonno on 2010-01-13
I need some help. I applied some upgrades to my Mythbuntu 9.10 machine the other day and now I can't log in to the system. At the login prompt (which is supposed to be automatic) I get a message about the Gnome Power Management not being installed correctly or something. When I try to log in it just bumps me back to the login screen.

What can I do? Think I can log in to a terminal and correct the
problem? How do I do that? Any ideas appreciated.

---

### Post by hrobinson on 2010-01-13
Hi Jonno,

Yes, download putty from here:  _[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html")_

You need to know the IP address of the myttv box, and you can use only ssh (which is what this "terminal client" supports.

Use your local login ID and password that was set up when you first installed Mythbuntu.  the Root account will be in accessible as it does not have a password on it.  If you have no password on the account then just hit enter for the password.

Good Luck!

Sincerely,

Harold Robinson

---

### Post by jonno on 2010-01-13
Thanks for the suggestion but I tried to ssh in to the box and I can't connect. It's only connected via wireless. I guess I could move the box over to a wired connection if you think it's more likely that the wired connection would work.

---

### Post by hrobinson on 2010-01-13
Jonno,

Yes, use a wired connection for now.  IT is possible that the wireless connection is not up or connected to your network.

Sincerely,

Harold Robinson

---

### Post by jonno on 2010-01-13
Ok I managed to get to a terminal using Ctrl-Alt-F1 and after poking around a bit I think I found the problem. / on sda1 which is the boot partition is 100% full. I had seen a warning message when trying to upgrade about lack of disk space and I guess I breezed right by it somehow.
I've read on the forums about deleting old kernels but they all point me to Synaptic, which I can't use since I can't get X started.
Help?

---

### Post by hrobinson on 2010-01-14
Jonno,

Excellent since you now have a terminal.  This webpage will help you with how to remove those kernels from your system.  Hint before you look... What is the command line version for synaptic?  Give up... _**apt-get**_ is the command you use in a terminal to install and remove packages.  This article will help you surgically remove all unnecessary kernels.    As a matter of fact I only use the command line version, I think its much easier to work with, in my humble opinion.  : _[http://www.foogazi.com/2008/07/02/quickzi-how-to-remove-older-kernels-from-ubuntu/](http://www.foogazi.com/2008/07/02/quickzi-how-to-remove-older-kernels-from-ubuntu/)_ 

While we are on this subject.  I want to point out that when installing any linux system it is better to partition the disk into several sections.  For example:

/boot = 100mb
/root = 20gb (roots home directory)
/var = 40gb
/home = 40gb
/ = all the rest.

The reason for this partitioning scheme is simple, and would have avoided the problem you are having now.  by having 100mb allocated for the boot partition (yes its small but thats the way you really want it), it prevents the /boot folder from becoming too big.  Causing your root partition to fill up and causing corruption with the back end data base (if its on this particular system) because disk space ran out.

the nice thing about Unix is its ability to be really adaptible.  back when drives were only 10gb, I would partition the drive and if any one section filled up, it would not bring the whole system to its knees.

Personally for the back end I have a two drive system.  one small drive (60 gb) is just for the OS and the data base, properly partitioned to protect the back end.

The second drive (a 2TB drive) is dedicated strictly to the storing of recordings and videos.  The whole /var/mythtv directory is actually on that second drive.  and a mount statement mounts that drive into that directory.  If I want to add an additional drive because the other one is filling up.  Lets say  for example, the videos directory, I can install a new drive format it with the proper file system, mount it in a temporary area, copy the videos folder to the new drive, confirm that the copy was successful, delete all the files in the videos folder.  dismount the new drive and re-mount the new drive inside the videos directory and presto, I just expanded my mythtv box, all from the command line and Myttv is none the wiser.

Good luck in your repair.

Sincerely,

Harold Robinson

---

### Post by jonno on 2010-01-14
Thanks for that Harold.
I managed to get up and running last night. I did delete one kernel but now I don't think that was the problem so much. I'll post my db -Th output this evening if you would take a look at it. Right now my / is 12GB and has been reduced from 100% full to 84% full. According to Synaptic I only have 2 kernels installed so I think something else is the problem. When I installed I let Mythbuntu do the partitioning so I'm sort of clueless about how best to organize that. I do have /var/lib/mythtv mounted on a completely separate drive though.

---

### Post by hrobinson on 2010-01-14
jonno,

Yes, this sounds like a db corruption problem.

The way Mythbuntu auto partitions your hard drive, generally is as follows:

max memory size = size of swap partition
rest on / (known as root of the file system)

This is never the best way to do things as you can see from your problem, and as I have mentioned in previous posts.

are your symptoms the same as in the first post of this thread?

Do you have the following options available to you?

1.  Add a second drive to your backend.  12 gig remaining is not a whole lot of disk space and you will shortly run into this again.

2.  Rebuild your mythTv Box.

if you can do one or the other or both, then you could place the OS on the existing drive and your recordings on the other, and I can help you with that.

Sincerely,

Harold Robinson
Sincerely,

Harold Robinson

---

### Post by klc5555 on 2010-01-14
Deleted

---

### Post by jonno on 2010-01-14
sdb is a 320GB drive
sda is a 1TB drive which is connected in a rather unusual way. It sits in an external enclosure with its own power supply but is actually connected to the motherboard via a SATA to eSATA cable.
```
jonno@jonno-mythbuntu:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb1     ext3     12G  8.7G  1.8G  84% /
udev         tmpfs    989M  352K  989M   1% /dev
none         tmpfs    989M  4.0K  989M   1% /dev/shm
none         tmpfs    989M  340K  989M   1% /var/run
none         tmpfs    989M     0  989M   0% /var/lock
none         tmpfs    989M     0  989M   0% /lib/init/rw
/dev/sdb6      xfs    286G  199G   87G  70% /var/lib
/dev/sda1      xfs    932G  844G   88G  91% /var/lib/mythtv
```

---

