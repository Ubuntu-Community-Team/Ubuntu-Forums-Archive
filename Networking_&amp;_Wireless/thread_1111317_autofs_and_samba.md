---
title: "autofs and samba"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by surfdoc on 2009-03-30
Hi,

I'm running intrepid and trying to mount some samba shares

I can mount them using 

```
sudo mount -t smbfs -o username=my_name,password=my_pass //lounge/documents /mnt
```

My /etc/auto.master has the line

```
/mnt /etc/auto.smb --timeout=60 --ghost
```

My /etc/auto.smb has the line

```
lounge -fstype=smbfs,username=my_name,password=my_pass ://lounge/documents
```

I run sudo /etc/init.d/autofs restart

ls /mnt/ returns nothing

/var/log/syslog has the lines

Mar 30 20:24:24 laptop automount[12749]: mount_autofs: already mounted 
Mar 30 20:24:24 laptop automount[12749]: /mnt: mount failed!  

After an few hours of googling and fiddling with the config files, I've come up blank.

Any ideas?

Cheers

Joe

---

### Post by bryanl on 2009-03-30
with autofs you usually have to address the desired share directly to see it. i.e. not "ls /mnt" but rather "ls /mnt/lounge"  (as I read your auto.smb the share mount name you are using is the server name but I may be confused)

it is a good idea to let autofs create its own mount directory and to not use a pre-existing directory.

The auto.smb that comes with the most recent version of autofs (just remove the comment marker and restart to activate it) will allow you to see the available shares when you "ls /smb/lounge" - makes it easy. The credentials file /etc/auto.smb.lounge is used if it exists. Make sure the samba-server (i.e. lounge) is in your hosts file to identify its IP address.

Use the cifs file system and not smbfs 

You may need a few mount options to get around permission headaches. nobrl, nounix, noperms, mapchars - check out man mount.cifs. In the auto.smb script, you can append these to the line that defines mountopts as "cifs"

---

### Post by surfdoc on 2009-03-30
Much thanks!

By changing the mount point to /mnt/network, the issue resolved. 

Although this is alluded to in many of the howtos out there, it wasn't that clear. The important point is that /mnt exists, but /mnt/network doesn't. On running /etc/init.d/autofs start, /mnt/network is created with each server is listed as a directory within.

I was aware of the scripted version of auto.smb, but over-wrote this with my more direct approach to try and fix the problem. I'll restore the backup of that file and try it out. This did bring up one interesting point - the config file approach that I'm using won't work if the auto.smb has executable permissions. Conversely, if auto.smb is a script, it must have executable permissions to work.

I left it set to smbfs and it worked fine. Is there any benefit changing it to cifs?

Having looked at the script I'm wondering how it knows what shares to mount. Does it detect them automatically?

Thanks Again

---

