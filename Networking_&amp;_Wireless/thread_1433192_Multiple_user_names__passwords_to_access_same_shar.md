---
title: "Multiple user names / passwords to access same shared directory??"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by mbehrenbrinker on 2010-03-18
Hello all,
I have an ubuntu server set up in which i would like my shared media directory to be accessable with multiple usernames / passwords because I use my admisistrator username and password for samba as well, but I do not want to give out that password to all clients in my house. And, I would like to have write permissions but keep other users to read only. Is this possible or do i need to just make one seperate username / password for samba sharing? 

thanks

---

### Post by jrssystemsnet on 2010-03-18
As an example, let's say you have a directory named /data, which is where your samba share lives.

Now let's say you are username john, and you want to allow access to users mary and tom - but you only want mary and tom to be read-only.

```
john@box:~$ sudo addgroup smbusers
john@box:~$ sudo useradd mary -g smbusers
john@box:~$ sudo useradd tom -g smbusers
john@box:~$ sudo usermod john -G smbusers
john@box:~$ sudo chown -R john:smbusers /data
john@box:~$ sudo chmod -R 750 /data
```

OK, at this point, you've made sure that your /data directory exists and has the right permissions, and that you've got a group "smbusers" that you, john, belong to, and that mary and tom also belong to.

Next, we need to add Samba accounts for mary and tom.

```
john@box:~$ sudo smbpasswd -a mary
New SMB password:
Retype new SMB password:
john@box:~$ sudo smbpasswd -a tom
New SMB password:
Retype new SMB password:
```

Now you've got Samba user accounts for Tom and Mary.  At this point, the system permissions are all correct, so you should have exactly what you want - all three of you can access the Samba share to /data, and you can read or write but Tom and Mary can only read.  But if you're a belt-and-suspenders kind of guy, you might want to make absolutely certain by also setting permissions on the Samba share itself, in /etc/samba/smb.conf.

```
[data]
comment = stuff in my /data directory
path = /data
valid users = john mary tom
write list = john
```

There; now if you slip up and make a file world-writeable or group-writeable, Mary or Tom still won't be able to write to it if they connect by SMB.

Another common problem: what if you keep creating files that aren't in the right group, or don't have the right permissions?  Well, if you're creating them by SMB access instead of by local access, you can fix that too - add the following lines to the bottom of the share definition:

```
force create mode = 0750
force directory mode = 0750
force group = +smbusers
```

Now, when you access the share using Samba and create a file or directory, you are assured that the file or directory will be owned by group smbusers, and will have permissions 0750 - so, again, john tom and mary can all read it, but only john can write to it.

---

