---
title: "Make home dir writable for mythtv user"
date: 2009-10-09
forum: Mythbuntu
---

### Post by 3gemail on 2009-10-09
I  Have installed Apple trailers from the menu, when I try to use it mythtv crashes and says:

mkdir: cannot create directory `.mythtv/mythstream/: No space left on device.

How Can I make the home dir writable?? I tried chown username:username, and chmod 777 neither work.

Thanks in advance.

-Gregg

---

### Post by tgm4883 on 2009-10-09
> **3gemail said:**
> I  Have installed Apple trailers from the menu, when I try to use it mythtv crashes and says:

mkdir: cannot create directory `.mythtv/mythstream/: No space left on device.

How Can I make the home dir writable?? I tried chown username:username, and chmod 777 neither work.

Thanks in advance.

-Gregg

Just out of curiosity, is there space left in /home?

what is the output of 

```
df -h
```

---

### Post by 3gemail on 2009-10-09
You are correct.  / is at 100%.  Strange that mythbuntu would do that on install.  There is an LVM volume that has 54 gig free according to gparted.  In order to manage it i will have to install lvm2.  Forgive my ignorance I am used to centos and fedora.  Is there any other way to move the home dir without repartitioning and moving it?

here is df -h 

[sudo] password for mythtvfamily: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  120K  1.6G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  140K  1.6G   1% /dev
tmpfs                 1.7G     0  1.7G   0% /dev/shm
lrm                   1.7G  2.2M  1.6G   1% /lib/modules/2.6.28-15-generic/volatile
overflow              1.0M   12K 1012K   2% /tmp

fdisk -l

/dev/sda1   *           1        7154    57463481    7  HPFS/NTFS
/dev/sda2            7481        7505      200812+  83  Linux
/dev/sda3            7506       14593    56934360   8e  Linux LVM
/dev/sda4            7155        7480     2618595    5  Extended
/dev/sda5            7155        7458     2441848+  83  Linux
/dev/sda6            7459        7480      176683+  82  Linux swap / Solaris

Thanks.

---

### Post by tgm4883 on 2009-10-09
> **3gemail said:**
> You are correct.  / is at 100%.  Strange that mythbuntu would do that on install.  There is an LVM volume that has 54 gig free according to gparted.  In order to manage it i will have to install lvm2.  Forgive my ignorance I am used to centos and fedora.  Is there any other way to move the home dir without repartitioning and moving it?

here is df -h 

[sudo] password for mythtvfamily: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.3G     0 100% /
tmpfs                 1.7G     0  1.7G   0% /lib/init/rw
varrun                1.7G  120K  1.6G   1% /var/run
varlock               1.7G     0  1.7G   0% /var/lock
udev                  1.7G  140K  1.6G   1% /dev
tmpfs                 1.7G     0  1.7G   0% /dev/shm
lrm                   1.7G  2.2M  1.6G   1% /lib/modules/2.6.28-15-generic/volatile
overflow              1.0M   12K 1012K   2% /tmp

fdisk -l

/dev/sda1   *           1        7154    57463481    7  HPFS/NTFS
/dev/sda2            7481        7505      200812+  83  Linux
/dev/sda3            7506       14593    56934360   8e  Linux LVM
/dev/sda4            7155        7480     2618595    5  Extended
/dev/sda5            7155        7458     2441848+  83  Linux
/dev/sda6            7459        7480      176683+  82  Linux swap / Solaris

Thanks.

2.3GB is pretty small to work with for a / partition

---

