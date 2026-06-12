---
title: "Multiboot maverick with lucid and 7"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by romar_31 on 2010-09-09
before upgrading, i thought of testing maverick if it would run with no issues on my pc like graphics compatibility and etc. But the problem is will there be no problem booting it with lucid?  Or is there any geeky procedures will i have to follow in order to make it work?

---

### Post by uRock on 2010-09-09
If you install it by Lucid, then the Maverick grub will see your other installs and offer them.

---

### Post by boog321 on 2010-09-09
All you need is a free partition for / and you can share the swap with Lucid.

---

### Post by wilee-nilee on 2010-09-09
Here is my setup 2 primaries then a extended with Lucid and Maverick in logical partitions, one swap. You can have it in different orders but the extended is the key for as many logicals you can fit in there.
[ATTACH]169014[/ATTACH]

---

### Post by oldfred on 2010-09-10
I keep three partitions in rotation, last, current & next (beta). Each partition is 20-25GB with all my data mounted in a /data partition that I link into each with a small script I created from my list of history from the first time. I also create a list of installed applications and some configurations I do from command line and have converted that to another script to semi-automate the configuration of a new system.

---

### Post by uRock on 2010-09-10
> **oldfred said:**
> I keep three partitions in rotation, last, current & next (beta). Each partition is 20-25GB with all my data mounted in a /data partition that I link into each with a small script I created from my list of history from the first time. I also create a list of installed applications and some configurations I do from command line and have converted that to another script to semi-automate the configuration of a new system.
I am not yet on that level of IT geekiness, but I am getting there.:D [COLOR=Navy](Spoken with humor, not disrespect.)[/COLOR]

---

### Post by oldfred on 2010-09-10
I thought you wanted something nice & geeky.:)

But the issue is more with partition planning. It is often difficult to reorganize partitions after you have lots of data in them. I still have about 10% of my newest hard drive unallocated as I am not sure if I want more partitions or not.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by beew on 2010-09-10
> **romar_31 said:**
> before upgrading, i thought of testing maverick if it would run with no issues on my pc like graphics compatibility and etc. But the problem is will there be no problem booting it with lucid?  Or is there any geeky procedures will i have to follow in order to make it work?


If you just want to test it I think you may want to install Maverick on an external drive and plug it into your PC instead if you have an external hard drive or don't mind getting one,--it also works with usb flash drives but it will be slow.  By that I mean a full installation, not a live usb with persistence. That way you can test updating kernel or installing graphic drivers etc if things don't work out of the box. With live usb there is no way to update kernel and system wares.  

To make a full installation in an external drive you first create a live usb and then boot into it. Attach the external drive you want to install Maverick on and go through the usual installation, **except you choose install it in the external drive instead of the internal hard drive in the last step choose "advanced" and write the boot loader into the external device instead of the internal hard drive** (that would probably be sdc, sdb would be your life usb, but check to be sure, be careful or you will wipe out your internal drive) Some people would remove the internal drive first  but it is not necessary if you use the advanced setting in the last step and remember the name of your external device.

The "real" Maverick won't be released until October and I wouldn't be installing the beta in my hard drive.

---

### Post by wilee-nilee on 2010-09-10
> **beew said:**
> If you just want to test it I think you may want to install Maverick on an external drive and plug it into your PC instead if you have an external hard drive or don't mind getting one,--it also works with usb flash drives but it will be slow.  By that I mean a full installation, not a live usb with persistence. That way you can test updating kernel or installing graphic drivers etc if things don't work out of the box. With live usb there is no way to update kernel and system wares.  

To make a full installation in an external drive you first create a live usb and then boot into it. Attach the external drive you want to install Maverick on and go through the usual installation, **except you choose install it in the external drive instead of the internal hard drive in the last step choose "advanced" and write the boot loader into the external device instead of the internal hard drive** (that would probably be sdc, sdb would be your life usb, but check to be sure, be careful or you will wipe out your internal drive) Some people would remove the internal drive first  but it is not necessary if you use the advanced setting in the last step and remember the name of your external device.

The "real" Maverick won't be released until October and I wouldn't be installing the beta in my hard drive.

When you install Maverick the advanced button, for setting grub is in a different place and not called advanced anymore. It is now just under the partitioning setup area. You want grub only in the mbr of the HD you install to.

---

### Post by romar_31 on 2010-09-10
thanks for your reply and i have learned a lot :) But  have another problem, there's always an error while installing maverick from usb stick. I have tried wubi but it just stucks, the usb creator(provided inside the iso) but it also gives me squash errors and corrupted datas.

---

### Post by uRock on 2010-09-10
> **romar_31 said:**
> thanks for your reply and i have learned a lot :) But  have another problem, there's always an error while installing maverick from usb stick. I have tried wubi but it just stucks, the usb creator(provided inside the iso) but it also gives me squash errors and corrupted datas.
Wubi installs within Windows, not on thumb drives.

---

### Post by romar_31 on 2010-09-10
> **uRock said:**
> Wubi installs within Windows, not on thumb drives.

yah of course i know. i just said it for you to know and not recommending it anymore.

---

### Post by uRock on 2010-09-10
> **romar_31 said:**
> yah of course i know. i just said it for you to know and not recommending it anymore.
I'd never recommend Wubi. I always recommend installing in a virtual machine or putting it in a partition. ;P

PS, no offense to those who do.

---

### Post by romar_31 on 2010-09-10
> **uRock said:**
> I'd never recommend Wubi. I always recommend installing in a virtual machine or putting it in a partition. ;P

PS, no offense to those who do.
yeah right. haha. i'm currently redownloading another maverick iso file. for i have found out that md5sum hashes of my previous iso and the official one didn't much. maybe because of broken, and then resumed download process. wew. i have to wait for long again with 50kb/sec. speed. -.-

---

### Post by uRock on 2010-09-10
> **romar_31 said:**
> yeah right. haha. i'm currently redownloading another maverick iso file. for i have found out that md5sum hashes of my previous iso and the official one didn't much. maybe because of broken, and then resumed download process. wew. i have to wait for long again with 50kb/sec. speed. -.-
Ouch, that will take a while. You should sign up for the free disk when Maverick releases. Won't do you much good now, but it will be good to have a known good copy to fall back on in the future.

---

### Post by Sef on 2010-09-11
Moved to MMTnD.

---

### Post by romar_31 on 2010-09-11
> **uRock said:**
> Ouch, that will take a while.

i'm done. but md5sum mismatched again. trying again. -.-

---

### Post by uRock on 2010-09-12
Are you downloading from the ubuntu site or torrenting? Torrenting tends to pick up from disconnects a bit better, though I have had failures in the past.

---

### Post by romar_31 on 2010-09-12
> **uRock said:**
> Are you downloading from the ubuntu site or torrenting? Torrenting tends to pick up from disconnects a bit better, though I have had failures in the past.
i'll do it next time. i'll just wait for the final release. wew

---

### Post by kansasnoob on 2010-09-12
@romar_31,

If you're trying the daily build you might consider zsync:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

You could begin with the iso you have just make sure it's named appropriately: **maverick-desktop-i386.iso**

Then open the Terminal and "cd" to the directory where the .iso is eg: Desktop or Downloads, type **zsync**, back in Firefox right click the proper zsync link, select "copy link location" and then back in Terminal right click and paste the link.

Here's an example, note that my Downloads folder contains folders for various projects, ie: Ubuntu and Kubuntu, because the various *buntus often use the same iso-name, so I have to "cd" Downloads/Ubuntu:

> lance@lance-desktop:~$ cd Downloads/Ubuntu
lance@lance-desktop:~/Downloads/Ubuntu$ zsync [http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.iso.zsync)
#################### 100.0% 278.5 kBps DONE     

reading seed file maverick-desktop-i386.iso: ***************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read maverick-desktop-i386.iso. Target 90.6% complete.      
downloading from [http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.iso:](http://cdimage.ubuntu.com/daily-live/current/maverick-desktop-i386.iso:)
#################### 100.0% 513.0 kBps DONE     

verifying download...checksum matches OK
used 659587072 local, fetched 69076684


It even verifies the checksum, I still always double check the md5sum, but I've never had it fail :)

---

### Post by VMC on 2010-09-12
> **kansasnoob said:**
> @romar_31,

If you're trying the daily build you might consider zsync:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

You could begin with the iso you have just make sure it's named appropriately: **maverick-desktop-i386.iso**

Then open the Terminal and "cd" to the directory where the .iso is eg: Desktop or Downloads, type **zsync**, back in Firefox right click the proper zsync link, select "copy link location" and then back in Terminal right click and paste the link.

Here's an example, note that my Downloads folder contains folders for various projects, ie: Ubuntu and Kubuntu, because the various *buntus often use the same iso-name, so I have to "cd" Downloads/Ubuntu:



It even verifies the checksum, I still always double check the md5sum, but I've never had it fail :)
The name doesn't even matter if you use the "-i" option.

---

