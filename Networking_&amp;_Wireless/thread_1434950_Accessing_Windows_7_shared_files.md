---
title: "Accessing Windows 7 shared files"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by Vi3GameHkr on 2010-03-20
Good evening,

I have two computers set up, one is running Ubuntu 9.04 and the other running Windows 7 Professional.  I have a bunch of shared files from Windows 7 (which I am normally able to access from any Windows 7 or Windows XP machine on my network) but I can't access them from Ubuntu.

I have tried going to Places > Network > Windows Network, but I receive the error "Unable to mount locations  Failed to retrieve share list from server"

I have also found another recommendation for accessing a windows server, via Places > Connect to Server, but I receive another error message there, "Cannot display location "smb://..."  No application is registered as handling this file."

Could anyone explain what my problem is and how I could fix it?  I really wish I could figure this stupid thing out myself, but it's linux.. it's not meant to be understood by anyone >.<

---

### Post by johnson.d on 2010-03-22
You can try mounting it through command which would give an error message which would help you troubleshoot further. You can use the following command to mount the Windows share using command line.

$ mount -t cifs //<Ip-address>/<Share-name> /<mount-path> -o user=<user-id>

---

### Post by garvinrick4 on 2010-03-22
> **Vi3GameHkr said:**
> Good evening,

I have two computers set up, one is running Ubuntu 9.04 and the other running Windows 7 Professional.  I have a bunch of shared files from Windows 7 (which I am normally able to access from any Windows 7 or Windows XP machine on my network) but I can't access them from Ubuntu.

I have tried going to Places > Network > Windows Network, but I receive the error "Unable to mount locations  Failed to retrieve share list from server"

I have also found another recommendation for accessing a windows server, via Places > Connect to Server, but I receive another error message there, "Cannot display location "smb://..."  No application is registered as handling this file."

Could anyone explain what my problem is and how I could fix it?  I really wish I could figure this stupid thing out myself, but it's linux.. it's not meant to be understood by anyone >.<Set up samba on your linux box so it can be added to the Windows
workgroup.

---

### Post by Vi3GameHkr on 2010-03-22
garvinrick4, I need to access the files from my windows machine on my linux machine, although I will keep that suggestion in mind.

johnson.d, I tried using
```
sudo mount -t ntfs //192.168.0.3/victorusb /victorusb -o user=Victor
``` and I got this:
> ntfs-3g: Failed to access volume '//192.168.0.3/victorusb': No such file or directory

---

### Post by johnson.d on 2010-03-23
The command " mount -t ntfs " is used to mount a local drive with ntfs file system
You need to use the option "mount -t cifs" mount a windows share.
Hence the command could be as follows:

$ mount -t cifs //<Ip-address>/<Share-name> /<mount-path> -o user=<user-id>

---

### Post by Vi3GameHkr on 2010-03-23
Ohh I gotcha. I thought I was supposed to change the cifs part because I was getting a different error when I used cifs.

> mount: cannot mount block device //192.168.0.3/victorusb read-onlyThat doesn't make any sense to me, because from Windows 7 or XP I don't have any read-only problems.

If it changes anything, the USB key I'm trying to share is FAT32 filesystem.

---

### Post by Vi3GameHkr on 2010-03-23
Would it be possible to use an FTP server to not only access my USB key from another computer on the network, but also, any day I accidentally forget it, I just need an internet connection to access any files I need.

Mainly, my question is, could I use an FTP server to host a certain folder on the USB key over a network? Or does it have to be internet?

---

### Post by garvinrick4 on 2010-03-24
> **Vi3GameHkr said:**
> garvinrick4, I need to access the files from my windows machine on my linux machine, although I will keep that suggestion in mind.

johnson.d, I tried using
```
sudo mount -t ntfs //192.168.0.3/victorusb /victorusb -o user=Victor
``` and I got this:I can access my windows from my linux box using the windows network, with
setting up Windows Workgroup and in Linux Samba. I can access all devices, printers, media anything really.

---

