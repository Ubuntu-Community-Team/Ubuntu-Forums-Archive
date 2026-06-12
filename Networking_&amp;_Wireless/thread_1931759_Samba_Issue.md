---
title: "Samba Issue"
date: 2012-02-26
forum: Networking &amp; Wireless
---

### Post by just_cruising on 2012-02-26
I have samba setup and running but I have an issue when I browse 2 of my shares they come up with "Windows cannot access \\MediaServer\Movies. The 3rd "TV Shows" I can access without any issues. Below is my smb.conf file

```
[global]
	name resolve order = hosts wins bcast
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
	announce version = 5.0
	username map = /etc/samba/smbusers
	null passwords = yes
	passdb backend = tdbsam
	wins support = true
	netbios name = MediaServer
	writeable = yes
	server string = MediaServer
	printing = CUPS
	workgroup = WORKGROUP
	syslog only = yes
	os level = 20
	valid users = nathan
	printcap name = CUPS
	security = user
	syslog = 1
   ; General server settings





; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
   ;valid users = %S
   ;create mode = 0600
   ;directory mode = 0755
   ;browseable = no
   ;read only = no
   ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
   ;path = /var/lib/samba/netlogon
   ;admin users = Administrator
   ;valid users = %U
   ;read only = no


; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
   ;path = /media/cdrom
   ;browseable = yes
   ;read only = yes
   ;guest ok = yes

[Music]
	comment = Music
	writable = yes
	path = /media/Music


[TV Shows]
	comment = TV Shows
	path = /media/TV Shows

[Movies]
	comment = Movies
	path = /media/Movie

```

---

### Post by wyliecoyoteuk on 2012-02-26
Just a thought, but are the "Music" and "Movie" paths definitely correct?
Might they be "music" and "movie"?
Remember that Unix is case sensitive, (whereas Windows is not)

---

### Post by Toz on 2012-02-26
What are the permissions on the files/directories in /media?
```
ls -l /media
```

---

### Post by Morbius1 on 2012-02-26
As a follow on to what Toz is asking for, you have a global setting of:
> valid users = nathanSamba will allow access only to the user "nathan" but you also have to make sure that "nathan" has Linux permissions to access the actual folders.

---

### Post by just_cruising on 2012-03-03
> **Toz said:**
> What are the permissions on the files/directories in /media?
```
ls -l /media
```

Sorry for delayed reply, the output is as follows

drwx------ 1 nathan nathan 4096 2012-02-16 16:37 Movies

---

### Post by Iowan on 2012-03-03
I'm a bit curious:
> "Windows cannot access \\MediaServer\Movie[COLOR="Red"]s[/COLOR]
> [Movies]
	comment = Movies
path = /media/Movie
> drwx------ 1 nathan nathan 4096 2012-02-16 16:37 Movie[COLOR="Red"]s
[/COLOR] 
Is it Movie, or Movies

---

### Post by just_cruising on 2012-03-03
Thanks Iowan, you pointed something out I had missed. I also changed to "global" for default service under Webmin. Now I can connect to all shares and also map them via Windows7. I can also restart the samba service and it now reconnects without fault.

I also think it may have been that I hadn't mounted one of the drives, can I add a script to do this via startup?

---

### Post by Iowan on 2012-03-03
> **just_cruising said:**
> I also think it may have been that I hadn't mounted one of the drives, can I add a script to do this via startup?
I'm missing most details, but check into */etc/fstab*.

---

