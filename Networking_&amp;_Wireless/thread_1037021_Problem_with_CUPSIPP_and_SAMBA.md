---
title: "Problem with CUPS/IPP and SAMBA?"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by rhcm123 on 2009-01-11
Hello Ubuntu Forums, 

Ive been running an 8.04 server (headless) with no problems for quite some time now. It was working great until the new year. When it imploded. Every user was deleted. (I don't need help on this, i have another thread going).

After several fix attempts, i backed up my config files and started to reinstall. However, at the parition screen, i marked the USB drive i had connected as format instead of keep. Oops.

No big problem however, as I took 3 hours and rewrote all my config files. Apache, dhcpd, cups, samba, proftpd. All written to exacting standards :) .


Now, this is my problem. On my old server, i would share printers through samba, as the IPP wasn't working. I could never figure out why, but samba worked fine.
However, here, the opposite happened. Samba isn't working but the IPP is!

Does anybody know why? (My next post will be config files).

---

### Post by rhcm123 on 2009-01-11
Config files for cups and samba:

CUPS:
```
root@USSR-MOSCOW:~# cat /etc/cups/cupsd.conf
# Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin
# Allow remote access
Port 631
Allow localhost
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

SAMBA:
```
root@USSR-MOSCOW:~# cat /etc/samba/smb.conf
# CONFIG FILE FOR SAMBA
# WRITTEN BY USSR
# LAST MODIFIED 7 JAN/09

# Global parameters
[global]
	log file = /var/log/samba/log.%m
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	map to guest = Bad User
	wins support = true
	dns proxy = No
	netbios name = USSR-MOSCOW
	server string = SMB system on USSR-MOSCOW
	default = Share
	local master = yes
	workgroup = USSR
	os level = 20
	security = share
	preferred master = no
	max log size = 50
	printing = cups
	printcap name = cups
	use client driver = yes
	guest account = nobody
	load printers = yes
	interfaces = 192.168.2.193

# /SHARE CONFIGS
[share]
	path = /share
	valid users = ussr elisabeth fred nobody
	read only = No
	browseable = yes
	comment = Main share directory on USSR-MOSCOW.
	create mask = 0777
	directory mask = 0777

# BACKUP DRIVE CONFIGS
[backup]
	path = /media/backup
	valid users = root
	read only = No
	browseable = yes
	comment = Backup Drive on USSR-MOSCOW. Authorized use only.
	create mask = 0777
	directory mask = 0777

# PRINTER SETTINGS
[printers]
	comment = Printers on USSR-MOSCOW
	browseable = no
	path = /printer
	printable = yes
	force user = nobody
	public = yes
	writable = no
	create mode = 0700

# CDROM SHARING
[cdrom]
	comment = CD on USSR-MOSCOW
	read only = yes
	writable = no
 	locking = no
	path = /cdrom
	public = yes

```

---

### Post by rhcm123 on 2009-01-11
One last thing i thought I should mention: With my old server, if i went to Places -> Network -> Windows Network -> USSR, my server would show up. (It also appeared in Windows network, and even network)

Now, it dosent appear at all. This was actually mildly helpful, and could somebody help me with getting it back?

---

