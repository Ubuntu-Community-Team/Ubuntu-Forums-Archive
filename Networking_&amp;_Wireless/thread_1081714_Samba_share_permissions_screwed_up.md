---
title: "Samba share permissions screwed up"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by lordofduct on 2009-02-26
So I have a samba share set up on computer. It's a folder on a second hard drive. It's owned by "server" who is the main user of that computer. And it's chmodded to 755

The folder is:

/home/share/allusers/ where the device /dev/md0 is mounted

Now the root of this folder is going to be shared and accessible only to limited users.

But in the folder there are 2 folders that are shared via samba as accessible by anyone, one of which is read-only the other is read-write. This is to ANY users (no passwd needed)

So in my /etc/samba/smb.conf I added these lines:

```

[allusers]
comment = public limited share
path = /home/share/allusers
browseable = yes
public = yes
write list = dylan server

[media]
comment = public read only share of media
path = /home/share/allusers/Media
browseable = yes
public = yes
read only = yes
writable = no

[shared]
comment = public writable storage
path = /home/share/allusers/SharedStorage
browseable = yes
public = yes
writable = yes

```


NOW, when I access any of these from Windows they work GREAT. media is read only, shared is writable, and allusers requires a password to access.

BUT, I also have a couple linux boxes as well. One of which I'm posting from right now. This machine I want to mount this network share to a specified location here. Which I do so with this in my fstab:

```

# Server1
//###.###.###.###/allusers	/home/dylan/Storage/server1	cifs	auto,iocharset=utf8,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0

```

where ###.###.###.### is the ip address of the computer

and in /root/.cifscredentials I store the username and password which I added to smbpasswd

when I mount this everything mounts and I can read all the files from there. But I can't write anything! What is going on??? Oh and when I change it to 777 I can write files, but I can't recursively create folders. So if I drag a folder with a folder in it, nothing in the recursive folder gets copied and a permissions error fires.


oh yeah the credentials are:
```

username=dylan
password=*********
uid=server
gid=server

```

---

### Post by dmizer on 2009-02-26
Does "dylan" have an actual account on the server? Are the uid/gid different for dylan on the client and server?

---

### Post by lordofduct on 2009-02-28
there are two users on the host computer.

dylan && server

dylan is basically for me to access through samba. The files are owned by server though (hence uid and gid being server). I've tried both server and dylan as login name through the credentials files and both have the same problem.

---

### Post by lordofduct on 2009-02-28
So I have it working, but I have to log in as server and I had to add a create mask and directory mask to the allusers profile.

Thanks anyways guys.

---

