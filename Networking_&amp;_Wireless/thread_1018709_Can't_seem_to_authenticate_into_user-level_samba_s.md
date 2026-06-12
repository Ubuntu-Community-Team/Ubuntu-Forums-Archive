---
title: "Can't seem to authenticate into user-level samba share from XP"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by lumix on 2008-12-22
When I try either root, or another member of the admin group, I continually get rechallenged for a username and password (when I "map network drive").  I can get in with a share-level, guest-ok setup, but want to use user-level for more granularity of permissions (and just for the sake of understanding how to make them work).

The following is my smb.conf with most of the commented lines removed for brevity.

```

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######
security = user
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

   unix password sync = yes

   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssu
ccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'. <---Huh? I didn't change this.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
map to guest = bad user


[printers]
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

# THIS IS THE TEST SHARE.
[www]
	path = /var/www
	read only = no
	locking = yes
	

```

---

### Post by lumix on 2008-12-22
Wait a minute...does smbfs user-level security use the existing user/passwd database (i.e. for console or ssh logins) or a new one unto itself?

---

