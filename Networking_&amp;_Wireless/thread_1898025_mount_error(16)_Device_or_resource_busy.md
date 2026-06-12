---
title: "mount error(16): Device or resource busy"
date: 2011-12-20
forum: Networking &amp; Wireless
---

### Post by kamaradski on 2011-12-20
ooow no, not another samba\cifs\mounting thread! yes sorry though i did many searches i wasn't able to solve this one yet.

Setup:
- Samba server on turnkey linux (ubuntu) virtual machine.
- Trying to mount in fstab with "cifs".

Though the share is perfectly reachable by my windows-xp virtual machine, my xubuntu is refucing to mount this share with the following error: mount error(16): Device or resource busy

Samba config:
```

[global]
#	workgroup = WORKGROUP
	server string = uTserver
	hosts allow = 10.0.0. 127.
	log file = /var/log/samba/%m.log
	max log size = 1024
	security = user
	encrypt passwords = yes
	smb passwd file = /etc/smbpasswd
	unix password sync = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *New*UNIX*password* %n\n *ReType*new*UNIX*password* %n\n *passwd:*all*authentication*tokens*updated*successfully*
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	name resolve order = lmhosts bcast
	dns proxy = yes

#============================ Share Definitions ==============================

[utorrent]
	comment = uTorrent files
	path = /media/torrents
	writeable = yes
	guest ok = no
	public = no
	valid users = user1 user2
	read list = user1
	write list = user2

[utorrent-config]
        comment = uTorrent configuration
        path = /etc/utserver
        writeable = yes
        guest ok = no
        public = no
        valid users = user1 user2
	read list = user1
	write list = user2

[utorrent-logs]
        comment = uTorrent configuration
        path = /var/log
        writeable = no
        guest ok = no
        public = no
        valid users = user1 user2
	read list = user1 user2

```


/etc/fstab entries for these mounts:
```


##### Utorrent server #############################################################################
//10.0.0.25/utorrent/		/media/utserver-server	cifs	rw,noauto,user,credentials=/root/credfile.utserver,gid=users 0 0 
//utserver/utorrent-config/	/media/utserver-config	cifs	rw,noauto,user,credentials=/root/credfile.utserver,gid=users 0 0 
//utserver/utorrent-logs/	/media/utserver-logs	cifs	rw,noauto,user,credentials=/root/credfile.utserver,gid=users 0 0 
###################################################################################################

```

As this is a virtual machine running on the host, it should not automount on boot. therefore also 'user' is added so the desktop user is able to initiate the mount at a later stage.

As the mounts are working on other machines the error should be in the host, but to be honest i cannot see much going wrong in the fstab.. ?

Anyone able to share me some pointers on how to troubleshoot this ?

KR
kamaradski

---

### Post by kamaradski on 2011-12-21
Hmm dis is proofing harder then expected.

No documentation on this error available as far as i can see.

I tried all different kind of mounts in fstab and from the command line, so fart nothing seems to be able to work.

Though both from my work laptop (win7), as from my win XP, i have no problem mounting the drive ... kinda frustrating if you ask me.

KR
kamaradski

---

### Post by kamaradski on 2011-12-26
Ok this is my last shameless bumb of this thread.

But would anyone be able to explain me more about the mount-error-16, Some extensive troubleshooting over the last few days is not bringing me closer to any solution.

It would a lot if i would know a little bit more about the error itself? What device is actually busy? testing shows there is nothing wrong with the server, so would actually my mount-point be busy ? I cannot find any proof of this being so.

Anyway i'm totally stuck with this and would appreciate any help or link, however small, anything is useful at this point.

KR
kamaradski

---

### Post by luvshines on 2012-01-09
Maybe the mount point is already busy.

See if you can get anything in the mount command output.
Also can give a try to 'lsof' and 'fuser' command for the mount paths.

---

