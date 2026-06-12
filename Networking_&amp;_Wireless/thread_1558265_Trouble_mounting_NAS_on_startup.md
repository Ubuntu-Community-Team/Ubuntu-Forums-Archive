---
title: "Trouble mounting NAS on startup"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by LHC2009 on 2010-08-22
Hi everyone! ):PI'm quite new to linux and the forum here itself, but have heard great things about both of them.
I am having difficulties to mount my NAS (zyxel nsa210) on startup. After some online research, i stumbled upon the "solution". I was advised to write an entry into the fstab-file and that's what i did...my fstab-file now looks like this:
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=55e0d0a7-5766-4768-a2f4-9891de6d8e60 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=82ed01e3-3b4f-4241-bc93-7079ce073202 none            swap    sw              0       0
\\192.168.1.51\Tv-Shows /media/NAS smbfs credentials=/home/jan/.credentials
Later on in the tutorial i was advised to test it out by using the following command in the terminal:
sudo mount -a
And this actually worked like a charm and i was then able to find NAS in "Places". (Not on my desktop since i disabled it). BUT this works not after booting up...meaning there is nothing like NAS in "Places" and i have to mount it manually by using the "sudo mount -a"-command...there is nothing automatic about this solution...So now my question for everyone capable of answering me: "Where did i go wrong?" :D Thanks for all your efforts in advance. Best regards

P.S. Yes, i have installed smbfs and the folder where the NAS should be mounted in actually exists, so the usual suspects should be ruled out i guess ;-)

---

### Post by LHC2009 on 2010-08-23
Can't anyone help me? Please, I am kind of desperate since i tried everything i found online...

---

### Post by Iowan on 2010-08-23
**smbfs** is deprecated - use the **cifs** version - [this]("http://ubuntuforums.org/showthread.php?&t=283131") How-To has more information. :)

---

### Post by Gunman1982 on 2010-08-23
> **LHC2009 said:**
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0

# / was on /dev/sda1 during installation
UUID=55e0d0a7-5766-4768-a2f4-9891de6d8e60 /               ext4    errors=remount-ro 0       1

# swap was on /dev/sda5 during installation
UUID=82ed01e3-3b4f-4241-bc93-7079ce073202 none            swap    sw              0       0

\\192.168.1.51\Tv-Shows /media/NAS smbfs credentials=/home/jan/.credentials


Seems that the smbfs entry is lacking the '      0       0' at the end.

---

### Post by LHC2009 on 2010-08-24
Thanks for your answers...I've now switched from smbfs to cifs and adpated my version to the one posted in your tutorial. My fstab-file-entry now looks like this:
```
 \\192.168.1.51\Tv-Shows /media/NAS cifs users,auto,credentials=/home/jan/.credentials,noexec,noperm 0 0 
```But it still won't be mounted at startup...what am I missing? Thanks in advance...

---

### Post by Iowan on 2010-08-24
I'll admit I haven't tried fstab-mounting - but I notice the How-To uses forward-slashes instead of the backslashes in your entry.> //Server/share /mnt/samba cifs users,auto,credentials=/path/credentials_file,noexec,noperm 0 0 

---

### Post by LHC2009 on 2010-08-26
Hey Iowan! Thanks a lot for your help! You just solved my problem :) Thanks a lot! But now I'm wondering...why exactly did it work with the "sudo mount -a" command then? And what does the -a" stand for? Thanks again, you're my hero ;)

---

### Post by Iowan on 2010-08-26
From **man mount**:>  Options available for the mount command:
       ...
       -a     Mount all filesystems (of the given types) mentioned in fstab.Glad you got it straightened out!
Consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") :)

---

