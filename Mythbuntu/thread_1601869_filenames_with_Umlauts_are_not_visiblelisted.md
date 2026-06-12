---
title: "filenames with Umlauts are not visible/listed"
date: 2010-10-20
forum: Mythbuntu
---

### Post by MartinusEx on 2010-10-20
Hi out there,

I'm running mythbuntu 0.21 on Ubuntu 8.04.

I have several USB drives hooked to the pc which are automounted.
I regularily generate a txt file with a list of all the movies on the drives.
Since I'm German, some folders (the folder are named after the movies titles) contain german special characters (or french as well).

Sometimes those folders are listet, sometimes they aren't.
Not by ls and not seen by mini-dlna as well, which i use to distribute the movies over the local network.

I am not able to find out what the problem is.
I juggled with keyboard and language settings..
They are overwritten so it seems.

I set the keyboard settings to use the x config files. 
This worked for a while but now it is gone again and such 
folders do not appear although they are there (checked 
with a Lucid System, that has no problems with german umlauts)

I do not know how to proceed with this (out of ideas)

Any ideas available in the outer worlds here?
Thx a lot in advance.

Martin

---

### Post by andree_b on 2010-10-21
Any good reason not to upgrade to a more recent version?
 
If those files dont even show up with ls it is not a problem with the "myth" part of mythbuntu ;-) But i wonder if they dont show up at all or just with wrong character encodings?
 
Anyway you should probably force those disks to be mounted with utf8-encodings, see this thread [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

### Post by MartinusEx on 2010-10-23
Andree, thanks for your input:
> **andree_b said:**
> Any good reason not to upgrade to a more recent version?

I don't know a good reason against upgrading, but ususally i go for "do not touch a running system"
Simply: i fear that something might go hazardous wrong and I do not have the time to repair a broken update.
But probably I go for it since i do not have another clue. 

> **andree_b said:**
> If those files dont even show up with ls it is not a problem with the "myth" part of mythbuntu ;-) But i wonder if they dont show up at all or just with wrong character encodings?
 

Actually the situation is:
ls does not list file entries incorporating characters as ÄäÖöÜü?é etc. although the files are available.
Not even partially or with corrupted charakter encondings

When this occurs, a file with such a file name or a folder with such a name cannot be copied to the drive.

> **andree_b said:**
> Anyway you should probably force those disks to be mounted with utf8-encodings, see this thread [http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)
 
I could not follow this tutorial, it covers SMBFS realted solutions.


Any other ideas?

---

### Post by MartinusEx on 2010-10-24
Again hello,

i tried to change the fstab in a way i thougt might work, from what i read in the post andre linked here.

Since the drives are all ntfs and usb and this ist NOT a mythbuntu problem I move this to the global ubuntu forum.

<edit>
truly solved, have a look here
[http://ubuntuforums.org/showthread.php?t=1604553]("http://ubuntuforums.org/showthread.php?t=1604553")
</edit>

THX

martin

---

### Post by andree_b on 2010-10-25
Glad you solved the problem (solution  is setting the right locale before mounting) - just make sure mythbackend is not started before locale is set or mythvideo won't find your files with Umlauts even if they are accessable otherwise (this was a problem with mythbuntu 9.10 or 10.04).

---

