---
title: "Mapping a Network Drive in Ubuntu"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by jcm4 on 2008-12-07
I'm a Linux noob, I've spent the last 3 hours looking through Google to find out how to access a network drive, but I just can't get it. 
The instructions for Windows are as follows:
1.	Right Click on “My Computer” and select “Map Network Drive”
2.	Pick Drive Letter “I”
3.	In the Folder field enter \\WFS4\academics\
4.	Make sure the “Reconnect at Login” box is checked
5.	Select Finish


Can somebody please take the time to tell me the steps to go through to access it? Thanks.

---

### Post by dark_harmonics on 2008-12-07
> **jcm4 said:**
> I'm a Linux noob, I've spent the last 3 hours looking through Google to find out how to access a network drive, but I just can't get it. 
The instructions for Windows are as follows:
1.	Right Click on “My Computer” and select “Map Network Drive”
2.	Pick Drive Letter “I”
3.	In the Folder field enter \\WFS4\academics\
4.	Make sure the “Reconnect at Login” box is checked
5.	Select Finish


Can somebody please take the time to tell me the steps to go through to access it? Thanks.
First install smbfs with ```
sudo apt-get install smbfs
```
Then create a mount point for it under media with:
```
sudo mkdir /media/WFS4
``` You can really name the folder whatever you like.
Next put an entry in /etc/fstab so that your computer mounts it on each boot.

```
sudo gedit /etc/fstab&
```
add a line to the end of that file like this one:
//WFS4/academics/ /media/WFS4 cifs noperms 0 0

If you need a username and password to mount that you might need to edit like this:
//WFS4/academics/ /media/WFS4 cifs user=your_username_,pass=your_password,noperms 0 0

Save and close that file. Then run 

```
sudo mount -a
``` to force a mount or just reboot.

---

### Post by jcm4 on 2008-12-07
Thanks, but I get the following after trying to mount it:
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

---

### Post by jcm4 on 2008-12-07
Nevermind, I had to use a username and password. Thanks a bundle!

---

### Post by hambone79 on 2008-12-07
You are most likely having problems with the way the password is passed to the mount command (something I have run into many times). I would try changing the fstab line to this:
```

//WFS4/academics/ /media/WFS4 cifs credentials=/home/username/.credentials,domain=mydomain 0 0
```

After that, create a credentials file in /home/username/.credentials with the following info:

```

username=my_username
password=my_password

```

---

### Post by dark_harmonics on 2008-12-08
> **hambone79 said:**
> You are most likely having problems with the way the password is passed to the mount command (something I have run into many times). I would try changing the fstab line to this:
```

//WFS4/academics/ /media/WFS4 cifs credentials=/home/username/.credentials,domain=mydomain 0 0
```

After that, create a credentials file in /home/username/.credentials with the following info:

```

username=my_username
password=my_password

```

I didnt know this and i find it rather useful because you can change the credentials file instead of each entry in your /etc/fstab. I am therefore marking this post as thanked.

---

