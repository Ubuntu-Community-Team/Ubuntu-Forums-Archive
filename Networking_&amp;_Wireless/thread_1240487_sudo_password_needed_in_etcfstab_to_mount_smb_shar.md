---
title: "sudo password needed in /etc/fstab to mount smb shares- how do I?"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by martydavis on 2009-08-14
I need to mount two Windows network shares after my wireless has connected.  I put the lines in my /etc/fstab but since the wireless isn't connected yet, they don't mount.

The lines are: 

sudo smbmount //myServerIP/directory-1 /directory-1 -o username=myloginid,password=mypassword 

sudo smbmount //myServerIP/directory-2 /directory-2 -o username=myloginid,password=mypassword

Problem is that sudo needs a password - my question is how do I get it passworded in there so it will run when I run: "sudo mount -a"

Better yet - how do I automatically mount my two Windows shares AFTER my wireless has connected?

I'm sure this has been addressed before, but I didn't know what to search for.  smbmount in the search didn't bring anything up that I could use.

---

### Post by Iowan on 2009-08-15
Dunno if it applies to wireless, but [here]("http://ubuntuforums.org/showthread.php?t=288534") is a How-To for mounting CIFS shares.

---

### Post by dmizer on 2009-08-15
/etc/fstab has permission to mount all file systems without needing "sudo". So, if 
```
sudo smbmount //myServerIP/directory-1 /directory-1 -o username=myloginid,password=mypassword 
```
works via the CLI, then
```
//myServerIP/directory-1 /directory-1 cifs username=myloginid,password=mypassword,file_mode=0777,dir_mode=0777 0 0
```
will work in fstab without having to enter a password.

---

### Post by martydavis on 2009-08-15
/etc/fstab doesn't work from the command line either with "sudo mount -a".  I get this error:

[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 18 in /etc/fstab is bad

my lines 16 and 18 are the lines in my first post.

When I copy each line separately to the command line and hit enter, it asks for my sudo password and then my shares mount without error.

---

### Post by ahood on 2009-08-15
> **martydavis said:**
> /etc/fstab doesn't work from the command line either with "sudo mount -a".  I get this error:

[mntent]: line 16 in /etc/fstab is bad
[mntent]: line 18 in /etc/fstab is bad

my lines 16 and 18 are the lines in my first post.

If lines 16 and 18 are...

sudo smbmount //myServerIP/directory-1 /directory-1 -o username=myloginid,password=mypassword

sudo smbmount //myServerIP/directory-2 /directory-2 -o username=myloginid,password=mypassword

Then, the syntax of these lines are incorrect for the /etc/fstab file.

The correct syntax is provided by dmizer in the previous post.

> //192.168.0.x/shared_directory_name /mnt/local_directory_name cifs username=myloginid,password=mypassword,file_mode=0777,dir_mode=0777 0 0

The local_directory_name must be created prior to adding the line to fstab. It can also be placed anywhere on the Ubuntu system.

I typically leave out the file_mode=0777,dir_mode=0777 option. 

> **martydavis said:**
> When I copy each line separately to the command line and hit enter, it asks for my sudo password and then my shares mount without error.

The lines that begin with 'sudo smbmount...' is the correct syntax for the CLI, thus, it works.

Hope this helps.

---

### Post by martydavis on 2009-08-17
Thanks dmizer and ahood - it works.  I believe when I tried it before I left the "sudo smbmount" at the beginning of the line in the /etc/fstab.  I took it out and changed the "-o" to "cifs" and it mounted with no errors.

Thanks again.

---

