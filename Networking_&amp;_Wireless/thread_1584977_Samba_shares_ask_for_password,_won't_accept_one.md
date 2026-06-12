---
title: "Samba shares ask for password, won't accept one"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by turqoisehex on 2010-09-29
**Back story:**
With my clean install of Lucid, Samba didn't work (a seemingly common problem). After installing Apache, system-config-samba, and manually adding users, it worked for a couple of months (see more details here: [http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/](http://reformedmusings.wordpress.com/2010/05/22/samba-file-sharing-in-ubuntu-lucid-10-04-lts/))

Then Samba asked to update. During the update it asked if I wanted to update smb.conf. I did a line by line comparison and the changes appeared to be of no consequence, so I went ahead with it.

Since then, when I try to connect to the Ubuntu system from XP I get:

"The account is not authorized to log in from this location"

When I try and connect from an Ubuntu client it asks for a password as it should, but it won't accept either of the two users who have rights (or any other user). 

Here's the output of smbtree:

```

	\\TOMATO         		tomato
cli_rpc_pipe_open_noauth: rpc_pipe_bind for pipe \srvsvc failed with error ERRnosupport
		\\TOMATO\IPC$           	IPC Service (tomato)
		\\TOMATO\data           	data
		\\TOMATO\jffs           	jffs
		\\TOMATO\optware        	optware
		\\TOMATO\music          	Music
	\\TELEPHASIC-XP  		
		\\TELEPHASIC-XP\hppsc          	hp psc 1300 series
		\\TELEPHASIC-XP\C$             	Default share
		\\TELEPHASIC-XP\ADMIN$         	Remote Admin
		\\TELEPHASIC-XP\print$         	Printer Drivers
		\\TELEPHASIC-XP\IPC$           	Remote IPC
		\\TELEPHASIC-XP\Video          	
	\\TELEPHASIC     		
Server requested plaintext password but 'client plaintext auth' is disabled
anonymous failed session setup with NT_STATUS_INVALID_PARAMETER

```

I don't get the "failed session setup with NT_STATUS_INVALID_PARAMETER" part, but it sounds relevant to the issue.

I've attached my smb.conf, any and all help is appreciated.

---

### Post by luvshines on 2010-10-01
Hi

Looks something similar to this:
[http://ubuntuforums.org/showthread.php?t=1583601](http://ubuntuforums.org/showthread.php?t=1583601)

For the cleatext password thing.

Your smb.conf reads 'encrypt passwords = no' which is asking Windows clients to provide cleartext passwords instead of NTLM hashes. This is possible only if Windows registry has been changed to do so

Try setting it to 'encrypt passwords = yes', restart Samba and give it a try

---

### Post by dmizer on 2010-10-01
Password queries can offten be caused by local permission problems on the server. Could also be a firewall interfering. Check the output of: sudo iptables -L

---

### Post by turqoisehex on 2010-10-01
Thanks luvshines, that appears to have solved the problem! I wonder why that would have been changed, has the default value been changed to 'no' in the package?

Thanks dmizer, I'm sure it will come in handy to know where to look in the future. Here's the output of iptables -L, what should I be looking for?

```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

---

### Post by dmizer on 2010-10-01
If luvshines suggestion solved your problem, then you need not look any further. The iptables output you posted is for a machine without a firewall enabled. This is a good thing if you want to share files via samba.

---

