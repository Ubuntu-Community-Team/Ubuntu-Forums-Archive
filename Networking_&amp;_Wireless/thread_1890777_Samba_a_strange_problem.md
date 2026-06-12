---
title: "Samba a strange problem"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by poolet on 2011-12-04
I have build a server am trying to configure samba for file sharing but I have a strange problem... When am trying to reach the ip address smb://192.168.*.** works fine (See pictures below) if I try to connect on the spesific folder of then am get file not found... It's a strange problem since I have check twice the folder and is here I have also make 2 - 3 folders and try again but nothing the problem isn't fixed!!! Any ideas?? Below I post my smb.conf configuration please check it and let me know if something goes wrong!!! 

PICTURE 1:: 

[IMG]http://i40.tinypic.com/5cu0z.png


PICTURE 2:: 
[IMG]http://i42.tinypic.com/2uq2d7n.png

Thank you!!!

global] panic action = /usr/share/samba/panic-action %d workgroup = "Name" netbios name = "Server name" invalid users = root security = user wins support = no log file = /var/log/samba.log log level = 3  max log size = 1000 syslog = 1 encrypt passwords = true passdb backend = smbpasswd socket options = TCP_NODELAY dns proxy = no passwd program = /usr/bin/passwd %u passwd chat =*Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n . obey pam restrictions = yes pam password change = no null passwords = no  #Share Definitions  [homes]         comment = Home Directories         path = /srv/samba/share
        browseable = yes         writable = yes         security mask = 0700         create mask = 0700

---

### Post by dandnsmith on 2011-12-04
Are you quoting the smb.conf from the system which has produced those enormous pix you've posted?
If so, you're barking up a tree in the wrong forest, so to speak, as the local samba config has nothing to do with access the remote filesystem - it controls the actions of the local server, whereas you want the remote server actions.
If the config is for the remote system, then it doesn't look as if it has really been configured yet.

---

### Post by CharlesA on 2011-12-04
You don't use firefox to connect to a samba share.

Use Nautilus.

Run ***testparm*** and see if it spits out any errors.

---

### Post by Morbius1 on 2011-12-04
I'm not entirely sure what you are trying to achieve here but I think you are using the [homes] share the wrong way. A typical [homes] share allows clients to access their home directories on the Samba  server by creating a share "on the fly" at the moment the client asks  for it. In fact the typical [homes] share has no path.

If this is just a regular share then rename the share form this:
> [homes] 
comment = Home Directories 
path = /srv/samba/share
browseable = yes 
writable = yes 
security mask = 0700 
create mask = 0700To this:
> [COLOR=Blue]**[homes2] **[/COLOR]
[COLOR=Blue]**comment = Home2 Directory **[/COLOR]
path = /srv/samba/share
browseable = yes 
writable = yes 
security mask = 0700 
create mask = 0700Restart samba:
```
sudo service smbd restart
```And you'll see what I mean.

You can easily create a [homes] share that specifies a path but it requires a bit more work than you have done. And you would have to access it a different way. You don't browse to it you specify the user name of the client in the path: 
```
thunar smb://192.168.0.16/morbius
```If you have Windows clients and you set up user names and samba passwords in a certain way then they will be able to browse to and connect automatically.

---

### Post by poolet on 2011-12-04
Problem *SOLVED* Thank you very much guys!!!!!!!  Just follow the [Morbius1]("http://ubuntuforums.org/member.php?u=982144") instructions !!!

---

### Post by poolet on 2011-12-04
> **CharlesA said:**
> You don't use firefox to connect to a samba share.

Use Nautilus.

Run ***testparm*** and see if it spits out any errors.


No errors with  ***testparm***. I run it before I fixed the problem!! Same result as know!! But thank I figure out!!!

---

