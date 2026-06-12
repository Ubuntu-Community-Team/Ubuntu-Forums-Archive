---
title: "Samba Issues"
date: 2006-01-05
forum: Networking &amp; Wireless
---

### Post by Nikusan on 2006-01-05
Samba is causing me major headaches... It was all working fine until recently, I'm not sure what if anything has changed though.
I can't see my computer on the workgroup (from my computer or any other), but I can see and access the other windows machines on the network.

*smb://problemchild* doesn't work either. I've tried completely removing and reinstalling samba and samba-common.
It need to use *security = share* and it seems that is frowned upon so I'm not sure if anyone can help me.

Slightly off-topic - should my domain name in network settings be the same as the workgroup name in smb.conf, or should it be blank? Neither seem to make this work again though :(

here's my smb.conf:

```

[global]
security = share
wins support = no
workgroup = mshome
netbios name = problemchild

[Documents]
path = /home/dan/Documents
available = yes
browseable = yes
public = yes
guest ok = yes
writable = no

```

---

### Post by schdefan on 2006-01-06
to check if the syntax of your smb.conf is correct yiou can use the program testparm. From a quick view of your smb.conf it must be 
[COLOR="Black"]**writeable **[/COLOR]not [COLOR="Red"]**writable**[/COLOR] in Documents.

Try to use the IP address of the computers first.  From my experience Windows networking is sometimes very slow in learning names.

schdefan

---

### Post by Nikusan on 2006-01-07
Thanks schdefan it's working again now.

Edit: Whoops, I lied.

```

dan@problemchild:~$ /etc/init.d/samba restart
 * Stopping Samba daemons...                                             [ ok ]
 * Starting Samba daemons.. /etc/init.d/samba: line 24: 10085 Aborted                 start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/smbd -- -D
                                                                         [fail]

```

---

### Post by Nikusan on 2006-01-07
Using synaptic I just completely removed and then re-installed samba, samba-comon, smbclient, etc.
(Using the sample smb.conf) I now get:
```

dan@problemchild:~$ /etc/init.d/samba restart
 * Stopping Samba daemons...                                             [ ok ]
 * Starting Samba daemons.. /usr/share/samba/panic-action: line 48: mail: command not found
Failed to read a valid object file image from memory.
/etc/init.d/samba: line 24: 11289 Aborted                 start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/smbd -- -D
                                                                         [fail]


```

I'm worried now that it's something more serious...

---

