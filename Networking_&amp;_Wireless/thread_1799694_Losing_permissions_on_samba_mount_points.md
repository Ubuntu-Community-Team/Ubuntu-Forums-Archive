---
title: "Losing permissions on samba mount points"
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by che_bizarro on 2011-07-08
Hi,
This problem is driving me nuts and I can't seem to solve it. I have an Ubuntu 11.04 laptop that I use to connect to a Windows 7 server. Everything was working fine until the hard drive on the server crashed and it was replaced with a backup. Now I intermittently lose access to the shares with Nautilus giving me the following message:

"The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of Folder"

When I look at the mount points in terminal I see the following:

drwxr-xr-x  5 root  root  4096 2011-07-08 13:12 .
drwxr-xr-x 23 root  root  4096 2011-05-03 11:17 ..
d?????????  ? ?     ?        ?                ? Folder

Where Folder is the mount point.

My fstab looks like this, although I must point out that I have tried virtually every possible permutation with no change.

//10.35.1.110/Share /media/Folder cifs rw,_netdev,iocharset=utf8,credentials=/root/smb/credentials,uid=1000,gid=1000,noperm,file_mode=0777,dir_mode=0777,sign 0 0

Sometimes the permissions will revert back by themselves, sometimes I need to umount and mount to get back in.

I have tried deleting and recreating the mount points. No change.

It is driving me up the wall, I have tried everything I can think of, installing/uninstalling winbind, the fuse modules etc etc.

Help!!! I use this machine as a production machine in a heterogeneous environment and everything works awesomely except for this. I love Ubuntu, I can't even think of booting Windoze these days but not being able to access the network shares is a right show-stopper for me.

---

### Post by capscrew on 2011-07-08
> **che_bizarro said:**
> Hi,
This problem is driving me nuts and I can't seem to solve it. I have an Ubuntu 11.04 laptop that I use to connect to a Windows 7 server. Everything was working fine until the hard drive on the server crashed and it was replaced with a backup. Now I intermittently lose access to the shares with Nautilus giving me the following message:

"The folder contents could not be displayed.
You do not have the permissions necessary to view the contents of Folder"

When I look at the mount points in terminal I see the following:

drwxr-xr-x  5 root  root  4096 2011-07-08 13:12 .
drwxr-xr-x 23 root  root  4096 2011-05-03 11:17 ..
d?????????  ? ?     ?        ?                ? Folder

Where Folder is the mount point.

My fstab looks like this, although I must point out that I have tried virtually every possible permutation with no change.

//10.35.1.110/Share /media/Folder cifs rw,_netdev,iocharset=utf8,credentials=/root/smb/credentials,uid=1000,gid=1000,noperm,file_mode=0777,dir_mode=0777,sign 0 0

Sometimes the permissions will revert back by themselves, sometimes I need to umount and mount to get back in.

I have tried deleting and recreating the mount points. No change.

It is driving me up the wall, I have tried everything I can think of, installing/uninstalling winbind, the fuse modules etc etc.

Help!!! I use this machine as a production machine in a heterogeneous environment and everything works awesomely except for this. I love Ubuntu, I can't even think of booting Windoze these days but not being able to access the network shares is a right show-stopper for me.

I believe that the problem is due to the Ubuntu client inability to  determine the UID/GID of the folder (the ??? indicate this).  This could be due to the SID changing on the Windows Server with the new disk. 

Did the disk hold the OS as well as the data?  Is the Ubuntu client part of an AD environment?  Why do you feel you need to run winbind on a Ubuntu client of a Windows server?  What fuse modules are you running?

I notice that you are mounting the share by IP address.  Can you mount the share by computer name (e.g. //server_name/share)?

---

### Post by dasan on 2011-07-08
First of all make sure that the IP address 10.35.1.110 for server is static

you can try to open it directly by 
press alt+F2 to open run then type
smb://10.35.1.110
see some thing is opening or not 

if not try to get the machine name and replace ip with name and try it.
names will work if it is under same gateway.

---

### Post by headvampyre@hotmail.co.uk on 2011-07-08
Why not install a WINS server on the 2003 server and a WINS client on ubuntu, that should help map the UID's, GID's, SID's, etc :) oh, btw:

apt-get install winbind

---

### Post by capscrew on 2011-07-08
> **headvampyre@hotmail.co.uk said:**
> Why not install a WINS server on the 2003 server and a WINS client on ubuntu, that should help map the UID's, GID's, SID's, etc :) oh, btw:

apt-get install winbind

I have to disagree here.  WINS has nothing to do with UID/GID's.  WINS maps IP addresses to COMPUTER NAMES (NetBIOS).

Winbind in this case is also not appropriate.  Although it maps UID/GID's it does this for a SAMBA server that is configured a a NT4 Domain PDC.

The OP is clearly using his Ubuntu host as a SMB client and therefore, most probably, only needs the SMB client.

---

### Post by che_bizarro on 2011-07-11
Hi,
Well, I tried deleting the secrets.tdb file, following on from the advice re: SID (yes, the server OS was on the same drive as the one which was replaced). This seemed to work but after an hour or so, the problem came back :-(
So I deleted the .tdb file and removed winbind and it now seems to be working!
I will need to let it run for a while before I mark it as solved but thanks for all the help, the Ubuntu community rocks!!

---

### Post by roberthanekom on 2011-07-11
I have a similar problem with external (usb) hard drive and memory sticks that I have to be root to copy / delete files.
I noticed this a couple of days ago for the first time.
This occurs on my desktop running on Ubuntu 10.10 not on a laptop running on 11.04.

---

### Post by capscrew on 2011-07-11
> **roberthanekom said:**
> I have a similar problem with external (usb) hard drive and memory sticks that I have to be root to copy / delete files.
I noticed this a couple of days ago for the first time.
This occurs on my desktop running on Ubuntu 10.10 not on a laptop running on 11.04.

What file system is the drive (partitions) formated as?  If you have not formatted it (them), then the most probable cause is that the format is vFAT or NTFS.  These file system formats are Windows based.  They don't use the same owner/group structure as Linux and therefore only root can read and write to the files and folders.

The symptoms may be the same as the OP, but the basic cause is very different.

---

### Post by roberthanekom on 2011-07-14
They are indeed windows-type (4GB of type "W95 FAT32(LBA)(0x0c)" and a 250GB of same type). But how is it that it worked for the past two years on this same PC and now not? And also working on the laptop that is also running Ubuntu? Doesn't make sense.

---

### Post by capscrew on 2011-07-14
> **roberthanekom said:**
> They are indeed windows-type (4GB of type "W95 FAT32(LBA)(0x0c)" and a 250GB of same type). But how is it that it worked for the past two years on this same PC and now not? And also working on the laptop that is also running Ubuntu? Doesn't make sense.

I can't tell you specifically what config changed.  What I can tell you is that the vFAT (any FAT file structure for that matter) has no concept or the user (owner) or group.  When Linux mounts the drive and can't determine the user/group (UID/GID) it makes root the owner.  This can be overridden to a specific user if you mount it from fstab, the command line or via a script. There are numerous threads at this forum on that subject.

So what happened to  your setup?  Who knows, but there is a method to overcome your problem.

I can't tell you what the config is on your laptop is so I can't comment on that either.

---

### Post by che_bizarro on 2011-07-19
So the problem continues only I have narrowed it down to whenever I save a file out of a program to the shared folder. This only seems to happen if I create a new file and not if I am saving an existing file. I thought it might have something to do with the file mask settings but changing them doesn't make any difference.
On the plus side, it doesn't seem to be happening at random, as it was doing before.
Does anybody have any thoughts on why this might be happening? I'm just about at the limit of my Linux/Samba knowledge.

---

### Post by capscrew on 2011-07-19
> **che_bizarro said:**
> So the problem continues only I have narrowed it down to whenever I save a file out of a program to the shared folder. This only seems to happen if I create a new file and not if I am saving an existing file. I thought it might have something to do with the file mask settings but changing them doesn't make any difference.
On the plus side, it doesn't seem to be happening at random, as it was doing before.
Does anybody have any thoughts on why this might be happening? I'm just about at the limit of my Linux/Samba knowledge.

What "program" behaves this way?

---

### Post by che_bizarro on 2011-07-21
OK, so I have tested all of the applications that I use on a daily basis, including Google Earth, Quantum GIS, Firefox, Inkscape, Gimp and Libreoffice and it appears to be completely random. There is no question that sometimes creating a new file using any of these programs on the network share causes the mount point to lose its permissions, but it is not reliably reproducible.
Grrrrr.
I'm a bit stumped here, I thought at first it might be related to Qt but it seems to happen with GTK+ apps as well.
Anybody?

---

### Post by capscrew on 2011-07-21
> **che_bizarro said:**
> OK, so I have tested all of the applications that I use on a daily basis, including Google Earth, Quantum GIS, Firefox, Inkscape, Gimp and Libreoffice and it appears to be completely random. There is no question that sometimes creating a new file using any of these programs on the network share causes the mount point to lose its permissions, but it is not reliably reproducible.
Grrrrr.
I'm a bit stumped here, I thought at first it might be related to Qt but it seems to happen with GTK+ apps as well.
Anybody?

For the longest time Open Office and GEdit have had problems with shares mounted at .gvfs (Nuatilus mount of the share).  I have one share from a Windows machine that I mount via a script for this very reason.  It seems that Gnome and Nautilus (which uses GTK) is not Samba aware.  i have no answers for you other than you are not alone.  :-(

---

### Post by che_bizarro on 2011-07-25
I did some more testing and it doesn't appear to be related to any  specific app, I tried unzipping files from the command line and the  result was the same :sad:  It seems to have something to do with the file creation. I have added  the right mask settings to my fstab file but that doesn't seem to make  any difference. The other annoying part is that it doesn't happen all  the time :confused:

---

### Post by capscrew on 2011-07-25
> **che_bizarro said:**
> I did some more testing and it doesn't appear to be related to any  specific app, I tried unzipping files from the command line and the  result was the same :sad:  It seems to have something to do with the file creation. I have added  the right mask settings to my fstab file but that doesn't seem to make  any difference. The other annoying part is that it doesn't happen all  the time :confused:

I thing we need to be more specific about this.  If you think this is permissions give me examples.  I think you are dealing with two problems here.  Using a file system that needs translating to Ubuntu (Linux) and Nautilus (GUI) interfaced Applications that assume the correct file system is there.

---

