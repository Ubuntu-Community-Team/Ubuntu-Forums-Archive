---
title: "Samba4/Win issue"
date: 2012-11-30
forum: Networking &amp; Wireless
---

### Post by erictherev on 2012-11-30
First of all, I'd like to welcome myself back to the community. I took a couple of years off to do something or other.

Second, I put this in Networking and Wireless because it seems to me that sharing on a local network with Samba is a network issue.

Now, to the issues... 
1) I'd like to share user home directories (/home/erictherev) on my local network and have the individual users able to access their own directories. Is this possible?
2) When I look at my shares from a WinXP system, there is some funky stuff under the name of the share.

[IMG]http://i.imgur.com/aCzCL.png[/IMG]

In this example, I'd love to have this just say "Comics on Holonet". What would I need to modify in my smb.conf to accommodate this?

```

# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options (perhaps too
# many!) most of which are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentry and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command "testparm"
# to check that you have not made any basic syntactic errors.
#
#======================= Global Settings =====================================
[global]

# 1. Server Naming Options:
# workgroup = NT-Domain-Name or Workgroup-Name
workgroup = Galactic_Empire

# netbios name is the name you will see in "Network Neighbourhood",
# but defaults to your hostname
netbios name = Holonet

# server string is the equivalent of the NT Description field
server string = Eric's File Server

# Message command is run by samba when a "popup" message is sent to it.
# The example below is for use with LinPopUp:
; message command = /usr/bin/linpopup "%f" "%m" %s; rm %s

# 2. Printing Options:
# CHANGES TO ENABLE PRINTING ON ALL CUPS PRINTERS IN THE NETWORK
# (as cups is now used in linux-mandrake 7.2 by default)
# if you want to automatically load your printer list rather
# than setting them up individually then you'll need this
printcap name = cups

# printcap cache time, so samba will automatically load new cups printers
printcap cache time = 60

# It should not be necessary to spell out the print system type unless
# yours is non-standard. Currently supported print systems include:
# bsd, sysv, plp, lprng, aix, hpux, qnx, cups
printing = cups

# Samba 2.2 supports the Windows NT-style point-and-print feature. To
# use this, you need to be able to upload print drivers to the samba
# server. The printer admins (or root) may install drivers onto samba.
# Note that this feature uses the print$ share, so you will need to
# enable it below.
# Printer admins are now defined by granting the SePrintOperatorPrivilege, ie:
# run: net rpc rights grant 'DOMAIN\Printer Operators' SePrintOperatorPrivilege

# 3. Logging Options:
# this tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/%m.log

# Put a capping on the size of the log files (in Kb).
max log size = 50

# Set the log (verbosity) level (0 <= log level <= 10)
# log level = 3

# 4. Security and Domain Membership Options:
# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page. Do not enable this if (tcp/ip) name resolution does
# not work for all the hosts in your network.
#   hosts allow = 192.168.2. 127.

# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
#  guest account = pcguest
# Allow users to map to guest:
map to guest = Bad User

# Security mode. Most people will want user level security. See
# security_level.txt for details.
security = share
# Use password server option only with security = server or security = domain
# When using security = domain, you should use password server = *
#   password server = <NT-Server-Name>
#   password server = *

# Password Level allows matching of _n_ characters of the password for
# all combinations of upper and lower case.
#  password level = 8
#  username level = 8

# You may wish to use password encryption. Please read
# ENCRYPTION.txt, Win95.txt and WinNT.txt in the Samba documentation.
# Do not enable this option unless you have read those documents
# Encrypted passwords are required for any use of samba in a Windows NT domain
# The smbpasswd file is only required by a server doing authentication, thus
# members of a domain do not need one.
encrypt passwords = yes

# The following are needed to allow password changing from Windows to
# also update the Linux system password.
# NOTE: Use these with 'encrypt passwords' and 'smb passwd file' above.
# NOTE2: You do NOT need these to allow workstations to change only
#        the encrypted SMB passwords. They allow the Unix password
#        to be kept in sync with the SMB password.
;  unix password sync = Yes
# You either need to setup a passwd program and passwd chat, or
# enable pam password change
;  pam password change = yes
#  passwd program = /usr/bin/passwd '%u'
;  passwd chat = *New*UNIX*password* %n\n *Re*ype*new*UNIX*password* %n\n ;*passwd:*all*authentication*tokens*updated*successfully*

# Unix users can map to different SMB User names
;  username map = /etc/samba/smbusers

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
#   include = /etc/samba/smb.conf.%m

# Options for using winbind. Winbind allows you to do all account and
# authentication from a Windows or samba domain controller, creating
# accounts on the fly, and maintaining a mapping of Windows RIDs to unix uid's
# and gid's. winbind uid and winbind gid are the only required parameters.
#
# winbind uid is the range of uid's winbind can use when mapping RIDs to uid's
#  idmap uid = 10000-20000
#
# winbind gid is the range of uid's winbind can use when mapping RIDs to gid's
#  idmap gid = 10000-20000
#
# winbind separator is the character a user must use between their domain
# name and username, defaults to "\"
#  winbind separator = +
#
# winbind use default domain allows you to have winbind return usernames
# in the form user instead of DOMAIN+user for the domain listed in the
# workgroup parameter.
#  winbind use default domain = yes
#
# template homedir determines the home directory for winbind users, with
# %D expanding to their domain name and %U expanding to their username:
#  template homedir = /home/%D/%U

# When using winbind, you may want to have samba create home directories
# on the fly for authenticated users. Ensure that /etc/pam.d/samba is
# using 'service=system-auth-winbind' in pam_stack modules, and then
# enable obedience of pam restrictions below:
#  obey pam restrictions = yes

#
# template shell determines the shell users authenticated by winbind get
#  template shell = /bin/bash

# 5. Browser Control and Networking Options:
# Configure Samba to use multiple interfaces
# If you have multiple network interfaces then you must list them
# here. See the man page for details.
#   interfaces = 192.168.12.2/24 192.168.13.2/24

# Configure remote browse list synchronisation here
#  request announcement to, or browse list sync from:
#       a specific host or from / to a whole subnet (see below)
#   remote browse sync = 192.168.3.25 192.168.5.255
# Cause this host to announce itself to local subnets here
#   remote announce = 192.168.1.255 192.168.2.44

# set local master to no if you don't want Samba to become a master
# browser on your network. Otherwise the normal election rules apply
#   local master = no

# OS Level determines the precedence of this server in master browser
# elections. The default value should be reasonable
#   os level = 33

# Domain Master specifies Samba to be the Domain Master Browser. This
# allows Samba to collate browse lists between subnets. Don't use this
# if you already have a Windows NT domain controller doing this job
#   domain master = yes

# Preferred Master causes Samba to force a local browser election on startup
# and gives it a slightly higher chance of winning the election
#   preferred master = yes

# 6. Domain Control Options:
# Enable this if you want Samba to be a domain logon server for
# Windows95 workstations or Primary Domain Controller for WinNT and Win2k
#   domain logons = yes

# if you enable domain logons then you may want a per-machine or
# per user logon script
# run a specific logon batch file per workstation (machine)
#   logon script = %m.bat
# run a specific logon batch file per username
#   logon script = %u.bat

# Where to store roaming profiles for WinNT and Win2k
#        %L substitutes for this servers netbios name, %u is username
#        You must uncomment the [Profiles] share below
#   logon path = \\%L\Profiles\%u

# Where to store roaming profiles for Win9x. Be careful with this as it also
# impacts where Win2k finds it's /HOME share
# logon home = \\%L\%u\.profile


# The add user script is used by a domain member to add local user accounts
# that have been authenticated by the domain controller, or when adding
# users via the Windows NT Tools (ie User Manager for Domains).

# Scripts for file (passwd, smbpasswd) backend:
# add user script = /usr/sbin/useradd -s /bin/false '%u'
# delete user script = /usr/sbin/userdel '%s'
# add user to group script = /usr/bin/gpasswd -a '%u' '%g'
# delete user from group script = /usr/bin/gpasswd -d '%u' '%g'
# set primary group script = /usr/sbin/usermod -g '%g' '%u'
# add group script = /usr/sbin/groupadd %g && getent group '%g'|awk -F: '{print $3}'
# delete group script = /usr/sbin/groupdel '%g'

# Scripts for LDAP backend (assumes nss_ldap is in use on the domain controller,
# and needs configuration in smbldap_conf.pm
# add user script = /usr/sbin/smbldap-useradd -m '%u'
# delete user script = /usr/sbin/smbldap-userdel '%u'
# add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
# delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
# set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'
# add group script = /usr/sbin/smbldap-groupadd '%g' && /usr/sbin/smbldap-groupshow %g|awk '/^gidNumber:/ {print $2}'
# delete group script = /usr/sbin/smbldap-groupdel '%g'


# The add machine script is use by a samba server configured as a domain
# controller to add local machine accounts when adding machines to the domain.
# The script must work from the command line when replacing the macros,
# or the operation will fail. Check that groups exist if forcing a group.
# Script for domain controller for adding machines:
# add machine script = /usr/sbin/useradd -d /dev/null -g machines -c 'Machine Account' -s /bin/false -M '%u'
# Script for domain controller with LDAP backend for adding machines (please
# configure in /etc/samba/smbldap_conf.pm first):
# add machine script = /usr/sbin/smbldap-useradd -w -d /dev/null -c 'Machine Account' -s /bin/false '%u'

# Domain groups:
# Domain groups are now configured by using the 'net groupmap' tool

# Enable priveleges, ie allowing members of Domain Admins to join machines
# to the domain
# enable privileges = yes

# Samba Password Database configuration:
# Samba now has runtime-configurable password database backends. Multiple
# passdb backends may be used, but users will only be added to the first one
# Default:
# passdb backend = smbpasswd guest
# TDB backen with fallback to smbpasswd and guest
# passdb backend = tdbsam smbpasswd guest
# LDAP with fallback to smbpasswd guest
# Enable SSL by using an ldaps url, or enable tls with 'ldap ssl' below.
# passdb backend = ldapsam:ldaps://ldap.mydomain.com smbpasswd guest
# Use the samba2 LDAP schema:
# passdb backend = ldapsam_compat:ldaps://ldap.mydomain.com smbpasswd guest

# Idmap settings (set idmap uid and idmap gid above):
# Idmap backend to use:
# idmap backend = ldap:ldap://ldap.mydomain.com

# LDAP configuration for Domain Controlling:
# The account (dn) that samba uses to access the LDAP server
# This account needs to have write access to the LDAP tree
# You will need to give samba the password for this dn, by
# running 'smbpasswd -w mypassword'
# ldap admin dn = cn=root,dc=mydomain,dc=com
# ldap ssl = start_tls
# start_tls should run on 389, but samba defaults incorrectly to 636
# ldap port = 389
# ldap suffix = dc=mydomain,dc=com
# Seperate suffixes are available for machines, users, groups, and idmap, if
# ldap suffix appears first, it is appended to the specific suffix.
# Example for a unix-ish directory layout:
# ldap machine suffix = ou=Hosts
# ldap user suffix = ou=People
# ldap group suffix = ou=Group
# ldap idmap suffix = ou=Idmap
# Example for AD-ish layout:
# ldap machine suffix = cn=Computers
# ldap user suffix = cn=Users
# ldap group suffix = cn=Groups
# ldap idmap suffix = cn=Idmap


# 7. Name Resolution Options:
# All NetBIOS names must be resolved to IP Addresses
# 'Name Resolve Order' allows the named resolution mechanism to be specified
# the default order is "host lmhosts wins bcast". "host" means use the unix
# system gethostbyname() function call that will use either /etc/hosts OR
# DNS or NIS depending on the settings of /etc/host.config, /etc/nsswitch.conf
# and the /etc/resolv.conf file. "host" therefore is system configuration
# dependant. This parameter is most often of use to prevent DNS lookups
# in order to resolve NetBIOS names to IP Addresses. Use with care!
# The example below excludes use of name resolution for machines that are NOT
# on the local network segment
# - OR - are not deliberately to be known via lmhosts or via WINS.
# name resolve order = wins lmhosts bcast

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
#   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
#       Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
#   wins server = w.x.y.z

# WINS Proxy - Tells Samba to answer name resolution queries on
# behalf of a non WINS capable client, for this to work there must be
# at least one  WINS Server on the network. The default is NO.
#   wins proxy = yes

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The built-in default for versions 1.9.17 is yes,
# this has been changed in version 1.9.18 to no.
dns proxy = no
dos charset = 850
unix charset = ISO8859-1
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
acl compatibility = winnt
ldap ssl = No
server signing = Auto
# You can enable VFS recycle bin and on-access virus-scanning on a per
# share basis:
# Uncomment the next 2 lines (make sure you create a .recycle folder in
# the base of the share and ensure all users will have write access to it.
# For virus scanning, install samba-vscan-clamav and ensure the clamd service
# is running
#   vfs objects = vscan-clamav recycle
#   vscan-clamav: config-file = /etc/samba/vscan-clamav.conf

# Un-comment the following and create the netlogon directory for Domain Logons
# [netlogon]
#   comment = Network Logon Service
#   path = /var/lib/samba/netlogon
#   guest ok = yes
#   writable = no

#Uncomment the following 2 lines if you would like your login scripts to
#be created dynamically by ntlogon (check that you have it in the correct
#location (the default of the ntlogon rpm available in contribs)
#root preexec = /usr/bin/ntlogon -u '%u' -g '%g' -o %a -d /var/lib/samba/netlogon/
#root postexec = rm -f '/var/lib/samba/netlogon/%u.bat'

# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
#[Profiles]
#    path = /var/lib/samba/profiles
#    browseable = no
#    guest ok = yes
#    writable = yes
# This script can be enabled to create profile directories on the fly
# You may want to turn off guest acces if you enable this, as it
# hasn't been thoroughly tested.
#root preexec = PROFILE='/var/lib/samba/profiles/%u'; if [ ! -e $PROFILE ]; #                then mkdir -pm700 $PROFILE; chown '%u':'%g' $PROFILE;fi
# If you want read-only profiles, fake permissions so windows clients think
# they have written to the files
# vfs objects = fake_perms

# NOTE: If you have a CUPS print system there is no need to
# specifically define each individual printer.
# You must configure the samba printers with the appropriate Windows
# drivers on your Windows clients or upload the printer driver to the
# server from Windows (NT/2000/XP). On the Samba server no filtering is
# done. If you wish that the server provides the driver and the clients
# send PostScript ("Generic PostScript Printer" under Windows), you have
# to use 'printcap name = cups' or swap the 'print command' line below
# with the commented one. Note that print commands only work if not using
# 'printing=cups'
  realm = localdomain
  server role = domain controller
[printers]
comment = All Printers
path = /var/spool/samba
browseable = no
# to allow user 'guest account' to print.
guest ok = yes
printable = yes
create mask = 0700
# =====================================
# print command: see above for details.
# =====================================
print command = lpr-cups -P %p -o raw %s -r # using client side printer drivers.
#   print command = lpr-cups -P %p %s # using cups own drivers (use generic PostScript on clients).
# If you install drivers on the server, you will want to uncomment this so
# clients request the driver
use client driver = yes
# Settings suitable for Winbind:
# write list = @"Domain Admins" root
# force group = +@"Domain Admins"

# A useful application of samba is to make a PDF-generation service
# To streamline this, install windows postscript drivers (preferably colour)
# on the samba server, so that clients can automatically install them.
# Note that this only works if 'printing' is *not* set to 'cups'

[pdf-gen]
path = /var/tmp
printable = Yes
comment = PDF Generator (only valid users)
printing = bsd
#print command = /usr/share/samba/scripts/print-pdf file path win_path recipient IP &
print command = /usr/share/samba/scripts/print-pdf "%s" "%H" "//%L/%u" "%m" "%I" "%J" &
lpq command = /bin/true

[Gaming]
path = /home/shared/Gaming
guest ok = yes
read only = no

[ISOs]
path = /home/shared/ISOs
guest ok = yes
read only = no

[LEGO]
path = /home/shared/LEGO
guest ok = yes
read only = no

[Music]
path = /home/shared/music
guest ok = yes
read only = no

[Setup]
path = /home/shared/Setup
guest ok = yes
read only = no

[Torrents]
path = /home/shared/torrents
guest ok = yes
read only = no

[Wallpapers]
path = /usr/share/wallpapers

[COMICS]
path = /home/shared/Comics
guest ok = yes
read only = no
```

---

### Post by erictherev on 2012-12-01
I'm going with Samba3 on this since that seems to be what I've had the best luck with. I am not using the options in Dolphin for file sharing.

I've got the funky stuff cleared up on the name and description. Now I can see the shares and a good description of everything, but it seems to think I need a guest login.

Here's my current smb.conf:

```

# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options (perhaps too
# many!) most of which are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a # (hash)
# is a comment and is ignored. In this example we will use a #
# for commentry and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command "testparm"
# to check that you have not made any basic syntactic errors.
#
#======================= Global Settings =====================================
[global]

# 1. Server Naming Options:
# workgroup = NT-Domain-Name or Workgroup-Name
workgroup = Galactic_Empire

# netbios name is the name you will see in "Network Neighbourhood",
# but defaults to your hostname
netbios name = Holonet

# server string is the equivalent of the NT Description field
server string = Imperial File Server

# Message command is run by samba when a "popup" message is sent to it.
# The example below is for use with LinPopUp:
; message command = /usr/bin/linpopup "%f" "%m" %s; rm %s

# 2. Printing Options:
# CHANGES TO ENABLE PRINTING ON ALL CUPS PRINTERS IN THE NETWORK
# (as cups is now used in linux-mandrake 7.2 by default)
# if you want to automatically load your printer list rather
# than setting them up individually then you'll need this
; printcap name = cups

# printcap cache time, so samba will automatically load new cups printers
; printcap cache time = 60

# It should not be necessary to spell out the print system type unless
# yours is non-standard. Currently supported print systems include:
# bsd, sysv, plp, lprng, aix, hpux, qnx, cups
; printing = cups

# Samba 2.2 supports the Windows NT-style point-and-print feature. To
# use this, you need to be able to upload print drivers to the samba
# server. The printer admins (or root) may install drivers onto samba.
# Note that this feature uses the print$ share, so you will need to
# enable it below.
# Printer admins are now defined by granting the SePrintOperatorPrivilege, ie:
# run: net rpc rights grant 'DOMAIN\Printer Operators' SePrintOperatorPrivilege

# 3. Logging Options:
# this tells Samba to use a separate log file for each machine
# that connects
log file = /var/log/samba/%m.log

# Put a capping on the size of the log files (in Kb).
max log size = 50

# Set the log (verbosity) level (0 <= log level <= 10)
log level = 3

# 4. Security and Domain Membership Options:
# This option is important for security. It allows you to restrict
# connections to machines which are on your local network. The
# following example restricts access to two C class networks and
# the "loopback" interface. For more examples of the syntax see
# the smb.conf man page. Do not enable this if (tcp/ip) name resolution does
# not work for all the hosts in your network.
#   hosts allow = 192.168.2. 127.

# Uncomment this if you want a guest account, you must add this to /etc/passwd
# otherwise the user "nobody" is used
#  guest account = pcguest
# Allow users to map to guest:
map to guest = Bad User

# Security mode. Most people will want user level security. See
# security_level.txt for details.
security = share

# Use password server option only with security = server or security = domain
# When using security = domain, you should use password server = *
#   password server = <NT-Server-Name>
#   password server = *

# Password Level allows matching of _n_ characters of the password for
# all combinations of upper and lower case.
#  password level = 8
#  username level = 8

# You may wish to use password encryption. Please read
# ENCRYPTION.txt, Win95.txt and WinNT.txt in the Samba documentation.
# Do not enable this option unless you have read those documents
# Encrypted passwords are required for any use of samba in a Windows NT domain
# The smbpasswd file is only required by a server doing authentication, thus
# members of a domain do not need one.
encrypt passwords = yes

# The following are needed to allow password changing from Windows to
# also update the Linux system password.
# NOTE: Use these with 'encrypt passwords' and 'smb passwd file' above.
# NOTE2: You do NOT need these to allow workstations to change only
#        the encrypted SMB passwords. They allow the Unix password
#        to be kept in sync with the SMB password.
;  unix password sync = Yes
# You either need to setup a passwd program and passwd chat, or
# enable pam password change
;  pam password change = yes
#  passwd program = /usr/bin/passwd '%u'
;  passwd chat = *New*UNIX*password* %n\n *Re*ype*new*UNIX*password* %n\n ;*passwd:*all*authentication*tokens*updated*successfully*

# Unix users can map to different SMB User names
;  username map = /etc/samba/smbusers

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
#   include = /etc/samba/smb.conf.%m

# Options for using winbind. Winbind allows you to do all account and
# authentication from a Windows or samba domain controller, creating
# accounts on the fly, and maintaining a mapping of Windows RIDs to unix uid's
# and gid's. winbind uid and winbind gid are the only required parameters.
#
# winbind uid is the range of uid's winbind can use when mapping RIDs to uid's
#  idmap uid = 10000-20000
#
# winbind gid is the range of uid's winbind can use when mapping RIDs to gid's
#  idmap gid = 10000-20000
#
# winbind separator is the character a user must use between their domain
# name and username, defaults to "\"
#  winbind separator = +
#
# winbind use default domain allows you to have winbind return usernames
# in the form user instead of DOMAIN+user for the domain listed in the
# workgroup parameter.
#  winbind use default domain = yes
#
# template homedir determines the home directory for winbind users, with
# %D expanding to their domain name and %U expanding to their username:
#  template homedir = /home/%D/%U

# When using winbind, you may want to have samba create home directories
# on the fly for authenticated users. Ensure that /etc/pam.d/samba is
# using 'service=system-auth-winbind' in pam_stack modules, and then
# enable obedience of pam restrictions below:
#  obey pam restrictions = yes

#
# template shell determines the shell users authenticated by winbind get
#  template shell = /bin/bash

# 5. Browser Control and Networking Options:
# Configure Samba to use multiple interfaces
# If you have multiple network interfaces then you must list them
# here. See the man page for details.
#   interfaces = 192.168.12.2/24 192.168.13.2/24

# Configure remote browse list synchronisation here
#  request announcement to, or browse list sync from:
#       a specific host or from / to a whole subnet (see below)
#   remote browse sync = 192.168.3.25 192.168.5.255
# Cause this host to announce itself to local subnets here
#   remote announce = 192.168.1.255 192.168.2.44

# set local master to no if you don't want Samba to become a master
# browser on your network. Otherwise the normal election rules apply
#   local master = no

# OS Level determines the precedence of this server in master browser
# elections. The default value should be reasonable
#   os level = 33

# Domain Master specifies Samba to be the Domain Master Browser. This
# allows Samba to collate browse lists between subnets. Don't use this
# if you already have a Windows NT domain controller doing this job
#   domain master = yes

# Preferred Master causes Samba to force a local browser election on startup
# and gives it a slightly higher chance of winning the election
#   preferred master = yes

# 6. Domain Control Options:
# Enable this if you want Samba to be a domain logon server for
# Windows95 workstations or Primary Domain Controller for WinNT and Win2k
#   domain logons = yes

# if you enable domain logons then you may want a per-machine or
# per user logon script
# run a specific logon batch file per workstation (machine)
#   logon script = %m.bat
# run a specific logon batch file per username
#   logon script = %u.bat

# Where to store roaming profiles for WinNT and Win2k
#        %L substitutes for this servers netbios name, %u is username
#        You must uncomment the [Profiles] share below
#   logon path = \\%L\Profiles\%u

# Where to store roaming profiles for Win9x. Be careful with this as it also
# impacts where Win2k finds it's /HOME share
# logon home = \\%L\%u\.profile


# The add user script is used by a domain member to add local user accounts
# that have been authenticated by the domain controller, or when adding
# users via the Windows NT Tools (ie User Manager for Domains).

# Scripts for file (passwd, smbpasswd) backend:
# add user script = /usr/sbin/useradd -s /bin/false '%u'
# delete user script = /usr/sbin/userdel '%s'
# add user to group script = /usr/bin/gpasswd -a '%u' '%g'
# delete user from group script = /usr/bin/gpasswd -d '%u' '%g'
# set primary group script = /usr/sbin/usermod -g '%g' '%u'
# add group script = /usr/sbin/groupadd %g && getent group '%g'|awk -F: '{print $3}'
# delete group script = /usr/sbin/groupdel '%g'

# Scripts for LDAP backend (assumes nss_ldap is in use on the domain controller,
# and needs configuration in smbldap_conf.pm
# add user script = /usr/sbin/smbldap-useradd -m '%u'
# delete user script = /usr/sbin/smbldap-userdel '%u'
# add user to group script = /usr/sbin/smbldap-groupmod -m '%u' '%g'
# delete user from group script = /usr/sbin/smbldap-groupmod -x '%u' '%g'
# set primary group script = /usr/sbin/smbldap-usermod -g '%g' '%u'
# add group script = /usr/sbin/smbldap-groupadd '%g' && /usr/sbin/smbldap-groupshow %g|awk '/^gidNumber:/ {print $2}'
# delete group script = /usr/sbin/smbldap-groupdel '%g'


# The add machine script is use by a samba server configured as a domain
# controller to add local machine accounts when adding machines to the domain.
# The script must work from the command line when replacing the macros,
# or the operation will fail. Check that groups exist if forcing a group.
# Script for domain controller for adding machines:
# add machine script = /usr/sbin/useradd -d /dev/null -g machines -c 'Machine Account' -s /bin/false -M '%u'
# Script for domain controller with LDAP backend for adding machines (please
# configure in /etc/samba/smbldap_conf.pm first):
# add machine script = /usr/sbin/smbldap-useradd -w -d /dev/null -c 'Machine Account' -s /bin/false '%u'

# Domain groups:
# Domain groups are now configured by using the 'net groupmap' tool

# Enable priveleges, ie allowing members of Domain Admins to join machines
# to the domain
# enable privileges = yes

# Samba Password Database configuration:
# Samba now has runtime-configurable password database backends. Multiple
# passdb backends may be used, but users will only be added to the first one
# Default:
# passdb backend = smbpasswd guest
# TDB backen with fallback to smbpasswd and guest
# passdb backend = tdbsam smbpasswd guest
# LDAP with fallback to smbpasswd guest
# Enable SSL by using an ldaps url, or enable tls with 'ldap ssl' below.
# passdb backend = ldapsam:ldaps://ldap.mydomain.com smbpasswd guest
# Use the samba2 LDAP schema:
# passdb backend = ldapsam_compat:ldaps://ldap.mydomain.com smbpasswd guest

# Idmap settings (set idmap uid and idmap gid above):
# Idmap backend to use:
# idmap backend = ldap:ldap://ldap.mydomain.com

# LDAP configuration for Domain Controlling:
# The account (dn) that samba uses to access the LDAP server
# This account needs to have write access to the LDAP tree
# You will need to give samba the password for this dn, by
# running 'smbpasswd -w mypassword'
# ldap admin dn = cn=root,dc=mydomain,dc=com
# ldap ssl = start_tls
# start_tls should run on 389, but samba defaults incorrectly to 636
# ldap port = 389
# ldap suffix = dc=mydomain,dc=com
# Seperate suffixes are available for machines, users, groups, and idmap, if
# ldap suffix appears first, it is appended to the specific suffix.
# Example for a unix-ish directory layout:
# ldap machine suffix = ou=Hosts
# ldap user suffix = ou=People
# ldap group suffix = ou=Group
# ldap idmap suffix = ou=Idmap
# Example for AD-ish layout:
# ldap machine suffix = cn=Computers
# ldap user suffix = cn=Users
# ldap group suffix = cn=Groups
# ldap idmap suffix = cn=Idmap


# 7. Name Resolution Options:
# All NetBIOS names must be resolved to IP Addresses
# 'Name Resolve Order' allows the named resolution mechanism to be specified
# the default order is "host lmhosts wins bcast". "host" means use the unix
# system gethostbyname() function call that will use either /etc/hosts OR
# DNS or NIS depending on the settings of /etc/host.config, /etc/nsswitch.conf
# and the /etc/resolv.conf file. "host" therefore is system configuration
# dependant. This parameter is most often of use to prevent DNS lookups
# in order to resolve NetBIOS names to IP Addresses. Use with care!
# The example below excludes use of name resolution for machines that are NOT
# on the local network segment
# - OR - are not deliberately to be known via lmhosts or via WINS.
# name resolve order = wins lmhosts bcast

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable it's WINS Server
#   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
#       Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
#   wins server = w.x.y.z

# WINS Proxy - Tells Samba to answer name resolution queries on
# behalf of a non WINS capable client, for this to work there must be
# at least one  WINS Server on the network. The default is NO.
#   wins proxy = yes

# DNS Proxy - tells Samba whether or not to try to resolve NetBIOS names
# via DNS nslookups. The built-in default for versions 1.9.17 is yes,
# this has been changed in version 1.9.18 to no.
dns proxy = no
dos charset = 850
unix charset = ISO8859-1
restrict anonymous = no
domain master = no
preferred master = no
max protocol = NT
acl compatibility = winnt
ldap ssl = No
server signing = Auto
# You can enable VFS recycle bin and on-access virus-scanning on a per
# share basis:
# Uncomment the next 2 lines (make sure you create a .recycle folder in
# the base of the share and ensure all users will have write access to it.
# For virus scanning, install samba-vscan-clamav and ensure the clamd service
# is running
#   vfs objects = vscan-clamav recycle
#   vscan-clamav: config-file = /etc/samba/vscan-clamav.conf

# Un-comment the following and create the netlogon directory for Domain Logons
# [netlogon]
#   comment = Network Logon Service
#   path = /var/lib/samba/netlogon
#   guest ok = yes
#   writable = no

#Uncomment the following 2 lines if you would like your login scripts to
#be created dynamically by ntlogon (check that you have it in the correct
#location (the default of the ntlogon rpm available in contribs)
#root preexec = /usr/bin/ntlogon -u '%u' -g '%g' -o %a -d /var/lib/samba/netlogon/
#root postexec = rm -f '/var/lib/samba/netlogon/%u.bat'

# Un-comment the following to provide a specific roving profile share
# the default is to use the user's home directory
#[Profiles]
#    path = /var/lib/samba/profiles
#    browseable = no
#    guest ok = yes
#    writable = yes
# This script can be enabled to create profile directories on the fly
# You may want to turn off guest acces if you enable this, as it
# hasn't been thoroughly tested.
#root preexec = PROFILE='/var/lib/samba/profiles/%u'; if [ ! -e $PROFILE ]; #                then mkdir -pm700 $PROFILE; chown '%u':'%g' $PROFILE;fi
# If you want read-only profiles, fake permissions so windows clients think
# they have written to the files
# vfs objects = fake_perms

# NOTE: If you have a CUPS print system there is no need to
# specifically define each individual printer.
# You must configure the samba printers with the appropriate Windows
# drivers on your Windows clients or upload the printer driver to the
# server from Windows (NT/2000/XP). On the Samba server no filtering is
# done. If you wish that the server provides the driver and the clients
# send PostScript ("Generic PostScript Printer" under Windows), you have
# to use 'printcap name = cups' or swap the 'print command' line below
# with the commented one. Note that print commands only work if not using
# 'printing=cups'
; [printers]
; comment = All Printers
; path = /var/spool/samba
; browseable = no
# to allow user 'guest account' to print.
; guest ok = yes
; printable = yes
; create mask = 0700
# =====================================
# print command: see above for details.
# =====================================
; print command = lpr-cups -P %p -o raw %s -r # using client side printer drivers.
#   print command = lpr-cups -P %p %s # using cups own drivers (use generic PostScript on clients).
# If you install drivers on the server, you will want to uncomment this so
# clients request the driver
use client driver = yes
# Settings suitable for Winbind:
# write list = @"Domain Admins" root
# force group = +@"Domain Admins"

# A useful application of samba is to make a PDF-generation service
# To streamline this, install windows postscript drivers (preferably colour)
# on the samba server, so that clients can automatically install them.
# Note that this only works if 'printing' is *not* set to 'cups'

; [pdf-gen]
; path = /var/tmp
; printable = Yes
; comment = PDF Generator (only valid users)
; printing = bsd
#print command = /usr/share/samba/scripts/print-pdf file path win_path recipient IP &
; print command = /usr/share/samba/scripts/print-pdf "%s" "%H" "//%L/%u" "%m" "%I" "%J" &
; lpq command = /bin/true

[Comics]
comment = Comics and Graphic Novels
path = /home/shared/Comics
guest ok = no
read only = no
valid users = nomad lupa

```

---

### Post by CharlesA on 2012-12-01
So you are going to be using Samba 3 not Samba 4? Samba 4 is still in Alpha as far as I know, and version 3 would be a better choice.

The text below the share on XP is just a description, you can modify it in smb.conf.

As far as being prompted for a guest logon, which version of XP are you using? It sounds like maybe simple file sharing is enabled.

---

### Post by bab1 on 2012-12-02
> **CharlesA said:**
> Samba 4 is still in Alpha as far as I know...

Not really.  From the ZDNET,com comes [**_[COLOR="Blue"]this news[/COLOR]_**]("http://www.zdnet.com/samba-4-is-now-slated-for-release-on-november-27-7000006648/") as of 	October 31, 2012 

> Samba 4.0 – complete with a Microsoft-compatible Active Directory controller – is now slated for release on November 27 -- for real.  

The fourth release candidate of the open source  platform was released today and the fifth release candidate is slated for release on November 13. If all goes well, the final version is expected to be released by the end of November, one Samba project manager said today.

At the very least Samba4 is at rc5 as of this November (2012)  [**_[COLOR="Blue"]Here[/COLOR]_**]("http://lists.samba.org/archive/samba-announce/2012/000279.html") is the release email.  So we are well past alpha and beta stages.  It is a brave new world for Samba users.  :-)

---

### Post by CharlesA on 2012-12-02
Wow. That's a big jump. Thanks bab1!

---

### Post by erictherev on 2012-12-02
> **CharlesA said:**
> So you are going to be using Samba 3 not Samba 4? 

I've had pretty good luck with Samba3 in the past, so after trying 4 a few times, I reverted to a version I've had success with. 3 it is!

> **CharlesA said:**
> As far as being prompted for a guest logon, which version of XP are you using?

I'm running XP Pro 32 SP3 on all of the other systems on the local network. 

> **CharlesA said:**
> It sounds like maybe simple file sharing is enabled.

I'm not certain I know what this is or how to turn it on/off.

I've run into this issue before, and it seems like I was able to get it to the point that, so long as Win/Ubuntu passwords match across the network, users could access anything on the file server that they were authorized to with read/write permissions (without changing any settings in Win). This is ultimately what I'd like to do.

Thanks for the help!

---

### Post by CharlesA on 2012-12-02
Running XP Pro or Home? If you are running Pro, it should be under tools > Options > scroll to bottom > use simple file sharing

---

### Post by erictherev on 2012-12-02
> **CharlesA said:**
> Running XP Pro or Home?

> **erictherev said:**
> I'm running XP Pro 32 SP3 on all of the other systems on the local network.

> **CharlesA said:**
> If you are running Pro, it should be under tools > Options > scroll to bottom > use simple file sharing

> **erictherev said:**
> I've run into this issue before, and it seems like I was able to get it to the point that, so long as Win/Ubuntu passwords match across the network, users could access anything on the file server that they were authorized to with read/write permissions (without changing any settings in Win). This is ultimately what I'd like to do.

I seem to recall the solution being in smb.conf, I just don't remember what the solution was. While playing with the Simple File Sharing in Windows might work on a small scale, it would be very time-consuming on a large scale, like in a corporate environment, and Linux is smarter than that. I still think the solution I've used in the past was in Samba.

Thanks for the help!

---

### Post by erictherev on 2012-12-02
Here's the results of a testparm I just ran:

```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
params.c:Parameter() - Ignoring badly formed line in configuration file: 
WARNING: Ignoring invalid value 'NT' for parameter 'max protocol'
Processing section "[Comics]"
Processing section "[Gaming]"
Processing section "[Guitar]"
Processing section "[ISOs]"
Processing section "[LEGO]"
Processing section "[Music]"
Processing section "[Setup]"
Processing section "[Torrents]"
Processing section "[Wallpapers]"
WARNING: The security=share option is deprecated
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        dos charset = 850
        unix charset = ISO8859-1
        workgroup = GALACTIC_EMPIRE
        server string = Imperial File Server
        security = SHARE
        map to guest = Bad User
        log file = /var/log/samba/%m.log
        max log size = 50
        acl compatibility = winnt
        server signing = auto
        domain master = No
        dns proxy = No
        ldap ssl = no
        idmap config * : backend = tdb
        use client driver = Yes

[Comics]
        comment = Comics and Graphic Novels
        path = /home/shared/Comics
        valid users = nomad, lupa
        read only = No

```

The following lines from this have me wondering:

```
WARNING: The security=share option is deprecated
```
```
Server role: ROLE_STANDALONE
```

---

### Post by erictherev on 2012-12-02
I found the solution to the password prompt here: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#OfficeServer]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#OfficeServer")
```
 **Initialize the Microsoft Windows password database with the new users:**

root# smbpasswd -a root
New SMB password: bigsecret
Reenter smb password: bigsecret
Added user root.

root# smbpasswd -a jackb
New SMB password: m0r3pa1n
Retype new SMB password: m0r3pa1n
Added user jackb.

root# smbpasswd -a maryo
New SMB password: secret
Reenter smb password: secret
Added user maryo.

root# smbpasswd -a ameds
New SMB password: mysecret
Reenter smb password: mysecret
Added user ameds.

```

Now, on to the user home directories..

Also, on one of the Win systems, I deleted the shortcuts to the server in My Network Places. Any ideas on how to get them to come back?

Thanks for the help!

---

