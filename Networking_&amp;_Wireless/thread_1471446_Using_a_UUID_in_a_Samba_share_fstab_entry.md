---
title: "Using a UUID in a Samba share fstab entry"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by Tyler H on 2010-05-03
The system I'm working with is running 10.04 and I am running into problems mounting a Samba share.

The first problem I just solved. My drives kept switching names from sdb to sda and back. This isn't a big deal except it was causing errors on boot up when trying to mount my secondary drive which is also running a Samba share. I fixed this by listing the drives as their UUID's instead of paths'.

Now my issue is how to I right a path to a Samba cifs share with a UUID instead of a normal path entry.

---

### Post by dannyboy79 on 2010-05-03
HUH? don't know what you're asking. Please tell me exactly what you're trying to do.

fstab is used to permanently or auto-mount disks/shares. you would never have a UUID of a samba share within the your fstab. you would have an entry like this in your fstab if you're mounting the samba share from another computer within the computer that has the fstab.

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

if you're talking about sharing that drive that you just changed from /dev/sda to a UUID within your fstab, you still have the path to the folder you want to share defined in your smb.conf.

---

### Post by Tyler H on 2010-05-03
But my problem is the damn drives like to switch names. So what listed as the server and share in fstab could end up being the wrong name the next time I reboot.

Example:

I edit fstab to have the current path of my shared drive.
/dev/sda1         /media/Shared	ntfs-3g		0		2

But the next time I reboot the name of the partition changes from sda1 to sdb1. This is an issue since I'm aiming samba at //server/dev/sda1.

---

### Post by Morbius1 on 2010-05-03
You seem to have two very odd problems:

(1) Your sdxy designations change on every boot. Is this a raid or external USB device?

You could change the fstab line to point to a UUID or a LABEL. TO find out what those are run the following in a terminal:

**sudo blkid -c /dev/null**

(2) > This is an issue since I'm aiming samba at //server/dev/sda1.     I have no idea what that means. You can't access a remote share by using /dev/sdxy. /dev/sdxy is a device not a mount point or a share.

Please explain this one more.

---

### Post by dannyboy79 on 2010-05-03
> **Tyler H said:**
> But my problem is the damn drives like to switch names. So what listed as the server and share in fstab could end up being the wrong name the next time I reboot.

Example:

I edit fstab to have the current path of my shared drive.
/dev/sda1         /media/Shared	ntfs-3g		0		2

But the next time I reboot the name of the partition changes from sda1 to sdb1. This is an issue since I'm aiming samba at //server/dev/sda1.
OK, slow down. we're talking about the fstab located on the computer you want to MOUNT a network SMB/SAMBA share on correct?
if so, follow the link I provided to you earlier about mounting smb shares using CIFS.

---------------------------------------------------------

If you're talking about SHARING-OUT a folder to other computers via samba, then yes, you need to use the UUID of the partition or drive you want to share within your fstab and then the proper path in your smb.conf.

Example:
Here is my fstab line for the FAT32 share I want to SHARE-TO other windows computers on my network.

```
UUID=81B8-2F2C  /media/fat32    vfat    utf8,umask=000,gid=1000,uid=1000 0       1
```
so first I am mounting it via fstab on the SMB server (this drive is obviously installed in the same machine) using it's UUID  The following steps are what I did to figure out the UUID

Step 1
```
sudo fdisk -l
```
there are multiple drives and paritions in my output as I have 4 HDD's installed. I look for the HDD that says it's 300gb, it's currently mapped to /dev/sdc1 and it's formatted as W95 FAT32. 

Step 2
since I found it it's mapped to /dev/sdc1 THIS TIME, i do the following
```
ls -la /dev/disk/by-uuid/ | grep sdc1
```
it spits out the UUID of the partition, whic is 81B8-2F2C.

 I think there is an easier way to get the UUID but that's the way I know how to get it.                           
 
so the fstab will always mount the drive using it's UUID which DOESN'T between boot to /media/fat32, this is the share I have created in my smb.conf file.

some of this you won't need but this is what I use.

[fat32_movies]
path = /media/fat32/movies
comment = Movies on dell
available = yes
browsable = yes
read only = No
store dos attributes = Yes
create mask = 0755
directory mask = 0755
public = yes
writable = yes
guest ok = yes
force user = daniel
force group = daniel

so I am sharing out to other computer a sub-folder named movies on the /media/fat32 drive.

Get it now? If not, i have no idea what you're trying to do. I hope you're not trying to mount a smb share from one computer on another ubuntu machine using the first machines /dev/sdX location!!


also, you'll need to explain this a little better, "//server/dev/sda1"
because that doesn't make any sense to me and I have been using Ubuntu since 2005. Im not bragging and it's possible something has changed and I missed it, just saying.

---

### Post by dannyboy79 on 2010-05-03
> **Morbius1 said:**
> 
**sudo blkid -c /dev/null**


I was writing post #5 and you beat me to it. HA HA HA

P.S. there's that easier way of finding out the UUID I was talking about. hehe hehe

---

### Post by Tyler H on 2010-05-03
Ok sorry for the confusion if I'm not stating any of this clearly. I've been using the UUID's. The problem occurs when I use the UUID in the entry to my shared folder's fstab entry. After using the UUID for the 'file system' I save and : sudo mount -a which gives me this:

mount error: improperly formatted UNC name. UUID=0A1E762974845767 does not begin with \\ or //
No ip address specified and hostname not found

The entire reason I was trying to put this into fstab is because I was having trouble with my smb share mounting on boot.

---

### Post by Morbius1 on 2010-05-04
I admit that I am easily confused, so maybe the best way to resolve this problem is for you to provide us with some information.

On the server box that has the share you're trying to access, post the output of the following command: ```
cat /etc/fstab
```On the client box that has the line in fstab that is trying to mount the server share, post the output of the following command:```
 cat /etc/fstab
```

---

### Post by dannyboy79 on 2010-05-04
> **Tyler H said:**
> Ok sorry for the confusion if I'm not stating any of this clearly. I've been using the UUID's. The problem occurs when I use the UUID in the entry to my shared folder's fstab entry. After using the UUID for the 'file system' I save and : sudo mount -a which gives me this:

mount error: improperly formatted UNC name. UUID=0A1E762974845767 does not begin with \\ or //
No ip address specified and hostname not found

The entire reason I was trying to put this into fstab is because I was having trouble with my smb share mounting on boot.

again, i have to revert you back to my previous posts. I have no idea what you're trying to do, if you're fstab says you didn't provide a valid UUID then you must not have. please post the output of the commands I asked (example: ls -la /dev/disk/by-uuid/ | grep sdxX, and all the others) FROM BOTH THE smb server AS WELL as the client machine.

Im sorry to say but it sounds like you're trying to do something that is not preferred or even possible.

Also post what the other guy is asking for, your fstab's from both machines.

We can then begin to understand and help you.

---

