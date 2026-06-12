---
title: "File sharing on a private LAN"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by ZLance on 2009-06-23
I have this issue. I am writing a networked computer science project and i am using 2 computers on a lan, like comp-router-comp. So I am doing all the work on one machine, and I often need to update the code on the other machine as well, but using email/usb drive is taking some time. So how do I set up something that can be seen on both machines. I read that setting up NFS server on one and mounting the stuff on the other could be a solution. Can someone give me a good walkthrough or an example?

---

### Post by blackxored on 2009-06-23
> 
1. NFS
2. Samba
3. VCS
4. SCP
5. FTP


You choose.

---

### Post by ZLance on 2009-06-23
Ok, what about NFS?

---

### Post by jonobr on 2009-06-23
Hello

And welcome to the forums


I would recommend using either samba
[Here is a quick quide to help you set it up]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")

Or you could use something like rsync.

Rsync will compare the differences between two directories and copy over the differences.
You could manually execute the copy or have it automated to run at certain times.
Rsync is also installed by default on your system.
It really depends what you want to and how you want to do it, but you have multiple options

Cheers

---

### Post by ZLance on 2009-06-23
Thanks, uhm, but isn't samba used mostly becuase it allowes for combined linux/windows filesharing? I use Ubuntu 9.04 on both machines. I know, i'm getting a little bit tedious here, could you shoot me a link for NSF walthrough too plz? Samba walkthrough makes a lot of sence btw, ty.

---

### Post by Iowan on 2009-06-23
[Here]("https://help.ubuntu.com/community/SettingUpNFSHowTo") is the NFS help page, and [here]("http://ubuntuforums.org/showthread.php?t=249889") is a simpler method.

---

### Post by lisati on 2009-06-23
Although it doesn't really matter too much (the choice is yours) I use samba because I have both Windows and Ubuntu on my home network. The tutorial I used as a starting point for getting things working can be found at [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by ZLance on 2009-06-23
Ok, so I have the nfs server running on one machine, and it is set to allow read/write to a given folder (/files) for the given ip adress. I have this problem on the client:

username@localhost:~$ sudo mount (server ip) :/files /files

then it freeses up a bit and gives out

mount.nfs: mount system call failed.

---

