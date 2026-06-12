---
title: "Share folder with mac and windows"
date: 2010-03-09
forum: Networking &amp; Wireless
---

### Post by fiftyfour123 on 2010-03-09
I have a ubuntu server machine in my house and i want to create a folder that can be shared with all the computers on the network. Should i use NFS? how would i do this? I don't want to give out the admin password of the server to login to the folder, so is there a way to make a username and password specifically for the folder? Also, I want it to be accessible over the internet as well. And i want to automount the folder on the computers that access it so that it's just mounted at boot automatically.

Thanks

---

### Post by johnson.d on 2010-03-10
If you want to have a login for the share, You can use Samba server for sharing.

1) You can install Samba by using the following command:

```
$ sudo apt-get install samba
```

2) To create a new username for samba you can use the following steps:

(i) Create a username

```
$ sudo useradd <user-name>
```

Enter the password

(ii) Add the user as a samba user

```
$ sudo smbpasswd -a <user-name>
```

Enter the SMB passwd

Now the username will get added to the samba users

You can append the /etc/samba/smb.conf file with the following lines:

[<Share-name>]

path = /<share-path>
browseable = yes
valid users = <user-name>

Now you can limit the access to the particular user you have created.

---

### Post by fiftyfour123 on 2010-03-10
thanks, it works perfectly!

---

