---
title: "FSTAB help....."
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by Ckesey on 2011-01-26
I'm trying to mount windows shared network drive upon boot up.

I have put the string (//server/share    /mnt/dir   smbfs   username=user,password=xxx  0 0) in my /etc/fstab file but upon reboot it doesn't mount.

I can do a mount -a (after reboot) and it mounts correctly.

Any idea/suggestions what's going on here?

Thanks

---

### Post by Morbius1 on 2011-01-26
I'm surprised that smbfs still works as it has been replaced with cifs some years ago but if it works after a mount -a then the problem is a known bug. Under certain circumstances fstab is being executed before the network is up so one workaround is this:

Create a script with the "mount -a" command in it and place it in if-up.d:

Create a script:
```
gksu gedit /etc/network/if-up.d/fstab
```With this content:
```
#!/bin/sh
mount -a
```Save the file, exit gedit, and back in the terminal make the file executable:
```
sudo chmod +x /etc/network/if-up.d/fstab
```Anything placed in if-up.d will execute only after the network is up.

---

### Post by Ckesey on 2011-01-26
Thanks for the reply.

I tried the commands you listed. It will mount the drive if I disable the network and re-enable it but doesn't do it automatically upon reboot.

I can still sudo mount -a to establish the mount.

From your reply I'm thinking I should be using cifs.

I have tried a few commands in the fstab 

//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
however when trying to mount -a I get permission denied (error 13) with or without a nounix option. 

I have checked my /root/.smbcredentials file and all looks good there.[FONT=monospace]

[/FONT]

---

### Post by Morbius1 on 2011-01-26
> 
I tried the commands you listed. It will mount the drive if I disable  the network and re-enable it but doesn't do it automatically upon  reboot.

I can still sudo mount -a to establish the mount.I am truly sorry but I don't have a clue what's going on there.

The if-up.d script appears to be doing what it's supposed to do but for the life of me I don't know why it's not doing it at boot.

As a temporary ( or perhaps permanent ) workaround to this you might try Gigolo. It's a front end to gvfs-mount smb://.... so it places it's mount point in the .gvfs folder in your home directory but you can always symlink to someplace else. Gigolo Mini-Howto: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

---

### Post by Ckesey on 2011-01-27
I figured out what was going on with the if-up.d config......I didn't put sudo mount -a instead I left out the sudo......if I understand this correctly that something that has to be done by root.

Seems to be working correctly know.

I also checked out that program you recommended and it really takes the guess work out of mounting drives. Good recommendation. The only issue I had was it opened my drives as read-only. However It may be something I'm doing incorrectly. 

Thanks for all your help on this!

---

### Post by Morbius1 on 2011-01-27
> I figured out what was going on with the if-up.d config......I didn't  put sudo mount -a instead I left out the sudo......if I understand this  correctly that something that has to be done by root.
That's very odd since it's root that's running the script at that moment so a sudo is unnecessary.

Anyway it's good you found a way out of this.

---

