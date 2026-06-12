---
title: "You don't have permission to access /mythweb/data/music/music"
date: 2007-11-06
forum: Mythbuntu
---

### Post by aidan_curtis on 2007-11-06
I have a problem accessing music or video files on mythweb of mythbuntu
while mythweb displays them in the listings if i click on one i get the following.
Forbidden
You don't have permission to access /mythweb/data/music/music/B-B- King/Blues (1960)/02 - Ruby Lee.mp3 on this server.


--------------------------------------------------------------------------------

Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6 Server at myb Port 80
I get something very similar for videos.
Help please.

---

### Post by uopjohnson on 2007-11-08
mythweb works through symbolic links and it doens't care what your setting are in the frontend.  You need to change the links for your music and recordings to pint to their actual location.

you can see if this is the problem be executing
```
 ls -l /var/www/mythweb/data

```
If you get ugly black boxes that point (->) to somewhere your music isn't then you need to relink them.
```

cd /var/www/mythweb/data/
rm music
ln -s /pathtomusic music

```

---

### Post by superm1 on 2007-11-10
Particularly, if you are using the default directory structure and these links are in the wrong place, this is a bug in mythbuntu.  If that's the case, please file a bug against mythweb.  Thanks :)

---

### Post by aidan_curtis on 2007-12-07
if i type 

 ln -s  /var/lib/mythtv/music music
this is the output
ln: creating symbolic link `music' to `/var/lib/mythtv/music': Permission denied
the directory permissions for 
/var/www/mythweb/data
are  root:root is the owner and
drwxr-xr-x  2 root root 4096 2007-12-07 15:09 data
does this seem correctand if it is this would suppose that one would need to use sudo commands to acheive the ln
am i correct?

---

### Post by uopjohnson on 2007-12-07
Yes.  Sorry.  sudo is required for the last step.

---

### Post by aidan_curtis on 2007-12-07
should the data data directory not allow www-data access to it either as group or user since ter apache server runs as www-data?

---

### Post by uopjohnson on 2007-12-07
I think the data directory is 775 so apache can read from it, but not write to it.  I may be wrong though.

---

### Post by aidan_curtis on 2007-12-07
thanks i think i have it

---

### Post by aidan_curtis on 2007-12-07
this is what i done to fix the permissions problems on the music folder

sudo chgrp www-data /usr/share/mythtv/mythweb/data
sudo chmod 775 /usr/share/mythtv/mythweb/data
sudo chmod +t /usr/share/mythtv/mythweb/data
(thanks gary)
sudo chown mythtv:mythtv /var/lib/mythtv
sudo chmod 775 /var/lib/mythtv
cd /var/lib/mythtv
sudo chown mythtv:mythtv *
sudo chmod 775
cd var/lib/mythtv/music
sudo chown -R mythtv:mythtv *
sudo chmod -R 775 * 
the -R's are to recurse trough files directorys etc
by the way one would probably have to do  something similar for videos

this assumes apache is web browser driving mythweb
www-data is the user apache is running under
mythbackend is running as mythtv
and that www-data is a member of the group mythtv
also this is a gutsy install with mythbuntu
i noticed the link to video in /usr/share/mythtv/mythweb/data was wrong 
it was pointing to /var/lib/mythtv/video not /var/lib/mythtv/videos which is the correct location
so 
cd /usr/share/mythtv/mythweb/data
sudo rm video
sudo ln -s  /var/lib/mythtv/videos video
sudo rm video_covers
sudo ln -s  /var/lib/mythtv/videos video_covers
the firstbit is thanks to gary parker
[http://www.parker1.co.uk/mythtv_0.20.php](http://www.parker1.co.uk/mythtv_0.20.php)
thanks gary
the rest was thinkering until i got it
hope this helps the next poor sucker
mind you i offer no guarantees as to the results of following this course of action

---

### Post by aidan_curtis on 2007-12-08
thanks to ye all for pointing me in the right direction and ive aslo mannaged to map directorys from an external usb Hard drive fat 32 format onto the various directories as follows.

To finish this out i needed to be able to mount a fat formated usb drive like so
 
drwxrwx--- 13 myuser mythtv 32768 1970-01-01 01:00 usb_disk

to do this add

#my usb disk
BUS=="usb", SYSFS{product}=="OneTouch", KERNEL=="sd??", NAME="usbdisk", GROUP="mythtv", MODE=="0660"


to to the top of

/etc/udev/rules.d/20-names.rules

and

/dev/usbdisk    /media/usb_disk  vfat  user,utf8,umask=007,uid=1000,gid=121   0   0
to

/etc/fstab

create a directory 

drwxrwxrwx 1 root root 32768 1970-01-01 01:00 usb_disk

the value of "XXXXXX" in
SYSFS{product}="XXXXXXXX" can be got by running

sudo fdisk -l

output
Disk /dev/hda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35633bda

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       36128   290198128+  83  Linux
/dev/hda2           36129       36481     2835472+   5  Extended
/dev/hda5           36129       36481     2835441   82  Linux swap / Solaris

Disk /dev/sda: 250.0 GB, 250058637312 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x20233cb3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001    c  W95 FAT32 (LBA)

noteing that the usb drive is /dev/sda 

then run

udevinfo -a -p $(udevinfo -q path -n /dev/sda)

output

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/block/sda':
    KERNEL=="sda"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{capability}=="12"
    ATTR{stat}=="   64227   135603   200298    48944        1        0        1        4        0    42264    48948"
    ATTR{size}=="488395776"
    ATTR{removable}=="0"
    ATTR{range}=="16"
    ATTR{dev}=="8:0"
    .
    .
    .
    .
    .
    .
    .


  looking at parent device '/devices/pci0000:00/0000:00:10.4/usb5/5-2':
    KERNELS=="5-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="S08BJ1PLA052"
    ATTRS{product}=="OneTouch"
    ATTRS{manufacturer}=="Maxtor"
    .
    .
    .


notice the line ATTRS{product}=
thats the value for SYSFS{product}

the last thing to ensure is that your volume manager 
is set to automount hotpluged devices


Thanks again for the help

---

### Post by aidan_curtis on 2007-12-10
one last thought
one does not need to use 775 in the lines below although this works, so does the slightly more restrictive 755 
its allows read access only to the group. 

sudo chown mythtv:mythtv /var/lib/mythtv
sudo chmod 775 /var/lib/mythtv
cd /var/lib/mythtv
sudo chown mythtv:mythtv *
sudo chmod 775
cd var/lib/mythtv/music
sudo chown -R mythtv:mythtv *
sudo chmod -R 775 * 
the -R's are to recurse trough files directorys etc
by the way one would probably have to do something similar for videos

---

