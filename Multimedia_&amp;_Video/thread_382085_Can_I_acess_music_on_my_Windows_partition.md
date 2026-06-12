---
title: "Can I acess music on my Windows partition?"
date: 2007-03-11
forum: Multimedia &amp; Video
---

### Post by MiKe42 on 2007-03-11
I have my whole music library on the D: partition. I made 2 new ones for Ubuntu, one for Swap and one for Root. Can I use any music player on Ubuntu to acess that music?

---

### Post by jellyfisharepretty on 2007-03-11
Yes you can.  NTFS partitions (standard windows XP partitions) are readable in linux.  Try to go into the /media/ folder in linux.

There should be a folder similar to /hda2 (if your drive is IDE/PATA) or /sda2 (if your drive is SATA).

The number indicates the number of the partition.  If the partition D: is the third one on the drive you might get /hda3 or /sda3.

I'm sure there are other ways to access your windows drive, but that's how I do it !

PS.  If your windows drive isn't there you might have to edit your fstab.  However do not change it unless you know what you are doing.

---

### Post by MiKe42 on 2007-03-11
It isn't there.... Isn't there a way to do this? I can't work without music :guitar:

---

### Post by jellyfisharepretty on 2007-03-12
You can take a look here :

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only")

In the command line:

[FONT="Courier New"]sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab[/FONT]

Then append to the file:

[FONT="Courier New"]/dev/hda1    /media/windows ntfs  nls=utf8,umask=0222 0    0[/FONT]

In the example they give, they use partition hda1.  You drive D: might not be this.

1st you have to find out how your drive is identified.  If your drive is IDE it will be identified as hda, hdb, hdc , etc. depending on the numbers of drives you have.  If it's SATA it could be sda, sdb, ...

Then look (in windows if you want) at the partition D: .  What position is it on the drive ? Is it 1st, 2nd, 3rd, etc.

All you have to so then is append that number to the drive identifier.  For example if D: is the 2nd partition of the 1st IDE drive, then you get hda2.

Just remember to backup your fstab just in case it doesn't work.  You can then apply the changes by running

[FONT="Courier New"]sudo mount -a[/FONT]

PS Totally agree with you about working without music :guitar:

---

