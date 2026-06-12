---
title: "Ubuntu connection to Win Mapped Drive OK /to Synology NAS Not OK"
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

### Post by tgalati4 on 2013-02-11
I don't have an Synology NAS, but I understand that it uses a Linux firmware.  Perhaps there is a difference in the version of samba that is being used.

After mounting:

```
smbstatus
```

Samba 3.6.6 seems to be running on 12.10.  I also know that if you don't have the same user accounts on the smbd server (in this case the NAS), then user authentication becomes difficult.  I don't know how the Synology NAS server authenticates its users without PAM.  Perhaps it runs PAM with fake users, I have no idea.

Try using smbmount from the command line and see if that works.  You will have to work out the switches for that command.

A work-around would be to allow permissive shares.  Not secure, but try it and see if it works.  Look in /etc/samba/smb.conf

---------------------------------------------
####### Authentication #######

# "security = user" is always a good idea. [B]This will require a Unix account
# in this server for every user accessing the server.[/B] See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

security = share

--------------------------------

Browse the files in /var/log/samba for clues.

---

### Post by Carlo Jongen on 2013-02-13
Thanks tgalati4 but your suggestion didn't work either.

I did a long google search and after several trials and errors I came up with this code below.
Apparently this did the trick. So with this code I can mount Shared Maps from the Synology Disk in Ubuntu 12.10 and it also mounts Win7 Shared Maps.

Maybe it can be useful to others:

```
//192.168.2.200/test /media/winshares/test_nas cifs credentials=/etc/smbcredentials,rw,noperm,iocharset=utf8,dir_mode=0777,file_mode=0777 0 0
```


--------------------------------------------------------------------------------------------------
Freelance 3D animation at [www.c3d.be](www.c3d.be)

---

