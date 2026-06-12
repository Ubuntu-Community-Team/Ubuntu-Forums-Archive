---
title: "change in harddrive naming sd*"
date: 2010-09-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kristian_gjengedal on 2010-09-25
i just upgraded to the maverick beta. and got a mount error on startup.

turns out my hdds had changed from sda-d to sde-h (yes i'm too lazy to get the UUIDs in fstab) meaning from sda1 to sde1 etc. fixed it in fstab but any specific reason why this happened?

---

### Post by MacUntu on 2010-09-25
Don't know why, but it happended to me too. Without my (empty) USB card reader plugged in, my HDD is sda, else it's sde. That's why we use UUIDs - never trust a /dev/sd* label.

---

### Post by lloyd_b on 2010-09-25
> **kristian_gjengedal said:**
> i just upgraded to the maverick beta. and got a mount error on startup.

turns out my hdds had changed from sda-d to sde-h (yes i'm too lazy to get the UUIDs in fstab) meaning from sda1 to sde1 etc. fixed it in fstab but any specific reason why this happened?

The main reason UUID's were added as a mount option was the fact that  unlike the old /dev/hda type entries, there is *no* guarantee that a given drive will remain at a given device name ("/dev/sda", etc) from reboot to reboot.  For example, having an external SATA drive connected at boot time can completely scramble your device names...

I'd strong recommend getting "unlazy" for a while and get those UUID's in fstab :)

Lloyd B.

---

### Post by VMC on 2010-09-25
I wonder if this is related. I have partitions labeled, and if I open one using Places, then mount display = "/media/labelname" Next boot it may change to something like "/media/labelname__" sometimes even "/media/labelname___". 

Must be where it keeps track of media mounts.

---

### Post by ronacc on 2010-09-25
thats why I use gparted to "label" my drives/partitions , it makes it easier to find them when things go amiss .

---

### Post by ibuclaw on 2010-09-25
> **ronacc said:**
> thats why I use gparted to "label" my drives/partitions , it makes it easier to find them when things go amiss .

You need not gparted [to rename partition labels]("https://help.ubuntu.com/community/RenameUSBDrive"). But yeah, it is generally a smart thing to do.

I wonder if you can mount partitions by using the /dev/disk/by-label/ path... ;)

---

### Post by 23dornot23d on 2010-09-25
I was a little bored and this seemed a good idea to re label some partitions ....

I did two as a test ..... and now cannot access them .....

Will have to work out why now .....

if it ain't broke you ain't tweaked it enough ..... now on another voyage of discovery.

( I just love Grub ...... I shouldn't say this - as its not always Grub that I have a problem with ....... ) ;)
Interesting ..... Grub is refusing to update now and hanging at ...... Grub.cfg

[COLOR=Red]Its due to a drive refusing to unmount now ..... it just hangs ..... so not really grub at
fault here ....... although it maybe should have a timeout and exit neatly .....
[/COLOR]**I hope its ok to ctrl-z out of this as its the only option I have ..... Hey ho ....**

a few little problems ....

Ok its booting again .... and un-mounting it refused the first couple of times to unmount .....

I have one OS refusing to boot now .... this may be unrelated .... but seems strange as the last thing
I did was to alter the labels ...... but its good to be able to see what is what now in the listing.

At Least 2 are labeled now anyway - ZORIN and ULTIMATE EDITION.

So to try a few more ...... I have 4 drives and now 4 fully working boot menus ..... and all will
probably need updating from the correct partitions that they were created with .... we will see .......

The labels seem to be ok .... now

---

### Post by seeker5528 on 2010-09-25
> **kristian_gjengedal said:**
> turns out my hdds had changed from sda-d to sde-h (yes i'm too lazy to get the UUIDs in fstab) meaning from sda1 to sde1 etc. fixed it in fstab but any specific reason why this happened?

Don't know about the why now, but as to why, my guess.....

Is your BIOS set up with USB having a higher boot priority than hard drives?

Later, Seeker

---

### Post by iClouseau88 on 2010-09-25
Yesterday when I re-installed Meerkat and had to use gparted to prepare the partitions, Ubuntu called the hard drive /dev/sda while gparted called it /dev/sdb.  This leads to a costly mistake where I installed Ubuntu into an existing openSUSE root partition.  Repairing one mistake in a multi-boot system leads to another mistake and I have not been able to boot into Meerkat!

---

### Post by sisco311 on 2010-09-25
I'm lazy too!!!


[http://en.wikipedia.org/wiki/Udev](http://en.wikipedia.org/wiki/Udev)
The Arch & Gentoo wiki pages are usually good:
[http://wiki.archlinux.org/index.php/Udev](http://wiki.archlinux.org/index.php/Udev)
[http://www.gentoo.org/doc/en/udev-guide.xml](http://www.gentoo.org/doc/en/udev-guide.xml)
and
[http://www.reactivated.net/writing_udev_rules.html](http://www.reactivated.net/writing_udev_rules.html)

---

### Post by seeker5528 on 2010-09-25
> **iClouseau88 said:**
> Yesterday when I re-installed Meerkat and had to use gparted to prepare the partitions, Ubuntu called the hard drive /dev/sda while gparted called it /dev/sdb.  This leads to a costly mistake where I installed Ubuntu into an existing openSUSE root partition.  Repairing one mistake in a multi-boot system leads to another mistake and I have not been able to boot into Meerkat!

I'm guessing from that that probably you ran gparted from something other than the Ubuntu installation disk? And probably you have mixed types of hard drives, SATA + PATA?

In the past typically whatever type of subsystem you are booting from those are the drives that would show up first. So if you had SATA and PATA hard drives and your CDROM drive was PATA, your PATA hard drives would be first then your SATA drives and if you were installing to a SATA hard drive and boot and booting from the MBR on the SATA drive then when you booted the installed system the SATA drives might be first.

Now in addition to allowing you to choose which subsystems have priority newer BIOSes typically let you specify hard disk priority, but instead of being a static setting they try to be clever and automatically adjust the priority depending on what drives you have connected at the time, so things get even more complicated since if you boot without the drive that had priority being connected then later reconnect the drive, it will then be last in the HDD boot priority list.

So you have mixing of SATA and PATA hard drives is potentially and issue, the way HDD boot priority is handled is potentially an issue, don't know how much extra confusion is created if you add USB connected drives into the mix.

Bottom line is, it is up to the user to make sure what order the hard drives are listed in is the same as what they were expecting.

There is work being on the other part of the equation, making sure things work as expected if the order while doing the installation is different than the order in the installed system.

When it comes to creating some predictability in the ordering of the detected hard drives when booted from the installation medium and by extension determining where GRUB should be installed by default that's not such an easy thing to solve.

As people dump their older PATA HDDs, that helps one aspect of the situation, but who knows what the next generation of "clever" BIOS crap is going to bring.

Later, Seeker

---

### Post by sisco311 on 2010-09-25
> **seeker5528 said:**
> I'm guessing from that that probably you ran gparted from something other than the Ubuntu installation disk? And probably you have mixed types of hard drives, SATA + PATA?

In the past typically whatever type of subsystem you are booting from those are the drives that would show up first. So if you had SATA and PATA hard drives and your CDROM drive was PATA, your PATA hard drives would be first then your SATA drives and if you were installing to a SATA hard drive and boot and booting from the MBR on the SATA drive then when you booted the installed system the SATA drives might be first.

Now in addition to allowing you to choose which subsystems have priority newer BIOSes typically let you specify hard disk priority, but instead of being a static setting they try to be clever and automatically adjust the priority depending on what drives you have connected at the time, so things get even more complicated since if you boot without the drive that had priority being connected then later reconnect the drive, it will then be last in the HDD boot priority list.

So you have mixing of SATA and PATA hard drives is potentially and issue, the way HDD boot priority is handled is potentially an issue, don't know how much extra confusion is created if you add USB connected drives into the mix.

Bottom line is, it is up to the user to make sure what order the hard drives are listed in is the same as what they were expecting.

There is work being on the other part of the equation, making sure things work as expected if the order while doing the installation is different than the order in the installed system.

When it comes to creating some predictability in the ordering of the detected hard drives when booted from the installation medium and by extension determining where GRUB should be installed by default that's not such an easy thing to solve.

As people dump their older PATA HDDs, that helps one aspect of the situation, but who knows what the next generation of "clever" BIOS crap is going to bring.

Later, Seeker

Well, that's only the BIOS part. Linux and/or udev doesn't really cares about the order or physical location of the mass storage devices. The first detected device becomes sda, the second one sdb and so on...

---

### Post by ronacc on 2010-09-25
> **sisco311 said:**
> Well, that's only the BIOS part. Linux and/or udev doesn't really cares about the order or physical location of the mass storage devices. The first detected device becomes sda, the second one sdb and so on...

Yes but it's damn confusing even for someone who isn't a newbe when grub , gparted , the bios and ubuntus partitioner all call the same damn drive something different ( HD1 , SDA , etc ) some constancy would be nice , that is exactly why I use a STANDALONE gparted to partition , label and format my drives , Ubiquity sometimes dont even call the same drive the same thing twice in a row .

edited to add : and UUID is NOT the answer because 1 it changes with each format and 2 is not visible to the partitioner so it is totally useless during install .

---

### Post by sisco311 on 2010-09-25
> **ronacc said:**
> Yes but it's damn confusing even for someone who isn't a newbe when grub , gparted , the bios and ubuntus partitioner all call the same damn drive something different ( HD1 , SDA , etc ) some constancy would be nice , that is exactly why I use a STANDALONE gparted to partition , label and format my drives , Ubiquity sometimes dont even call the same drive the same thing twice in a row .

edited to add : and UUID is NOT the answer because 1 it changes with each format and 2 is not visible to the partitioner so it is totally useless during install .

I agree, it's confusing, on the other hand (I'm very lazy & ) I can't think of any better solution. So until then. [noparse]..:)[/noparse]

---

### Post by iClouseau88 on 2010-09-25
Hello seeker 5528, sisco311 and ronacc,

I ran Gparted from KNOPPIX 6.2 Live CD in a SATA DVD drive.  My desktop PC only has SATA hard disks.  I wish the opensoftware or open source community establish some sort of convention or standard for naming drives, for example, just like the professional engineers societies do.

---

### Post by seeker5528 on 2010-09-25
> **sisco311 said:**
> Well, that's only the BIOS part. Linux and/or udev doesn't really cares about the order or physical location of the mass storage devices. The first detected device becomes sda, the second one sdb and so on...

The BIOS factors in because in some cases it affects what is detected first based on priority of what you are booting from.

By default the installer always installs GRUB to sda.

If you have a SATA and PATA hard drive, booting the installation from the SATA drive typically means SATA will get recognized first, since it is what is required to access your boot drive, making it sda.

Then if you boot from a PATA CDROM drive to do an installation, since it's the PATA stuff that is required to boot from the CD, PATA gets recognized first making your PATA HDD sda.

Then assuming you missed something during the installation and GRUB installed to sda, it's now on the wrong partition.

Assuming you then find out how to boot the live session and get grub on to the correct HDD without having to install again, you might find that it doesn't boot because it's looking for the boot stuff on sdb instead of sda.

Different situation.

You have all SATA drives, but you thought you would be clever and change the HDD priority so the second SATA drive is the boot drive. So your boot drive is sdb and you forgot to take that into account when doing the installation, so now GRUB is installed on the wrong drive.

Different situation.

You started with a single drive, but for whatever reason it was not attached to the first SATA port. You add a second drive and by luck of the draw it gets attached to the first SATA port, but since it is last in HDD boot priority, you don't see any issue with that right away.

You decide to do a new installation, you left unpartitioned space on the drive, so use automatic 'install to free space' option, not noticing your boot drive is sdb and your newer drive is sda. Grub installs to your newer drive instead of your boot drive.

Making it so GRUB can use UUIDs to find the boot partition, which has been some of the recent work on GRUB, gets rid of some problems, there was work on static device names of drives too, so that helps on an installed system where device names might randomly change from one boot to the next, but other problems are still going to be problems for the foreseeable future. 

How reliable the static device naming is from one kernel to another remains to be seen, when ethernet/wireless stuff started needing rules to keep their device names static they would still get renamed some times during upgrades.

Later, Seeker

---

### Post by seeker5528 on 2010-09-25
> **iClouseau88 said:**
> Hello seeker 5528, sisco311 and ronacc,

I ran Gparted from KNOPPIX 6.2 Live CD in a SATA DVD drive.  My desktop PC only has SATA hard disks.  I wish the opensoftware or open source community establish some sort of convention or standard for naming drives, for example, just like the professional engineers societies do.

Assuming the hard drives are all plugged into the same SATA controller, I've always had mine come up in the order of the SATA port they are connected to (SATA0=sda, SATA1=sdb or SATA0=sda, SATA1=no HDD, SATA2=sdb, etc....) so I don't know why they would change unless you have two different SATA controllers or there was some kind of timeout or other random glitch that caused the HDD that would normally be sda not to be recognized until later. Two different controllers are much more likely to be detected in a different order from one time to another than 2 hard drives on the same controller but I'm not going to claim that it doesn't happen.

Later, Seeker

---

### Post by ktp on 2010-09-25
> **VMC said:**
> I wonder if this is related. I have partitions labeled, and if I open one using Places, then mount display = "/media/labelname" Next boot it may change to something like "/media/labelname__" sometimes even "/media/labelname___". 

Must be where it keeps track of media mounts.

I had noticed the "__" being added when for some reason previous unmount had failed and left the mount folder around.  The UI did not show any error when unmounting, but I had noticed the previous mount folder was left around.  When trying to manually unmount/delete the folder, it gave some error like Disk busy or something (I don't remember the exact error message now since I have not seen this for while now).  If I removed the folder on after reboot, it would mount to correctly to correct folder.

---

### Post by VMC on 2010-09-25
> **ktp said:**
> I had noticed the "__" being added when for some reason previous unmount had failed and left the mount folder around.  The UI did not show any error when unmounting, but I had noticed the previous mount folder was left around.  When trying to manually unmount/delete the folder, it gave some error like Disk busy or something (I don't remember the exact error message now since I have not seen this for while now).  If I removed the folder on after reboot, it would mount to correctly to correct folder.

I just did a new install of Maverick and only left "/home" intact, and on first boot when I mounted another partition using Nautilus it showed up again with the "__" appended on the end.

I checked my home with a fine tooth comb, and couldn't find any reference.

Edit: Look what I found when I opened the media folder.

 I deleted all the references there and now when I mount any partition they appear in the media folder and go away once I unmount them. 

I was mistakenly thought that only "/home" folder was left intact once a fresh install was used.

Also the permissions were left in a strange state , now there not. I no longer have that bazaar "__" character.

---

