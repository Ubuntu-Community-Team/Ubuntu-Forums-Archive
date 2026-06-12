---
title: "smb.conf help"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by Karakh on 2009-10-06
I installed Ubuntu server on an old box last weekend, and set it up as a deluged server. Worked much better than I expected, but when I tried to add an SMB shared folder, it just doesn't want to play.

I added several variations of this to my smb.conf. 

```
[torrents]
path = /home/karakh/torrents
   comment = WORK, YOU ****!
   public = yes
   only guest = yes
   writable = yes
   read only = no
   guest ok = yes
```

But when I mount it with cifs on my laptop, I don't have permission to create/delete anything, even though ls says that I own the files/folders and have rw permissions...

I've read all the official samba/SMB guides and can't work out what the problem is.

Any ideas?

(I know less than nothing about networking... When speaking to me, please imagine that you are talking to a 4 year old.)

---

### Post by bogdan.veringioiu on 2009-10-06
Hi.
On server, try to do this:
sudo chmod a+rwx /home/karakh/torrents

Bogdan

---

### Post by Karakh on 2009-10-06
It seems to help if I do a ```
sudo chmod -R a+rwx /home/karakh/torrents
```

I'm starting to think that the problem could lie in the command that I'm using to mount the share.

I'm having most success with:

```
sudo mount -t cifs //path/to/share temp/ -o nounix
```

Which is pretty much the command I use to mount my NAS. Is there a better way to mount a linux samba share?

---

### Post by Karakh on 2009-10-06
I have it semi-working with:

```
sudo mount -t cifs //192.168.1.101/torrents temp/ -o file_mode=0644,dir_mode=0755,guest,nounix,rw,uid='karakh',gui='karakh'
```

But there must be a better way than this.

---

### Post by bogdan.veringioiu on 2009-10-06
Yes, I have not much experience with samba.
Some time ago I did a simple setup like you (guest writable), and chmod-ed the folder on server.
However, I did not spent too much on the issue, as I did not use samba a lot.
Bogdan

---

### Post by swerdna on 2009-10-08
Make it like this:
```
[torrents]
path = /home/karakh/torrents
comment = stop beating me and I will work, I promise
read only = no
guest ok = yes
force user = karakh
```
FFI: [Defining and Using File Shares]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")

Mount it with exactly this:
```
mount -t cifs -o password=,uid=karakh,gid=karakh
//192.168.1.101/torrents /temp
```Note: there's no password after the = sign. And temp is a directory right under root (but you can make one anywhere).
FFI: [HowTo Mount a CIFS Network Share]("http://opensuse.swerdna.org/susesambacifs.html")

---

### Post by Karakh on 2009-10-09
Finally got it working with something similar.

```
[storage]
        comment = Public storage
        path = /mnt/sdb3/storage
        create mask = 0644
        directory mask = 0755
        read only = no
        guest only = no
        guest ok = yes
```

Mounted with:

```
sudo mount -t cifs -o guest,nounix //192.168.1.101/storage /media/serverstorage/
```

Thanks guys.

---

