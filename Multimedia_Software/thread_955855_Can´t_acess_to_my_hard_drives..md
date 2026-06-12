---
title: "Can´t acess to my hard drives."
date: 2008-10-22
forum: Multimedia Software
---

### Post by blackfury on 2008-10-22
Hi to everyone,

I´m have a problem.. I can´t acess to my Hard Drives from Ubuntu.
Here is what Ubuntu says: "Error org.freedesktop.DBus.Error.AccesDenied."
And I can´t launch any program.

Please help me.

---

### Post by cariboo on 2008-10-22
Please post the output of:

```
sudo fdisk -l
```

You will have to do this in a Applications-->Accessories-->Terminal. Paste the output in your next post.

Jim

---

### Post by cariboo on 2008-10-23
Highlight the output of the following command. In a Applications-->Accessories-->Terminal type:

```
sudo fdisk -l
```

Paste the output in your next post by either clicking the mouse wheel, or the left and right mouse buttons at the same time. The above command will list all the hard drives on your system. We need to see the listing in order to help you mount your drives.

The output form the above command should look something like this:

```
sudo fdisk -l
[sudo] password for jim: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x51b6cc16

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81920000    7  HPFS/NTFS
/dev/sda3           10200       30401   162272565    5  Extended
/dev/sda5           29697       30401     5662881   82  Linux swap / Solaris
/dev/sda6           12112       29696   141251481   83  Linux
/dev/sda7   *       10200       12111    15358077   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066acc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1912    15358108+  83  Linux
/dev/sdb2            1913       20023   145476607+  83  Linux
```

Jim

---

### Post by blackfury on 2008-10-23
```
sudo fdisk -l

Disk /dev/sda: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ce2250c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916   31455238+    7  HPFS/NTFS
/dev/sda2            3917        6682    22217895    7  HPFS/NTFS
/dev/sda3            6683       15017   66950887+    f  W95 Ext´d (LBA)
/dev/sda5           11295       15017    29904966    7  HPFS/NTFS
/dev/sda6            6683      110997   35479489+   83  Linux
/dev/sda7          111000       11294     1566306   82  Linux swap/Solaris

Partition table entries are not in disk order
```
Here it is the information...

---

### Post by cariboo on 2008-10-23
It looks like your problem is with hal, there was a bug in it, but is was fixed back in April. You could reinstall hal to see if that fixes the problem:

```
sudo apt-get reinstall hal
```

Give it a try and report back

Jim

---

### Post by blackfury on 2008-10-23
```
E: invalid operation reinstall
```

Its that says when i try to reinstall the hal....

BlackFury

---

### Post by cariboo on 2008-10-24
Try:

```
sudo apt-get --reinstall hal
```

Jim

---

### Post by blackfury on 2008-10-24
I think that the only solution is to delete and reinstall ubuntu...

```
E: invalid operation hal
```

Says that when I write ```
sudo apt-get --reinstall hal
```

---

### Post by cariboo on 2008-10-24
Can you go to System-->Administration-->Synaptic Package Manger and search for hal, once synaptic has found it right-click and mark for reinstallation?

Jim

---

### Post by blackfury on 2008-10-25
Wen I go to System-->Administration-->Synaptic Package Manger it says that tehre is a problem and to resplve it I must write manually... 
```
dpkg --configure -a
```

and don´t allows me to continue in the Synaptic Package Manger...
I go to the terminal and write the 
```
dpkg --configure -a
```

...but when I write that it says
```
dpkg:requested operation requires superuser privilege
```

BlackFury

---

### Post by vanadium on 2008-10-25
```
dpkg:requested operation requires superuser privilege
```
This means that you must precede the command with "sudo". "sudo" in fact mean: "do as super user".

```

sudo dpkg --configure -a

```

---

