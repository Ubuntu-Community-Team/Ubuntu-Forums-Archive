---
title: "Boot Camp In 10.4?"
date: 2007-12-13
forum: Mac OSX
---

### Post by Armman on 2007-12-13
I really don't want to upgrade to Mac OS X 10.5. I rather just wait till 10.6 comes out and stick with tiger. The only thing I really want in Leopard is Bootcamp. Is there anyway to get bootcamp for 10.4? Or install some other program that does the same?

---

### Post by Infinite Recursion on 2008-03-22
There is a command-line utility that is essentially Boot Camp's backend.  You can resize a partition using diskutil, for example:
```
sudo diskutil resizeVolume disk0s2 80G HFS+ NewPartition 20G
```
where: 
-disk0s2 is the disk identifier (you can find this by right- or ctrl-clicking on the volume in Disk Utility and selecting Information)
-80G is the desired size for the current partition (if you replace this with "limits" and ignore the rest of the command, it will print the resize limits of the selected volume)
-HFS+ is the new filesystem (You can also use MS-DOS if you want FAT32)
-NewPartition is the name given to the newly-created partition
-20G is the size of NewPartition

As always, when dealing with partitioning your computer, it is wise to back up your data in case of complications.  You can also do this using Disk Utility, but that would mean erasing the current partition.

---

### Post by metallicamaster3 on 2008-03-22
No, Boot Camp Beta for Tiger ended when leopard was released. You cannot have boot camp on Tiger anymore.

---

### Post by cprofitt on 2008-03-24
> **metallicamaster3 said:**
> No, Boot Camp Beta for Tiger ended when leopard was released. You cannot have boot camp on Tiger anymore.
 
Go ahead and grab [Virtual Box]("http://www.virtualbox.org/") for Mac OS X and be done with needing the vendor tie in product known as bootcamp. Just gotta love Apple... they 'use' their customers to 'beta' test a product and then rip it away from them.

---

### Post by 3rdalbum on 2008-03-25
> **PrivateVoid said:**
> Go ahead and grab [Virtual Box]("http://www.virtualbox.org/") for Mac OS X and be done with needing the vendor tie in product known as bootcamp. Just gotta love Apple... they 'use' their customers to 'beta' test a product and then rip it away from them.

Well, that's fairly standard practice.

BUT: Boot Camp isn't just a fancy partitioner; it adds a BIOS compatibility module to the EFI, that Apple removed from the EFI in the first place :-)

If the OP wants to do Windows-based gaming, Virtualbox will be useless. Boot Camp is not a virtualiser, it just sets up a dual-boot system where the other operating system runs natively. Operating systems installed within Virtualbox cannot access 3D acceleration, so they cannot do any 3D games.

---

### Post by cprofitt on 2008-03-26
> **3rdalbum said:**
> Well, that's fairly standard practice.
 
BUT: Boot Camp isn't just a fancy partitioner; it adds a BIOS compatibility module to the EFI, that Apple removed from the EFI in the first place :-)
 
If the OP wants to do Windows-based gaming, Virtualbox will be useless. Boot Camp is not a virtualiser, it just sets up a dual-boot system where the other operating system runs natively. Operating systems installed within Virtualbox cannot access 3D acceleration, so they cannot do any 3D games.
 
Well... I gues if you are a gamer you should skip buying gear from companies that cripple it in the first place.

---

