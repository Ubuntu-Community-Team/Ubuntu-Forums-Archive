---
title: "mounting hard drives"
date: 2008-06-27
forum: Mythbuntu
---

### Post by teddydov on 2008-06-27
Hello, 
This is actually 2 separate  but related issues:

1. the Hard drive that Mythbuntu is installed on is partitioned and I am not able to access the other part of the drive. (can't see it anywhere) 

2. I have a NAS and I wanted to know how I can mount it as well (so I can watch the media files I have located on it) 

thanks,

---

### Post by Joshua on 2008-06-27
> **teddydov said:**
> 1. the Hard drive that Mythbuntu is installed on is partitioned and I am not able to access the other part of the drive. (can't see it anywhere)

I think that if you do
```
sudo fdisk -l
```
you should see a list of your devices.  Maybe you can post the output of that command here.  If you aren't sure which device to choose someone here could probably help you figure it out.

Then, you can do ```
sudo mount *device* *location*
```
where *device* is the partition you want, like "/dev/hda2" and *location* is the directory where you want to access the files, like "/home/username/partitionfoldername"

In my Mythbuntu setup, I usually create a folder called mythtv in the /mnt directory and mount there.  Like this:
```
sudo mkdir /mnt/mythtv
sudo mount /dev/sda1 /mnt/mythtv
```

If you want it to mount automatically every time you boot, and you probably do if that's where your media files for MythTV are stored, you will have to edit your fstab file.  There is some detailed information [here]("http://ubuntuforums.org/showthread.php?t=283131").

> **teddydov said:**
> 2. I have a NAS and I wanted to know how I can mount it as well (so I can watch the media files I have located on it) 

There is a general guide to mounting networked storage [here]("http://ubuntuforums.org/showthread.php?t=280473").  This will basically involve installing the packages neccessary for "file sharing" like smbclient if using samba, and then editing your fstab file again so that the networked directories are automatically mounted at boot.

I think that once file sharing is set up in Mythbuntu you can mount things manually with
```
sudo mount *//network/location* */local/location* username=yournasname,password=yournaspassword
```
The network location will be something like //192.168.1.10/shared/directory/name and your local location will again be wherever you want to access the shared files like /mnt/mythtv or /home/username/sharedfiles.

---

