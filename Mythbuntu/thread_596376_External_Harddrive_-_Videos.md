---
title: "External Harddrive - Videos"
date: 2007-10-29
forum: Mythbuntu
---

### Post by kyfehr on 2007-10-29
I am running into an issue where mythtv can't see the external harddrive after restart.

I can go into media settings and direct the videos folder to my external harddrive at /media/USB-HDD/videos/ and then go to the video manager and find all the videos (go through the imdb tagging etc) and have no problem watching the videos. However, once I restart the computer, myth tv can not find the videos anymore and I need to remove the harddrive and replug it in for mythtv to find it. The harddrive is always accessible to the file manager through the desktop though and always maintains the same /media/USB-HDD/ location.

Any help would be great.

kyfehr

---

### Post by superm1 on 2007-10-29
> **kyfehr said:**
> I am running into an issue where mythtv can't see the external harddrive after restart.

I can go into media settings and direct the videos folder to my external harddrive at /media/USB-HDD/videos/ and then go to the video manager and find all the videos (go through the imdb tagging etc) and have no problem watching the videos. However, once I restart the computer, myth tv can not find the videos anymore and I need to remove the harddrive and replug it in for mythtv to find it. The harddrive is always accessible to the file manager through the desktop though and always maintains the same /media/USB-HDD/ location.

Any help would be great.

kyfehr
I would recommend making a symlink in your normal videos directory to this /media/USB-HDD location.  It would appear that it doesn't mount until the system is started up, causing the issues I believe.

---

### Post by kyfehr on 2007-10-30
how exactly do you setup a symlink?

---

### Post by superm1 on 2007-10-30
> **kyfehr said:**
> how exactly do you setup a symlink?

```
ln -s FROM TO
```

So lets say we have this structure:
```
:~/Software/iso_images$ ls
mythbuntu-7.10-i386.iso  ubuntu-7.04-desktop-i386.iso  ubuntu-7.10-desktop-i386.iso
```

We can do a symbolic link like this:
```
~$ ln -s  /home/supermario/Software/iso_images/mythbuntu-7.10-i386.iso /home/blah.iso
```

We do that and then look at ~

```
~$ ls -l ~ | grep *.iso
blah.iso 

```

---

### Post by srt4play on 2007-11-07
I ran into this problem tonight after adding a new 500GB usb drive.  A symlink won't fix it as the mountpoint /media/USB-HDD doesn't exist until you click on the volume in the left side of thunar.  I've played with the thunar preferences drive management and no luck.

---

### Post by srt4play on 2007-11-07
I worked around the problem by defining the drive in /etc/fstab, unchecking the option in thunar preferences to manage drives, and making a single line script with "mount /dev/sdb1" and set it to autostart through the xubuntu menu -> settings -> autostarted applications.

---

### Post by kyfehr on 2007-11-08
srt4play,

how did you edit the fstab.. I am not sure what info to put in there or how to find out the right info for my external drive.

Thanks.

---

### Post by srt4play on 2007-11-08
With the drive mounted (can see files on it in file manager), open a terminal and type:

```
mount
```

Look for the line referencing your usb drive, mine said:

```
/dev/sdb1 on /media/disk
```

Create a different mountpoint for the drive, not sure if you have to do this but I didn't want it to conflict with the automounting system, I made mine /video :

```
sudo mkdir /video
```

Edit /etc/fstab:

```
sudo nano /etc/fstab
```

Add this line at the bottom:

```
/dev/xxx#    /video    ext3    defaults,user,auto   0    0
```

Replace /dev/xxx# with the correct device name for your drive, and replace /video with whatever mountpoint you created for it. 

At this point I expected for everything to be ok after a reboot, but the drive still didn't automatically mount.  So I created a script on the desktop that contained this:

```
#!/bin/bash
mount /dev/sdb1
```

Then used the system settings menu to set it to execute on login.

---

