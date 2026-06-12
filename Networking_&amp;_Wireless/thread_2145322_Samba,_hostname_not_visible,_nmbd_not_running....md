---
title: "Samba, hostname not visible, nmbd not running..."
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by manuker on 2013-05-15
Hello!

(sorry for my poor english)

Here is my problem:

Previous situation: ubuntu server 10.04 (without GUI), with samba (version?) running, all was fine, I could access samba share from PC under linux and windows and was able to navigate the windows network.

Actual situation: no change to unbuntu server 10.04 except a "sudo apt-get update" and "sudo apt-get upgrade", Samba is now v3.4.7
No other change to the server, no config file modified...
I have now this problem: I can access the samba share if I access it with IP addresse (192.168.0.100) but NOT with hostname (serveur-ve): I can't see samba share anymore in network browsing! I really need it for some devices on my network.

Here are the *mbd processes:

```
root@serveur-ve:~# pgrep -l mbd
2878 smbd
2881 smbd
```

nmdb is not running..., it is not as it should be, and I guess that's why I can't see my server in the network browsing.

The nmbd log doesn't show errors:

```
root@serveur-ve:~# cat /var/log/samba/log.nmbd
[2013/05/06 07:29:59,  0] nmbd/nmbd.c:71(terminate)
  Got SIGTERM: going down...
[2013/05/06 07:42:00,  0] nmbd/nmbd.c:854(main)
  nmbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
```

And my attempts to restart:

```
ve@serveur-ve:~$ sudo restart smbd
smbd start/running, process 7025
ve@serveur-ve:~$ sudo restart nmbd
restart: Unknown instance: 
ve@serveur-ve:~$
```

And a testparm of the config file: 

```
ve@serveur-ve:~$ testparm /etc/samba/smb.conf
Load smb config files from /etc/samba/smb.conf
rlimt_max: rlimt_max (1024) below minimum Windows limt (16384)
Processing section "[srv_data]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	name resolve order = bcast lmhosts host wins
	dns proxy = No
	panic action = /usr/share/samba/panic-action %d

[srv_data]
	comment = Serveur de donnees Vivarais Energies
	path = /mnt/srv_data
	valid users = ve
	force user = ve
	force group = users
	read only = No
	create mask = 0770
	directory mask = 0770
	hosts allow = 192.168.0.0/26, 127., EXCEPT, 192.168.0.102, 192.168.0.101
	hosts deny = ALL
	strict locking = Yes
ve@serveur-ve:~$
```

I could not find any relevant answer on the net up to now...
Thank for any help :)

---

