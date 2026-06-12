---
title: "Samsung YP-T10 MP# Player in Ubuntu 8.04"
date: 2008-12-25
forum: Multimedia Software
---

### Post by don-robbery on 2008-12-25
After searching this morning finally found how to mount and use my mp3 player in Ubuntu Hardy Heron (gOS)

First run following commands

 sudo apt-get update &&  sudo apt-get install libmtp7 mtp-tools libtotem-plparser mtpfs

When this is done you open Rhythmbox, then go to "Edit > Pluginmodules" and check "Portable players - MTP".
Exit Rhythmbox, plug in your YP-T10 into your computer
and then start Rhythmbox. You should now see the T10 on the left side in Rhythmbox.

This will install the required libraries required to mount and browse mtp filesystems and supposable let rythymbox see the device (yet to get working)

Go to "System
> Administration > Users and groups" and add yourself to the group fuse.
Then log out and back in again. or execute following command;

sudo adduser <uid> fuse

using the following commands you can then mount the device to a location of your choosing.  I created a dir called t10 in my home directory

mtpfs ~/T10   // this will mount the filesystem
fusermount -u ~/T10    // this will umount the filesystem



I also created a script to make it a little easier for me, it checks for the device using lsusb and the device id, checks the dir for files and if non exist will mount the filesystem.  It will also in the event of not finding a usb device matching my samsung check the dir for files and umount if any exist.  This prevents conflicts when attempting a mount when if forgot to umount the device previously.

If you wish to use it first plug in your device and execute a 'lsusb' and then find something that looks like this;

donald@laptop:/var/log$ lsusb
Bus 002 Device 001: ID 0000:0000  
**Bus 001 Device 017: ID 04e8:508a Samsung Electronics Co., Ltd **
Bus 001 Device 004: ID 0951:1603 Kingston Technology 
Bus 001 Device 001: ID 0000:0000  
donald@laptop:/var/log$ 

take the setting simular to 04e8:508a (your maybe different) the key is to take the number sequence next to the line Samsung Electronics Co., Ltd

Then replace my one in the script below.  The script assumes you have created a dir called 't10' in your home directory.  feel free to modify as you like.  :)

Here it is for you all;


#!/bin/sh

## script for checking and mounting samsung t10 mp3 player
## to ~/t10

load='nautilus /home/donald/t10'
umount='fusermount -z -u /home/donald/t10'
mount='mtpfs /home/donald/t10'
ls=`ls /home/donald/t10 | wc -l`
search=`lsusb | grep 04e8:508a | wc -l`

if [ $search = "1" ]; then
        echo " "
        echo "samsung yp-t10 mp3player detected"
        echo "checking files in ~/t10"
        echo "...."

if [ $ls = "0" ]; then
        $mount
        echo " "
        echo "mounted yp-t10 mp3 player to ~/t10"
        echo "launching nautilus"
        $load

else
if [ $ls -gt "0" ]; then
        echo " "
        echo "mp3player already mounted"
        echo " "

fi
fi
fi


if [ $search = "0" ]; then
        echo " "
        echo "mp3 player not detected, checking ~/t10 for files"
        echo "......"

if [ $ls = "0" ]; then
        echo " "
        echo "no files detected"
        echo " "
else
        $umount
        echo " "
        echo "files detected, drive unmounted"
        echo " "
fi
fi
exit

Laters
Don

---

### Post by don-robbery on 2008-12-25
have found when deleting directories with a deep tree structure you first need to deleted the contained directories otherwise the player freezes requiring a manual umount with;

fusermount -u ~/t10
rm -r t10
mkdir t10

then a re-execute of the mount process to then get back into the device,


ie..

t10/Music/Foo Fighters contained a couple of directories with another directory in them,  this complex tree structure seems to be too much for the mtp libraries.  Delete em one by one, seems the limit is a tree of 2 deep.

---

### Post by Murdoc_of_puts on 2009-02-24
Hey thanks alot for this! I thought my hub was broken.  Works on 8.10 too just so you know.

---

### Post by notquitestr8t on 2009-08-27
Don, Maybe you can help. I posted my problem but no one is responding. Maybe I didn't explain myself. I used the T10 in Ubuntu 8.04. I bought a new hard drive and installed Jaunty amd64.
I did not run any scripts or install anything on Jaunty because the T10 was picked up and mounted as soon as I connected it. I am able to transfer new mp3's to the device. I am able to play from the device when connected to the usb port. However, when I go to the gym and turn on the MP3, only the only files I see are the ones I copied over before Juanty. None of the new ones appear in the playlist. Any ideas?
Thanks,
Chris

---

