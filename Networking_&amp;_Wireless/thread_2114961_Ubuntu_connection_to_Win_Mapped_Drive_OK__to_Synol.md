---
title: "Ubuntu connection to Win Mapped Drive OK / to Synology NAS Not OK"
date: 2013-02-11
forum: Networking &amp; Wireless
---

### Post by Carlo Jongen on 2013-02-11
I've made a working connection from Ubuntu ( IP:192.168.2.5 ) to a Win7 ( IP:192.168.2.3 ) Mapped Drive with the next code in fstab:
```
//192.168.2.3/test /media/winshares/test_pc cifs users,uid=1000,rw,suid,credentials=/etc/smbcredentials,workgroup=My_Network 0 0
```

with the smbcredentials setup like this:
```
username=MyUserName
password=MyPassWord
```

This works fine, Ubuntu mounts the "test" map from Win7 into the "test_pc" map every time the machine boots.

Now I wanted to do the same for my Synology NAS ( DS1812+ / IP:192.168.2.200 ) with the same code and the same credentials ( except for the IP address and the winshares map ).  See code below:
```
//192.168.2.200/test /media/winshares/test_nas cifs  users,uid=1000,rw,suid,credentials=/etc/smbcredentials,workgroup=My_Network  0 0
```

Ubuntu mounts the "test" map from the NAS into the "test_nas"map  every time the machine boots. I can see al the files inside the test map.

BUT, the main difference is that there is a Lock on each file. Apparently I have no R/W permission on the NAS.
However all credentials are ok, UserName, Password and Network Group are fine. When I look at the log of the NAS, it seems that I have access from IP:192.168.2.5 to the Shared Folder. Also when I manually Browse the Network with these credentials I can login and have R/W permission.

How come this code doesn't work for my NAS? 
Anybody any suggestions why I don't have R/W from fstab?

--------------------------------------------------------------------------------------------------
Freelance 3D animation at [www.c3d.be]("http://www.c3d.be")

---

### Post by Carlo Jongen on 2013-02-13
By Accident I made a double post of this issue.

Please find the solution in the next thread:

[http://ubuntuforums.org/showthread.php?p=12507559#post12507559](http://ubuntuforums.org/showthread.php?p=12507559#post12507559)

---

