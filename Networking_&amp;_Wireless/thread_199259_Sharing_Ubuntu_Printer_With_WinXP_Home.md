---
title: "Sharing Ubuntu Printer With WinXP Home"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by sickenmcsluggets on 2006-06-18
Okay Here is my cupsd.conf:
 #
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow 192.168.0.1
  Allow 192.168.0.1
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#
   I have read and reread the wiki at [https://wiki.ubuntu.com/NetworkPrintingWithUbuntu](https://wiki.ubuntu.com/NetworkPrintingWithUbuntu)
 and I have scoured the forums to find a solution or any help that gets me to print from Windows to Ubunut local printer. I have Samba working, and I can add the printer in Windows XP Home...it sees it and allows me to set it up as a default printer on the WinXP laptop. When I try and print anything it says that I am denied access. I can share files fine between the two computers. Any ideas? I've tried so many different cups configurations over the past couple of days, and I just can't get it to work. I can print locally on my Ubuntu computer as well.

---

### Post by crazygerad on 2006-06-18
I have your same exact problem, I used this [http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html](http://www.faqs.org/docs/Linux-mini/Debian-and-Windows-Shared-Printing.html) . I am using a HP PSC 1350 All In One and it says "Access Denied: Unable to connect". I dual boot and when both comps are with Windows XP then there is no problem. 

Also when I try to install it it says HPLIP is an invalid driver, I have tried with the PSC 950 that is the closest XP has to it and even the HP_1300 that comes with the installer CD but no luck whatsoever. Even installed a program called HP Network Printing Installation and it cant find my printer.

---

### Post by sickenmcsluggets on 2006-06-18
I too have an All In One printer (Dell A920) , but found a site from the wiki to substitute a Lexmark Z600 driver to get the thing to print. When I added the printer to XP, it had a driver. Thanks for the link...I'll read it and see if I can find something that will work.

---

### Post by danielti on 2006-06-27
I am having the same problem.

My cupsd.conf:

#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  AuthType None
  Order Deny,Allow
  Deny From All
  Allow From @LOCAL  
  Allow localhost
  Allow From 192.168.0.0/16
</Location>

    <Location /jobs>
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 192.168.0.0/16
    </Location>

    <Location /printers>
    comment = All Printers
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 192.168.0.0/16
    </Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

#
#

My smb.conf :

#
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not many any basic syntactic 
# errors. 
#

#======================= Global Settings =======================

[global]
	log file = /var/log/samba/log.%m
	printer = epson
	guest account = nobody
	passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
	socket options = TCP_NODELAY
	obey pam restrictions = yes
	map to guest = Bad User
	interfaces = 192.168.1.0/24
	encrypt passwords = true
	passwd program = /usr/bin/passwd %u
	dns proxy = no
	netbios name = dannyboy
	server string = %h server (Samba, Ubuntu)
	invalid users = root
	workgroup = HOME
	comment = Impressora
	security = share
	syslog = 0
	panic action = /usr/share/samba/panic-action %d
	max log size = 1000

[public]
  comment = Public Folder
  path = /home/public
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup



[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = yes
   path = /tmp
   printable = yes
   public = yes
   writable =yes
   create mode = 0700
   printing = cups
   printcap name = cups


# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

# A sample share for sharing your CD-ROM with others.
[cdrom]
   comment = Samba server's CD-ROM
   writable = no
   locking = no
   path = /cdrom
   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#	cdrom share is accesed. For this to work /etc/fstab must contain
#	an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#	is mounted on /cdrom
#
   preexec = /bin/mount /cdrom
   postexec = /bin/umount /cdrom

[websites]
    comment = Websites Tests 
    path = /home/daniel/websites 
    public = yes 
    writable = yes
    guest ok = yes
    browseable = yes
    create mask = 0777 
    directory mask = 0777 
    force user = nobody 
    force group = nogroup

I can connect, but I can't print. I get access denied message in Windows XP Home.

Regards,

---

### Post by danielti on 2006-06-27
Found the solution:

Just add :
use client driver = yes

To the printer section in smb.conf and restart samba.

---

