---
title: "mounting remote HD's"
date: 2006-05-14
forum: Networking &amp; Wireless
---

### Post by mosslack on 2006-05-14
I'm fairly new to Ubuntu, but I've been using Linux in general for several years.  I have a bunch of Mac's and PC's on a home network and they all get along pretty well for the most part.  My problem is that I cannot seem to mount the drives located on my file server in Ubuntu.  I can use the Connect To Server menu option to use them that way, but I want to put my usual commands in fstab so they are mounted each time I log in as read/write.  The drives I wish to mount are 4 large (50 Gb) SCSI units connected to a blue&white G3 Mac running OS X (10.3.9).  I run a program called Sharepoints on the Mac to allow the drives to be shared with Windows via Samba and I can connect to all my Windows PC's on the net just fine.  Of course I have no problem connecting to the other Mac's on the net as well.  I'm sure it's just an error in wording of my fstab command, but I'm at a loss to figure it out.  Here is the command I thought should have worked in fstab:

//192.168.0.106/D /home/doug/fs-x/D smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

I've tried switching the fs to hfsplus and that didn't help.  I also tried using the Mac name (fs-x) instead of the ip address.  I even tried it as /Volume/D instead of plain D as the drive name.  I'm open to any suggestions.  TIA

Just a message from Doug...

---

### Post by cgjones on 2006-05-14
You might want to do some research on NFS shares. I'm not too familar with Mac's, but with OS X, you might need to create a NFS share for the Linux boxes. Although I would think that Samba shares should work also.

---

### Post by mosslack on 2006-05-14
[QUOTE=cgjones]You might want to do some research on NFS shares. I'm not too familar with Mac's, but with OS X, you might need to create a NFS share for the Linux boxes. Although I would think that Samba shares should work also.[/QUOTE]

I wouldn't think that NFS has to be used as when I use the Connect To Server function the drives all mount as SMB shares.  I wouldn't even mind using them this way if I could write to them, but that is not allowed so I'm back to square one!

Doug

---

### Post by cgjones on 2006-05-14
Check out the man page for **mount**. It looks like the options need to be in a different format when mounting smbfs shares.

---

### Post by mosslack on 2006-05-14
I've already done that.  I just logged in under Fedora to see if I could accomplish anything here.  Sometimes the different distros are just different enough to make all the difference.  Thanks.

Doug

---

