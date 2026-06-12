---
title: "Help to set access rights to share folders in SAMBA"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by MarcusL on 2013-06-20
Hi all,
I am starting a different thread on this same issue to see if I explain it better than my first, and maybe I can get your expert help.

[COLOR=#000000]I have a folder on an EXT4 partition on a RAID6 mount. The folder is called "share".
From an smb.conf side, I [/COLOR][COLOR=#000000]have just reloaded Ubuntu 12.04 (after much frustration) and have the default SAMBA config, except:

I set up the workgroup to my internal name (LHOME)
and enabled (removed the comments character from) the line Security = User.[/COLOR]

[COLOR=#000000]What I am trying to achieve is:[/COLOR]
[COLOR=#000000]1. User "tm" to have admin rights to the share from Windows 8 client[/COLOR]
[COLOR=#000000]2. User "lf" to have read only access to the share from Windows 8 client[/COLOR]
[COLOR=#000000]3. No guest visibility to the shares[/COLOR]

[COLOR=#000000]I would be OK with:[/COLOR]
[COLOR=#000000]1. User "tm" to have admin rights to the share from Windows 8 client[/COLOR]
[COLOR=#000000]2. Guests (any incorrect user other than"tm") to have read only access to the share from Windows 8 client[/COLOR]
[COLOR=#000000]I have reloaded the Server (after much frustration) and on a default SAMBA config, I set up the workgroup to my internal name and enabled Security = User. 
[/COLOR]
I have created the user "tm" during installation and it is the default / admin user on the Server. I have created the user "lf" via:
> 
[COLOR=#000000][I]root@LSERVER:~# useradd lf
[/I][/COLOR][COLOR=#000000][I]root@LSERVER:~# passwd lf
[/I][/COLOR][COLOR=#000000][I]root@LSERVER:~# smbpasswd -a lf
[/I][/COLOR]

[COLOR=#000000]If I add the following share:[/COLOR]
> [COLOR=#000000][share]
comment = Ubuntu File Server Share
path = /storage/share
browsable = yes
guest ok = yes
read only = no
create mask = 0755
[/COLOR]
[COLOR=#000000]
Then I run:[/COLOR]
> 
[COLOR=#000000]root@LSERVER:~# chown nobody.nogroup /storage/share
root@LSERVER:~# restart smbd
root@LSERVER:~# restart nmbd
[/COLOR]
[COLOR=#000000]
I can then copy, read, delete from the share from Windows 8, without having to log in to do this.[/COLOR]

[COLOR=#000000]Can you suggest a share layout for smb.conf and then the steps on the folder rights so that this is achieved please? 

I will put you on my Christmas card list, I promise! [/COLOR][COLOR=#000000]I am really stuck after hours of noob trial and errors... your help is hugely appreciated!

M[/COLOR]

---

### Post by Morbius1 on 2013-06-20
> [COLOR=#000000]What I am trying to achieve is:[/COLOR]
[COLOR=#000000]1. User "tm" to have admin rights to the share from Windows 8 client[/COLOR]
[COLOR=#000000]2. User "lf" to have read only access to the share from Windows 8 client[/COLOR]
[COLOR=#000000]3. No guest visibility to the shares[/COLOR]
Then change your share definition to this:
> [share]
comment = Ubuntu File Server Share
path = /storage/share
browsable = yes
[COLOR=#0000cd]**guest ok = no**[/COLOR]
read only = no
create mask = 0755
And change ownership to this:
```
[COLOR=#000000]chown tm:tm /storage/share[/COLOR]
```
And permissions to this:
```
chmod 755 /storage/share
```
There's a delicate ballet that occurs between samba authorizations and Linux permissions. In this example the share is set up to allow all authenticated users ( non-guests ) access with write permissions but Linux permissions have been set up to allow write to only one of them.

---

### Post by MarcusL on 2013-06-22
Hi Morbius1,
Address please... for the Christmas card! THANK YOU SO MUCH.

Re the "ballet" as you describe it, what I was trying to achieve is not so out of the ordinary (I would have thought!) so did I miss a good step by step process somewhere on the web to achieve this? In other words did I need to set up users, pwds and smbpwds as I did? I assume yes.

Thanks again! Champion!

M

---

### Post by Morbius1 on 2013-06-22
> **MarcusL said:**
> Hi Morbius1,
Address please... for the Christmas card! THANK YOU SO MUCH.

Re the "ballet" as you describe it, what I was trying to achieve is not so out of the ordinary (I would have thought!) so did I miss a good step by step process somewhere on the web to achieve this? In other words did I need to set up users, pwds and smbpwds as I did? I assume yes.

Thanks again! Champion!

M
You still needed to set up users and then add them to the samba password database. 

I think the problem was the original HowTo you were using. There is only one HowTo in the known universe that tells its reader to set ownership to nobody:nogroup and it's this one: [https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.04/serverguide/samba-fileserver.html)

There's a strange convoluted logic to it and it will in fact work but it sets up a Samba File Server with a guest accessible share that will break the moment you create a private share or ( if the clients are Windows ) the moment you add a samba user matching the Windows user.

---

