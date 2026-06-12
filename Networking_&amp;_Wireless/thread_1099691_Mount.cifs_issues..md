---
title: "Mount.cifs issues."
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by Arabica Bean on 2009-03-18
Hi. I'm running ubuntu 8.10 and in my office, we have an iomega network hard drive that is used for communal files. I have installed samba and smbfs on all the computers, and I can properly connect to the filestore via the network folder and the "Connect to server" method. I am looking for a way to mount this drive on a local folder, so that software that is installed can connect and interact with the folder. I am trying to use mount.cifs but to no avail... Here's my command.

```
sudo mount.cifs //filestore/public /media/FILESTORE/ -o guest
```

I have created the FILESTORE folder, and the network address is correct. The error that I receive is "Segmentation fault"
Can anybody help? The drive is not password protected, so the guest option is fine.

---

### Post by bryanl on 2009-03-18
segfault? I've hit just about everything else but not that one (yet).

try leaving the slash off the mount point. (i.e. "/media/FILESTORE" rather than "/media/FILESTORE/")

---

### Post by Arabica Bean on 2009-03-19
Funnily enough that got rid of segfault, but now I have a new error..

```
mount error: could not find target server. TCP name filestore/public not found
```

When I substitute filestore for the IP address (of which I can ping to)

```
sudo mount.cifs //192.168.1.1/public /media/FILESTORE -o guest
```
... I get SEGFAULT again! 

I'm at my wits end here... someone please help. Thank you.

---

### Post by capscrew on 2009-03-19
Try this:```
sudo mount -t cifs //192.168.1.1/public /media/FILESTORE -o guest
```

---

### Post by Flos Headford on 2009-11-28
I put username and password in /etc/cifspwd
then from this
sudo mount -t cifs //myservername/mywinShare /media/mountpoint -o exec,credentials=/etc/cifspw 0 0
I get the response one would expect from
mount --help

I've been trying to connect to a windows share for several months.
I've read loads of forum entries, followed lots of apparently well-informed advice, but still cannot obtain one of the advantages I have been told that Linux has - good networking.

---

### Post by capscrew on 2009-11-28
> **Flos Headford said:**
> I put username and password in /etc/cifspwd
then from this
sudo mount -t cifs //myservername/mywinShare /media/mountpoint -o exec,credentials=/etc/cifspw 0 0
I get the response one would expect from
mount --help

The above response shows that at least the system understands you want to mount a partition.  But you are not using the correct syntax.> 

I've been trying to connect to a windows share for several months.
I've read loads of forum entries, followed lots of apparently well-informed advice, but still cannot obtain one of the advantages I have been told that Linux has - good networking.

One big thing that isn't correct is the "0 0" at the end of your mount command.  This is only used in the /etc/fstab file.  See```
man fstab
```Look for the description of the sixth field (fs_passno).

The mount commands are not exactly the same in /etc/fstab.

For information about mounting the partition form the CLI see ```
man mount
```

For specific information about mounting a CIFS volume (partition) see ```
man mount.cifs
```

Dont get confused with the mount.cifs.  It is not used at the command line.  You are using the correct syntax with *mount -t cifs*.

This is how I mount a CIFS volume using a script```
sudo mount -t cifs //rincon/backup /smb/backup -o user=capscrew
```

What we have is the root mount of cifs on a host named //rincon/share at the mountpoit /smb/backup with the option (-o) of user=capscrew.  This will mount and I have to login to the share.  I would try this method first.  Once it works you can use the cred file.

---

