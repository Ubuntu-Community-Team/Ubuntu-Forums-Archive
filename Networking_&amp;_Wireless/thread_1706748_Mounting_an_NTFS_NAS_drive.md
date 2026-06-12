---
title: "Mounting an NTFS NAS drive"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by smithcts on 2011-03-14
**Mounting an NTFS NAS drive** 
 
This is posted in Beginner Talk but it makes sense to see if anybody here has an idea.
I am attempting to mount and ultimately mount at login a 1TB Seagate GoFlex drive I use for backups. Following the advice given in this forum from the threads on how to fix windows share browsing issues and How to mount samba shares with utf8 encoding, I have managed to mount the drives by navigating to Home Folder/network. The drive appears there and I can mount any of the shares and read/write a file to the drive. I cannot mount it otherwise and really am at the point where I need to ask advice from those who actually know what they're doing. Even once I mount the drive through navigating the folders, it is invisible to any backup program I have installed and I cannot navigate to it from within the programs. I have attempted to manually copy files to the drive but that also failed due to timeout errors.
 
I would appreciate any sage advice an experienced user might be willing to offer. I'm a good learner.
 
Thanks,
Charlie

---

### Post by headvampyre@hotmail.co.uk on 2011-03-14
For the backup apps, instead of trying to find the drive through the Network directory(hopefully Gnome will fix this soon), just try typing this:

smb://NASDriveName/Backupshare

that should help :)

---

### Post by Morbius1 on 2011-03-14
> I have managed to mount the drives by navigating to Home Folder/network.  The drive appears there and I can mount any of the shares and  read/write a file to the drive. I cannot mount it otherwise and really  am at the point where I need to ask advice from those who actually know  what they're doing. Even once I mount the drive through navigating the  folders, it is invisible to any backup program I have installed and I  cannot navigate to it from within the programs.It's debatable if "I know what I'm doing" but from your description you are accessing the share through Nautilus. If so then you have a mount point at:
> /home/user-name/.gvfs/share-name on server-nameIt's a hidden directory ( because the developers are a cruel and heartless lot ) so you will have to enable the viewing of hidden files in both Nautilus and your applications to actually see it there.

---

### Post by smithcts on 2011-03-19
Sorry to be so late in replying but I've been travelling on business.  Thanks for the suggestions.  I'm using Back in Time and it does not (as far as I know how to operate it) permit you to type in the destination (snapshot) directory.  You have to browse to it.  And I can see the network share.  When I select it, it asks for the login/password.  But when I attempt to backup a file to it, it give me an error message saying the snapshot directory is not valid.

I can browse to the shares with Nautilus but it is not possible to manually mount the share.  Also, the /.gvfs subdirectory is empty.

Strange.  Obviously a lot I have to learn here about this OS.


Charlie

---

### Post by Morbius1 on 2011-03-19
If you connect to it in Nautilus and your ".gvfs" folder is empty then check to see if the following package is installed:
```
sudo apt-get install gvfs-fuse
```Then add yourself to the fuse group:
```
sudo gpasswd -a your_user_name fuse
```Then logout and login again to change your group membership.

---

### Post by smithcts on 2011-03-19
Thanks Morbius.  It shows up when mounted in Nautilus.  Sorry to say, that I really don't understand the significance of having a mount point.  Ultimately, I want to modify fstab to mount the drive automatically on boot. This seems a tall order of I cannot mount it manually.

But, I still consider this progress.


Charlie

Edit: Well, actually I got the mount point figured out since I discovered that Back in Time can see hidden directories and mount to the shares in them. Now all I need discover is why I keep getting a mount error 6 every time I try to manually mount the share.

---

### Post by smithcts on 2011-03-19
Another update.

I did get the share to mount manually.  Thanks to another thread, the problem was the share had spaces in its name and using \040 to separate them was the problem. I had to put quotes around the share.  When I did that, I could manually mount the share.  However, modifying /etc/fstab always resulted in an error.  So I found another thread suggesting putting the mount command into /etc/rc.local.  Worked fine.  I now have the drive mounted upon boot.

I will run the backup tonite to make sure it can write to the drive.  For now, call this one solved.

---

### Post by Morbius1 on 2011-03-20
I think I'm beginning to understand the problem here. You are using the term "manually mount" to actually mean "auto mount".

When you browse to the share in Network in Nautilus and connect to it you are manually mounting a remote share that will produce a mount point in a hidden directory.

What Nautilus is actually doing is using the following command to accomplish that:
```
gvfs-mount smb://server-name/share-name
```In your case since the share name has spaces in it it would be:
```
gvfs-mount smb://server-name/"share name"
```One quick way to automount the remote share assuming the "gvfs-mount" worked as expected was to add it to your start up applications:
System > Preferences > Start up Applications > Add > Command: gvfs-mount smb://server-name/"share name"

Although an easier method utilizing the same gvfs method underneath would be to use Gigolo to auto mount remote shares - [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

Then again maybe I still don't understand your use of the phrase "manually mount".

---

### Post by smithcts on 2011-03-21
Sorry for the confusion.  When I say manually mount, it means opening a terminal window and typing in the mount commands at the $ prompt.

Modifying rc.local seems to be connecting the share just fine and the backup programs can find it as well.  All is happiness.  Actually, only one glitch to fix and that's getting Evolution mail to keep asking me for my password an additional time.  I've seen some posts about it so I'm confident the fix is out there.

Thanks for the help and useful tips.

Charlie

---

### Post by jqdennis on 2011-05-25
Hi Gentlemen:

I too have a new GoFlex 1TB NAS drive.  Windows7 sees the network device (GOFLEX_HOME) and it's shares ("External Storage" is one), but I can't connect to this in Natty.

I can connect to Windows7 shares though.

What am I missing?

---

