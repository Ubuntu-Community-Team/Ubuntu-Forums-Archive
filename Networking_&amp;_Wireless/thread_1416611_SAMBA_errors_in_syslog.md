---
title: "SAMBA errors in syslog"
date: 2010-02-26
forum: Networking &amp; Wireless
---

### Post by BarryDocks on 2010-02-26
Hi there,

Recently noticed the following message in the syslog:
```
Feb 26 15:12:29 fileserver smbd[18430]: [2010/02/26 15:12:29, 0] smbd/service.c:make_connection_snum(859) 
Feb 26 15:12:29 fileserver smbd[18430]:   make_connection: connection to IPC$ denied due to security descriptor.
```

I assume it's samba related.  I have made a few changes lately but can't pin it down to anything.  Windows clients are connecting without any problems.

here's my smb.conf
```
[global]
	log file = /var/log/samba/log.%m
	load printers = yes
	name resolve order = bcast host lmhosts wins
	socket options = SO_KEEPALIVE TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=8192 SO_RCVBUF=8192
	force group = allhosts
	interfaces = eth1 lo
	hosts allow = xxx.xxx.xxx.xxx
	encrypt passwords = true
	password level = 8
	dns proxy = No
	netbios name = FileServer
	cups options = raw
	server string = 
	printing = cups
	kernel oplocks = no
;	veto oplock files = /*.mdb/
	local master = yes
	workgroup = WORKGROUP
	os level = 65
	hosts deny = ALL
	printcap name = cups
	security = user
	bind interfaces only = yes
#	oplocks = false

[printers]
  	comment = All Printers
   	path = /var/spool/samba
  	browseable = no
# to allow user 'guest account' to print.
   	guest ok = yes
   	writable = no
   	printable = yes
   	create mode = 0700

[print$]
  	path = /var/lib/samba/printers
  	browseable = yes
  	read only = yes
  	write list = root

# A useful application of samba is to make a PDF-generation service
# To streamline this, install windows postscript drivers (preferably 
# colour)on the samba server, so that clients can automatically install
# them.

;[pdf-generator]
;   path = /var/tmp
;   guest ok = No
;   printable = Yes
;   comment = PDF Generator (only valid users)
   #print command = /usr/share/samba/scripts/print-pdf file path win_path recipient IP &
;   print command = /usr/share/samba/scripts/print-pdf %s ~%u \\\\\\\\%L\\\\%u %m %I &

# Case Preservation can be handy - system default is _no_
# NOTE: These can be set on a per share basis
;  preserve case = no
;  short preserve case = no
# Default case is normally upper case for all DOS files
;  default case = lower
# Be very careful with case sensitivity - it can break things!
;  case sensitive = no

# a service which has a different directory for each machine that 
# connects this allows you to tailor configurations to incoming 
# machines. You could also use the %u option to tailor it by user name.
# The %m gets replaced with the machine name that is connecting.
;[pchome]
;  comment = PC Directories
;  path = /usr/pc/%m
;  public = no
;  writable = yes

;[homes]
;	comment = Home Directories
;	read only = No
;	browseable = No

[Adrian]
	comment = Adrians Files
	path = /media/disk/adrian
	valid users = xx
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777

[Music]
	comment = MP3s etc
	path = /media/disk/music
	read only = No
	guest only = Yes
	guest ok = Yes
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777
;force user = xx

[Staff]
	comment = Staff Files
	path = /media/disk/staff
	valid users = xx
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777
force user = xx
[Focus Data]
	writeable = yes
	path = /media/disk/focus_data
	force directory mode = 0777
	force create mode = 0777
	force user = xx
	comment = Data files for Focus and Clinical Records
	valid users = xx
	create mode = 0777
	directory mode = 0777
       veto oplock files = /*.mdb/

[Practice Documents]
	comment = Practice documents and files
	path = /media/disk/practice_documents
	valid users = xx
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777
force user = xx

[HoyaLog]
	comment = HoyaLog files
	path = /media/disk/hoyalog
	valid users = xx
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777
;force user = xx

[Clinical Images]
	comment = Clinical image files
	path = /media/disk/clinical_images
	valid users = xx
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777
;force user = xx

[SAGE]
	comment = SAGE accounts files
	path = /media/disk/sage
	valid users = xx
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777
;force user = xx

[Drivers_etc]
	comment = Windows drivers & device settings
	path = /media/disk/drivers_etc
	valid users = xx
	read only = No
	create mask = 0777
	force create mode = 0777
	directory mask = 0777
	force directory mode = 0777
force user = xx


```

---

