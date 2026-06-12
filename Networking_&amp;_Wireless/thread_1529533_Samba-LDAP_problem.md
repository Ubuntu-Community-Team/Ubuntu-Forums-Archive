---
title: "Samba-LDAP problem"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by hosseinyounesi on 2010-07-12
Hi,
this is my condition. I'm already using Fedora Directory Server (FDS) on fedora and samba on centos and NOW I want to change my samba server to ubuntu 10.04. these are my config files:

smb.conf
```

[global]

# hosi_config
	load printers = yes
	printing = cups
	printcap name = cups
	browseable = yes
	security = user
	client lanman auth = yes
	public = yes
	guest ok = yes

#1
	server string = ITCENTER2
	workgroup = ITCENTER2
	netbios name = ITCENTER_NET12

#2
	log level = 1
	syslog = 0
	log file = /var/log/samba/%m
	os level = 69
	max log size = 50
	name resolve order =  lmhosts hosts wins bcast
	time server = Yes
	wins support = Yes
	socket options = TCP_NODELAY IPTOS_LOWDELAY SO_SNDBUF=9216 SO_RCVBUF=8192

#3
	logon script = logon.bat
	logon path =""
	logon drive =

#4
	domain logons = Yes
	preferred master = Yes
	domain master = Yes
	username map = /etc/samba/smbusers
	interfaces = 127.0.0.1 eth*
	bind interfaces only = yes
	hosts allow = 172.16. 192.168.

#5
	passdb backend = ldapsam:ldap://ldapserver
#	passdb backend = ldapsam:ldaps://ldapserver:636
	ldap admin dn = cn=Directory Manager
	ldap suffix = dc=me,dc=you,dc=they
	ldap group suffix = ou=Groups
	ldap user suffix = ou=Users
	ldap machine suffix = ou=Computers
	ldap ssl =  no
#	ldap ssl =  start_tls
#	ldpasam:trusted = yes
	add machine script = /usr/sbin/smbldap-useradd -w "%u"
	add user script = /usr/sbin/smbldap-useradd -m "%u"
	ldap delete dn = Yes
	add group script = /usr/sbin/smbldap-groupadd -p "%g"
	add user to group script = /usr/sbin/smbldap-groupmod -m "%u" "%g"
	delete user from group script = /usr/sbin/smbldap-groupmod -x "%u" "%g"
	set primary group script = /usr/sbin/smbldap-usermod -g "%g" "%u"
	ldap passwd sync = Yes

[homes]
	comment = Home Directories
	path = /student/%U
	valid users = %U
	writeable = yes
	root preexec = /etc/samba/mkhomedir.sh %U %G

[netlogon]
	comment = Network Logon Service
	path = /home/netlogon
	guest ok = Yes
	locking = No
	browseable = no

[printers]
	comment = All Printers
	path = /var/spool/samba
	browseable = no
	public = yes
	guest ok = yes
	writable = yesdrwxr-xr-x
	printable = yes
	printer admin = root

[print$]
	comment = Printer Drivers
	path = /etc/samba/drivers
	browseable = yes
	write list = @domadmins root administrator lpadmin lp linlab


```

ldap.conf
```

base dc=me,dc=you,dc=they
binddn cn=Directory Manager
bindpw 12345678

port 389
timelimit 120

bind_timelimit 120
idle_timelimit 3600

nss_base_passwd		ou=Departments,ou=users,dc=me,dc=you,dc=they?sub

nss_base_hosts		ou=Departments,ou=users,dc=me,dc=you,dc=they?sub

nss_base_shadow		ou=users,dc=me,dc=you,dc=they?one
nss_base_group		ou=Groups,dc=me,dc=you,dc=they?one

nss_initgroups_ignoreusers root,ldap,named,avahi,haldaemon,dbus,radvd,tomcat,radiusd,news,mailman

uri ldap://ldapserver/
#ssl start_tls
#tls_cacertdthey /etc/openldap/cacerts
#pam_password md5

ldap_version 3

```

I tried to join a windows xp and succeeded, and login with "root" user succeeded too. But when I restart samba service, this error appears:
```

[2010/07/12 19:12:59,  0] lib/smbldap.c:1086(smbldap_connect_system)
  failed to bind to server ldap://ldapserver with dn="cn=Directory Manager" Error: Can't contact LDAP server
  	(unknown)
[2010/07/12 19:12:59,  1] lib/smbldap.c:1265(another_ldap_try)
  Connection to LDAP server failed for the 1 try!

```
and LDAP users can't login and this is given in error log (of windows machine):

```

[2010/07/12 19:32:05,  1] auth/auth_util.c:577(make_server_info_sam)
  User 8510453 in passdb, but getpwnam() fails!
[2010/07/12 19:32:05,  0] auth/auth_sam.c:355(check_sam_security)
  check_sam_security: make_server_info_sam() failed with 'NT_STATUS_NO_SUCH_USER'
[2010/07/12 19:32:07,  0] passdb/pdb_get_set.c:211(pdb_get_group_sid)
  pdb_get_group_sid: Failed to find Unix account for MYUSER

```

tho follwing commands work fine(!):
```

smbldap-useradd MYUSER
smbldap-passwd MYUSER
smbldap-usershow MYUSER

```

I'm confused and I can't understand the problem :(
Any miss in config files? any bug?
samba version is 3.4.7

---

### Post by hosseinyounesi on 2010-07-14
Hi again,
Long time and no answer! Should I ask my question some where else?

Thanks

---

