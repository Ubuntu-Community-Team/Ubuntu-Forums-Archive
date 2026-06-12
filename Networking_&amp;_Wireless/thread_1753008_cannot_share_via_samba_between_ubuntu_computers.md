---
title: "cannot share via samba between ubuntu computers"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by nethero on 2011-05-08
I have two Ubuntu 10.10 computers and two Windows XP computers connected to my network.  I cannot share files between the Ubuntu computers using samba.  I keep getting the "Unable to Mount Location Failed to mount Windows share" error.  I've tried the solutions [posted by dmizer]("http://ubuntuforums.org/showthread.php?t=1169149") here and nothing works.

Random true facts:

I can successfully connect to folders shared on my Windows XP computers from either windows computer.

I can successfully connect to folders shared on my Windows XP computers from either ubuntu computers.

Neither of my windows computers cannot connect to folders shared on either ubuntu computer.

Neither ubuntu computer can connect to folders shared by the other ubuntu computer.

I REALLY need to get samba to work since I have other Windows computers on my network.  It really is the best solution for me.  Any suggestions?  Thanks.

---

### Post by SteveDee on 2011-05-08
> **nethero said:**
> I have two Ubuntu 10.10 computers and two Windows XP computers connected to my network.  I cannot share files between the Ubuntu computers using samba.....

File sharing on 'buntu with Samba works very well. I don't know exactly how you have set your systems up, but it sounds like a file permissions problem.

When you create a file share using Samba (using the GUI interface) the share will still be blocked by Linux basic file permissions. So lets say you create a Samba share for:-
 /home/user/downloads
You must now allow read or read & write permissions for this folder by (say) selecting it in file manager and setting permissions.

I hope this helps.

---

### Post by Morbius1 on 2011-05-08
Please post the output of the following commands:
```
testparm -s
net usershare info --long
hostname
```

---

### Post by nethero on 2011-05-08
Here are the results of the commands you asked me to run.

```
$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers
``````
$ net usershare info --long
info_fn: file /var/lib/samba/usershares/transfer is not a well formed usershare file.
info_fn: Error was Path is not a directory.
[testshare]
path=/media/1TB_Volume/testShare
comment=
usershare_acl=Everyone:R,SOMEGUY\(null):F,
guest_ok=y
``````
$ hostname
someguy
```@SteveDee
I thought that I already did this when I shared the folder.  To share the folder, I right-clicked the folder, clicked on the share tab, and checked "Share this Folder", "Allow others to create and delete files in the folder", and "Guest Access (for people without a user account)"  Doesn't this add the permissions automatically?


EDIT:
If I right click the folder and uncheck "Guest Access (for people without a user account)" when I access the folder from an ubuntu computer it asks for the username and password.  I enter the username and password of the computer the folder is shared on and I can see the files.  However, I would like to use guest access.  How do I do this?

---

### Post by Morbius1 on 2011-05-08
> I thought that I already did this when I shared the folder.  To share  the folder, I right-clicked the folder, clicked on the share tab, and  checked "Share this Folder", "Allow others to create and delete files in  the folder", and "Guest Access (for people without a user account)"   Doesn't this add the permissions automatically?     It will and it works flawlessly if it's a Linux fileysytem.

Is /media/1TB_Volume/testShare formatted in NTFS or FAT32? If it is then it will try to change permissions but silently fail. There's an easy fix to this so let us know.

---

### Post by Morbius1 on 2011-05-08
Based on your last minute EDIT I'm almost certain this is a Linux permissions issue.

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add the following line to the [global] section of smb.conf:
```
force user = someguy
```Save smb.conf, exit gedit, and back in the terminal restart samba:
```
sudo service smbd restart
```Wait a few minutes ( not kidding ) for the network to settle down after a samba restart then set the share back to allow guests and give it a whirl.

The remote guest will be converted to "someguy" and at this moment "someguy" is the only one that can access the partition. It's either an ntfs partition that you are mounting through Nautilus or there is a bug in how nautilus-share is changing permissions on a linux filesystem.

---

### Post by nethero on 2011-05-08
I added the "force user" line and it worked!  Thanks for your help.  Yes, it is a FAT32 filesystem.  One more question...  

The force user converts the remote guest to someguy.  This is fine if I'm logged in on the someguy's account.  However if another user logs onto my ubuntu computer and shares a folder, their account name is different.  So would I have to redit the file to force user to their username?

---

### Post by Morbius1 on 2011-05-08
>  The force user converts the remote guest to someguy.  This is fine if  I'm logged in on the someguy's account.  However if another user logs  onto my ubuntu computer and shares a folder, their account name is  different.  So would I have to redit the file to force user to their  username?     Now you've got a problem. The force user thing works best with one machine - one user. Multiple users becomes an issue. Yes, you would have to change the user in "force user" every time the login user changes and that is not a workable plan.

From the server standpoint the easiest thing to do is to go back to making the share not accessible by guests and prompt the client for a username and password.

From the client standpoint if you want a guest accessible share you are going to have to abandon creating shares in Nautilus and use the classic method of sharing folders. In the classic method each share can have within it's definition a force user specific to that share.

And you going to have to settle on a more reliable way to mount that 1TB drive so that it mounts with the same owner or set of permissions every time you boot regardless of who boots. Hopefully this is an internal drive.

---

### Post by nethero on 2011-05-08
Thanks for the answer.  I think I'll stick with this method for now.

---

