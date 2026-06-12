---
title: "Samba Mount Problem on Upgrade from 10.04 to 12.04"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by blitzit on 2012-04-28
I upgraded my Ubuntu installation from 10.04 to 12.04 as soon as it was available.

I have a NAS Storage on which I have all my files backed up. On the 10.04 installation I had a line inserted in my fstab file such that it would mount automatically on start-up.

```
//10.64.251.248/vijay /media/NAS248 cifs credentials=/root/.smbcredentials,iocharset=utf8,noserverino,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0

```

I figure it won't work unless I had the packages *samba* and *smbfs* installed. However, I am not able to install them via apt-get or Software Center.

Has there been an upgrade on Samba? I need help with migrating the mount method.

Also, it would helpful if I got some suggestions to select between Samba and NFS.

---

### Post by Morbius1 on 2012-04-28
Not being able to install the samba package is not a good thing although you really don't need it as a samba client. What kind of error messages do you get?

The smbfs package is really a dummy package in that all it does is install it's replacement so you might try to install that instead:
```
sudo apt-get install cifs-utils
```

---

### Post by blitzit on 2012-04-28
I have cifs-utils installed. I checked again with apt-get.

I get this message on running

```
vijay@307-21:~$ sudo mount -a
error -1 (Unknown error -1) opening credential file /root/.smbcredentials
error -1 (Unknown error -1) opening credential file /root/.smbcredentials
```

Apparently these correspond to the following two samba mount lines that I have in my fstab file
```
#Mounting the Windows Partition
//dev/sda2 /media/Windows ntfs defaults,file_mode=0777,dir_mode=0777,uid=1000,gid=1000 0 0

#Mounting the Video Library
//10.64.251.248/VIDEO /home/vijay/Videos/CentralLibrary cifs credentials=/root/.smbcredentials,iocharset=utf8,noserverino,gid=1000,uid=1000,nounix,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by blitzit on 2012-04-28
Okies, got it! I had forgotten to copy my credentials file from my backup :)

Sorry to bug you guys. My bad. I have my NAS mounted and running now.

---

