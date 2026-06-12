---
title: "How to: mount a remote (ftp/ssh) directory locally"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by TheHimself on 2010-01-15
If you use Nautilus then you can just use the "Connect to server" from the file menu. However if you file manager does not support connecting to servers (like Thunar ) then you can use sshfs.

```
sudo apt-get install sshfs
```

You should create a directory as your mount point, say
```
mkdir /media/Server
``` 

If you make the directory outside your home folder (lie the above example) then you should make it your own:

```
sudo chown USER:USER /media/Server
```

where USER is your (local) username. To mount you remote directory run

```
sshfs *username*@*server*: *mountpoint* 
```

for example

```
sshfs thehimself@hellskitchen.org: /media/Server
```

Now you should be able to read form and write to your remote directory by pointing your file manager to the mount point (/media/Server in the above example). To unmount run

```
usermount -u /media/Server
```


Nautilus does not direct you to your remote home folder when you connect to a server and so you have to search and find it but sshfs does direct you to your home folder.

If you connect to a server frequently, you can make an alias:

```
 gedit $HOME/.bashrc 
```

and add the following 

```
 alian conn='sshfs thehimself@hellskitchen.org: /media/Server' 
```

(suitably modified for your case) to the end of the file. Now you can just run

```
conn 
```

to connect to the server. (I don't know how one can store their password without explicitly putting it in the bash file.)

---

### Post by batnas on 2010-01-15
By using Places -> Connect to server...
I am able to use nautilus to browse a passworded ftp server.

I am not sure if this is what you need.

\\Batnas

---

