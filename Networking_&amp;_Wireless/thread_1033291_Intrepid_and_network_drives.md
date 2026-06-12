---
title: "Intrepid and network drives"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by corblimey on 2009-01-07
I'm trying to access my Iomega Network Hard Drive through Samba to no avail.  This has been annoying me all morning, I've searched here and elsewhere and read thru threads like [http://ubuntuforums.org/showthread.php?t=964564&page=9](http://ubuntuforums.org/showthread.php?t=964564&page=9) all to no avail.  This was working in 804, but the closest I've got to getting it working was about 30 mins ago when the folder quickly flashed up on my desktop and then disappeared.

In Nautilus, typing smb://x.x.x.x/ gives me 0 items.  Typing smb://x.x.x.x/public gives me an error: failed to mount windows share.  I also get 'No application is registered as handling this file' from time to time.  I tried mounting in terminal 
```
sudo mount //x.x.x.x/public /home/user/Shared/ -o user=x,pass=x
```
and it just reverts to the prompt, but there's no files in home/user/Shared

and I've tried mounting in fstab
```
//x.x.x.x/public/ /home/user/Shared smbfs username=x,password=x,uid=1000
```

but 
```
sudo mount -a
```
then just appears to hang.  After asking for my sudo password, it goes to the next line and I have to ctrl+c to get out.

Ubuntu appears to see the drive.  Typing findsmb:
```
IP ADDR    Netbios Name   Workgroup
-----------------------------------
x.x.x.x    STORAGE-xxxx   [  WORKGROUP  ]

```
Any tips or advice would be much appreciated.  I only got this drive so I could easily transfer files to my media PC, if I can't access it thru Ubuntu, I might aswell revert to usb sticks, etc.

---

### Post by madmaxnj on 2009-01-11
I have the exact same problem.  Everything is the same... lock ups after asking for a password in a Terminal, the apparent connection and hard drive on my desktop only to disappear milliseconds later, every things the same.  I've also searched the forums and it pointed me to all the things we've both tried and failed.  I'll bookmark this page and check back to see if there is any progress.  If you figure it out, please post here for others to see.  Thanks.

---

### Post by madmaxnj on 2009-01-11
Okay, I figured out a way to connect to the iomega home network hard drive.  Like others that have posted I had many problems trying to connect to it through traditional methods.  But I found a way. 

First, login to the admin utility of the drive.  Enable FTP.  On the FTP page create a user account, and then give the user read/write privileges.  I also created a password since all the attempts I've tried to connect ask for a password, even when on the smb settings I didn't set one.

Now, go to Places-Connect to Server.  Select:
-FTP (with login)
-Server: your shared drives IP address
-Port:  default on iomega is 21
-folder:  default is public
-user name:  whatever you setup in the first step
-add a bookmark so you don't have to do this every time.  The bookmark will show up in your Places drop down.

When you connect it will ask for the password you created in the first step.

Now, I get an keyring error, which I just x out of and then get an error that it didn't connect, even though it did and I have the folder icon on my desktop.  Its not elegant, but it works.  Now if I can fix the keyring and somehow make this try to autoconnect on bootup I'll be all set.

---

