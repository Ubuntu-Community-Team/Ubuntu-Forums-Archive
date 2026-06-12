---
title: "share files not writable on xp server"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by linuxcss on 2010-01-31
I am trying to get write access to a share on xp machine via automatically mounting
the share via the following /etc/fstab entry .... after doing a
sudo mount -a ...
I can view the files on the 'C-share' but can not write them back to the server

//WINBLOWS/C-share  /media/C-share  cifs,rw

This used to work and allow share files to be read and writable  before some ubuntu updates. 

I am currently running ubuntu 9.10.

PS: if I connect via places->network ... the files are readable and writable ... but I need this 
setup to be automatic with a mount for someone else.

What needs to be added to the above fstab entry

---

### Post by suseendran.rengabashyam on 2010-02-01
Hi,

Try the following steps in your Ubuntu machine and let me know if it works

1) Open a Terminal and enter the following:

```
sudo id user_name
```

The output will be something similar to:

```
uid=1000(user_name) gid=1000(user_name) groups=...
```

Make a note of the uid and gid.

2) Make the following entry in your /etc/fstab file :

If you don't need a user name and password to access a samba share add this line:

```
//server_name/share_name  /mount_path  cifs  defaults,uid=1000,gid=1000  0  0
```

If you need a user name and password to access a samba share add this line and proceed to the next 2 steps:

```
//server_name/share_name  /mount_path  cifs  defaults,uid=1000,gid=1000,credentials=/root/.smbcredentials  0  0
```

Modify the server_name, share_name, mount_path, UID value and GID value to suit your environment.

"uid=1000,gid=1000" entry will result in mounted share being owned by the uid=1000 and gid=1000. 

4) Add the following in /root/.smbcredentials:

```
username=myusername
password=mypassword
```

Where myusername and mypassword is the user name and password to access the samba share.

5) Set the following permission to /root/.smbcredentials

```
chmod 600 /root/.smbcredentials
```

6) Now try to login as a particular user and see whether you able to read and write to the share.

---

