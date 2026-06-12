---
title: "Unable to access windows shares."
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by elanning on 2008-12-09
Greetings,

First I will state what I am trying to do.  I have a windows file server, and I want to be able to read from and write to several shared folders on the windows box.  Now the details.

I currently have a desktop system running Windows XP w/SP3 and a laptop running Ubuntu 8.10 i386.  Both are connected to my home WiFi network.  The windows machine is simply a member of "WORKGROUP".  On the xp box, there are several folders shared out, nothing fancy at this point, just basic shares, set to enable anyone to read/write.  If I attempt to access these shares from another windows box, it works no problem.  

However when I go to "Places -> Network" on Ubuntu, I do see an icon labeled "Windows Network", clicking on that does indeed show an icon labeled "WORKGROUP" as would be expected.  Double clicking on that shows the windows box's name, but when I double click on that, it thinks about it for awhile, but then comes up with nothing.  No error message, but no shared folders either.

So it seems to be able to communicate right up until the point of actually showing me the shared folders!

The following are the packages that are installed when I searched synaptic on my machine if it helps:

smbclient
samba
libpam-smbpass
samba-common
libsmbclient

---

### Post by RomanIvanov on 2008-12-09
if you cant do it by UI, you shuld do it by commands, Example :
//192.168.0.100/ - Windows
romani - user on Ubuntu
/mnt/romanihome_share/MyDownloads - folder where you will have all windows folder stuff.

```
sudo mkdir -p /mnt/romanihome_share/MyDownloads
sudo mount -t cifs //192.168.0.100/MyDownloads /mnt/romanihome_share/MyDownloads -o username=romani,rw,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777

```

---

### Post by MockY on 2008-12-09
This has been broken since Gutsy. You have to manually connect to the shares.

One way of doing that would be Places - Connect To Server...  Select Windows Share and enter the appropriate information.

Or you could open nautilus by going to your home folder (or any other folder). Select Go - Location and type in smb://[IP address]/sharename

Or it can in rare cases be fixed following the following thread
[http://ubuntuforums.org/showpost.php?p=6204264&postcount=81](http://ubuntuforums.org/showpost.php?p=6204264&postcount=81)

---

