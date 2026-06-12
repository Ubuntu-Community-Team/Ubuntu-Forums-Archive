---
title: "Error copying - Unexpected SMB Signiture"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by QuinRiva on 2011-05-25
Whilst downloading files using SABnzbd, my terminal gets flooded with CIFS errors.  The *downloads* directory is a Windows shared directory, on the host computer.  The user has full read/write privileges via a Windows Domain account.  Write to the disk seems to work fine, and some files are written, but others aren't resulting in corrupted files. 


[IMG]http://i344.photobucket.com/albums/p348/QuinRiva/CIFSError.png[/IMG]

And fstab:
```
//pride/btadded /media/btadded cifs auto,iocharset=utf8,uid=xnet,gid=deus,credentials=/root/.cifscredentialsn,file_mode=0775,dir_mode=0775 0 0

//pride/btwatch /media/btwatch cifs auto,iocharset=utf8,uid=xnet,gid=deus,credentials=/root/.cifscredentialsn,file_mode=0775,dir_mode=0775 0 0

//pride/Deluge-Downloading /media/ddown cifs auto,iocharset=utf8,uid=xnet,gid=deus,credentials=/root/.cifscredentialsn,file_mode=0775,dir_mode=0775 0 0

//pride/SABnzbd-Downloading /media/sdown cifs auto,iocharset=utf8,uid=xnet,gid=deus,credentials=/root/.cifscredentialsn,file_mode=0775,dir_mode=0775 0 0

//pride/Transmission-Downloading /media/tdown cifs auto,iocharset=utf8,uid=xnet,gid=deus,credentials=/root/.cifscredentialsn,file_mode=0775,dir_mode=0775 0 0

//pride/Unsorted-TV /media/bttv cifs auto,iocharset=utf8,uid=xnet,gid=deus,credentials=/root/.cifscredentialsn,file_mode=0775,dir_mode=0775 0 0

//pride/Finished-Other /media/finish cifs auto,iocharset=utf8,uid=xnet,gid=deus,credentials=/root/.cifscredentialsn,file_mode=0775,dir_mode=0775 0 0
```

---

