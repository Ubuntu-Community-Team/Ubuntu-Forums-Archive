---
title: "Cannot mount from smbmount, but works fine in Nautilus"
date: 2010-06-11
forum: Networking &amp; Wireless
---

### Post by chamila.sujeewa on 2010-06-11
I have a Samba (v3) server setup in Ubuntu 9.1, with the IP address 10.16.76.114. There is a drive (/dev/sdb1) mounted via fstab with the following options in the server. 

```
/dev/sdb1       /media/storage  ext3    defaults        0       2
```

I have shared this using the following stanza.

```
[storage]
        comment = shared storage
        path = /media/storage
        read only = No
        force user = username
        force group = username
        guest ok = Yes
        nt acl support = No
```

There is a Ubuntu 10.04 client machine. The packages smbfs and smbclient are installed there. 

The smbclient command gives the following output. 

```
root@ugclient:~# smbclient -L 10.16.76.114
Enter root's password: 
Domain=[DOMAINNAME] OS=[Unix] Server=[Samba 3.3.2]

	Sharename       Type      Comment
	---------       ----      -------
	IPC$            IPC       IPC Service (ubsmb server (Samba, Ubuntu))
	storage         Disk      shared storage
	print$          Disk      Printer Drivers

```
But when I issue the smbmount command it gives the following error. 

```
root@ugclient:~# smbmount //10.16.76.114/storage /mnt/storage -o guest
Warning: mapping 'guest' to 'guest,sec=none'
mount error(11): Resource temporarily unavailable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

But there can't be any network error or share error since I can access the shared space by entering smb://10.16.76.114/storage in Nautilus. I can even create, edit, delete files and folders there, and all with the default user privileges. 

I have Googled, and think I've exhausted all the forum entries on this issue. Most of them gives answers like to check the username, password, to check the spaces between the options or even to check the network status.

I have used the mount -t cifs/smbfs command and came down with the same result. I think the kernel in the client machine supports cifs file system since it gives the following output.

```
root@ugclient:~# lsmod | grep cifs
cifs                  248081  0 
```


Can anyone help me with this? 

([This link]("http://ubuntuforums.org/showthread.php?t=947279") says something about a certain bug in a particular version of smbfs but the one I have is "2:3.4.7~dfsg-1ubuntu3", so It didn't help.)

(The Samba server is setup to work with a OpenLDAP server but since I have enabled Guest user, I don't think it is any effect on this. On the other hand I CAN access it through Nautilus.)

---

### Post by chamila.sujeewa on 2010-06-14
No reply? Nobody even came across this problem before?

---

