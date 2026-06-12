---
title: "How to configure Samba; google wont help"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by Hatsune Miku on 2011-06-07
Alright im trying to configure samba. My family has a lot of digital movies and we are going to move them all into a old Pentium 4 with a 2 tb hard drive. Now i would like to use samba (smb) to share the files. It will work both on my Macs and PCs in my house, now when i look at the syntax i freeze in fear LOL! I've never networked any type of windows network before and having windows network emulator on a unix machine makes me so confused (syntax wise). So could someone PLEASE give me a quick run down or ever write me a syntax.  

I'm running Ubuntu server x64 11.04. 

I would like it to share the home directory of the , have it be able for people to read/write to, you log on with a password/username, and last but not least NO GUEST LOG IN.

Thanks in advance!  Miku :)

---

### Post by Hatsune Miku on 2011-06-07
Bump

---

### Post by kalimojo on 2011-06-07
testparm -s
smbpasswd -a username


# Sample configuration file for the Samba suite for
Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You
should read the
# smb.conf(5) manual page in order to understand the
options listed
# here. Samba has a huge number of configurable
options most of which 
# are not shown in this example
#
# Any line which starts with a ; (semi-colon) or a #
(hash) 
# is a comment and is ignored. In this example we will
use a #
# for commentary and a ; for parts of the config file
that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run
the command
# "testparm -s" to check that you have not many any
basic syntactic 
# errors. 
#

#======================= Global Settings
=======================


[global]
# domain name is CHAPTER3 
workgroup = CHAPTER3

# printing is controlled by CUPS
load printers = yes
printing = cups
printcap name = cups

# set this server to be the domain Time Server
time server = yes

# passwd chat allows users to change their
domain/samba/unix passwords
# from their windows computers. This works !
passwd chat = *New*Password* \
%n\n*Re-enter*new*password* %n\n *password*changed*

# username map creates a one-one between windows names
and 
# unix names. the only entry is root = Administrator
# Only need this if your unix names and windows names
are different,
# which they are not and shouldnt be.
username map = /etc/samba/smbusers

#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each
machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
   max log size = 1000

# If you want Samba to only log through syslog then
set the following
# parameter to 'yes'.
;   syslog only = no

# We want Samba to log a minimum amount of information
to syslog. 
Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead.
If you want to 
log
# through syslog you should set the following
parameter to something 
higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the
admin a backtrace
   panic action = /usr/share/samba/panic-action %d

#####################

# What naming service and in what order should we use
to resolve host 
names
# to IP addresses
name resolve order = wins bcast hosts

#####################################################3
#  add user script delete user script etc etc
#####################################################3
#
# The following group of commands are used in
conjunction
# with an existing NT domain controller PDC.
# 
# We've seen that a Unix user is needed for each
Windows users allowed 
to log on # to the Samba server. In a small
organisation, it's not a 
problem to add them 
# manually and to keep the synchronisation manually
also. 
# But in large organisations, it's sometimes not easy
to perform all 
these
#  tasks manually, but because Samba is great it has
two parameters to
#  automatically add and remove  Unix users.
#
# These parameters are add user script and delete user
script. The 
value they take # is the name of a program or a script
wich takes a 
username as argument 
# and creates a Unix account with it. In the value you
type in, don't 
forget to
# use  the macro %u to represent the Unix user.
#
# This leads to something like this :
#
#  [global]
#   add user script = /usr/sbin/useradd %u -g smbusers
#   delete user script = /usr/sbin/userdel %u
#
# Here we use the standard Unix useradd and userdel
command to add or 
remove # the user. The flag -g is used to give the
name of the primary 
Unix group of 
# the newly created Unix user.
#
# Samba will run the 'add user script' command when a
user connect to 
it, 
# he's authenticated by the PDC and does not have a
corresponding Unix 
user
# id .  The 'delete user script' command is run when a
user connect to 
Samba
# doesn't exist on the PDC anymore but still have a
unix account.
#
# This will maintain the list of Unix users in
synchronization with the 
Domain user list.
#
# This apply to users which exist in the domain where
Samba is located 
but also to # any user defined in any domain trusted
by the domain 
where Samba is found
# (Of course allow trusted domains must be set on yes
to be able to 
create a unix #  account for members of other
domains.)

;add user script = /usr/sbin/useradd -m `%u`
;delete user script = /usr/sbin/userdel -r `%u`
;add group script = /usr/sbin/groupadd  `%g`
;delete group script = /usr/sbin/groupdel  `%g`
;add user to group script = /usr/sbin/usermod -G  `%g`
`%u`
;add machine script = /usr/sbin/useradd \ -s
/bin/false -d /dev/null 
`%u`

#######################################
# logon scripts
#######################################
# Each logon script should be stored at the base of
the [netlogon] 
share. 
# For example, if the base of the [netlogon] share is 
/export/samba/logon and the # logon script is
jeff.bat, the file should be located at 
# /export/samba/logon/jeff.bat. When a user logs on to
a domain that 
contains a # logon script, he or she will see a small
dialog that informs 
them that the script is # executing, as well as any
output the script 
generates in an MS-DOS-like box.
#
# One warning: because these scripts are loaded by
Windows and executed 
on
# the Windows side, they must consist of DOS formatted

carriage-return/linefeed
# characters instead of Unix carriage returns. It's
best to use a DOS- 
or
# Windows-based editor to create them.
#
# Here is an example of a logon script that sets the
current time to 
match that of 
# the Samba server and maps two network drives, h and
i, to individual 
shares on
#  the server:
#
#  Reset the current time to that shown by the server.
#  We must have the "time server = yes" option in the
#  smb.conf for this to work.
#
# echo Setting Current Time...
# net time \\hydra /set /yes
#
#  Here we map network drives to shares on the Samba
#  server
# echo Mapping Network Drives to Samba Server Hydra...
# net use h: \\hydra\data
# net use i: \\hydra\network
#
logon script = logon.bat

###################################
# roaming profiles
###################################
#
[http://www.oreilly.com/catalog/samba/chapter/book/ch06_06.html](http://www.oreilly.com/catalog/samba/chapter/book/ch06_06.html)
# Samba will provide roaming profiles if it is
configured for domain 
logons and you # provide a tree of directories pointed
to by the logon 
path option. This option is # # typically used with
one of the user 
variables, as shown in this example:
#
# [global]
#    domain logons = yes
#    security = user
#    workgroup = SIMPLE
#    os level = 34
#    local master = yes
#    preferred master = yes
#    domain master = yes
#
#    logon path =  \\knoppix\profile\%U
#
# We need to create a new share to support the
profiles, which is a 
basic disk
# share accessible only by the Samba process' user (
root). This share 
must be
# writeable, but should not be browseable. In
addition, we must create 
a directory
# for each user who wishes to log on (based on how we
specified our 
logon path
# in the example above), which is accessible only by
that user. For an 
added
# measure of security, we use the directory mode and
create mode 
options to
# keep anyone who connects to it from viewing or
altering the files 
created in
# those directories:
#
# [profile]
# comment = User profiles
# path = /export/samba/profile
# create mode = 0600
# directory mode = 0700
# writable = yes
# browsable = no
#
# Once a user initially logs on, the Windows client
will create a 
user.dat 
# ntuser.dat file - depending on which operating
system the client is 
running. The
# client then uploads the contents of the desktop, the
Start Menu, the 
Network
# Neighborhood, and the programs folders in individual
folders in the 
directory.
# When the user subsequently logs on, those contents
will be downloaded 
from
#  the server and activated for the client machine
with which the user 
is logging
# on. When he or she logs off, those contents will be
uploaded back on 
the server # until the next time the user connects.
#
# leaving logon path=  blank effectively disables
roaming profiles
# roaming profiles are disabled here
logon path = 

# automatically maps the users home drive to the
letter specified
# works with the [homes] section
logon drive = H:
domain logons = yes
preferred master = yes
wins support = yes

[homes]
valid users = %S
read only = no
browseable = no

[netlogon]
path=/data
writeable = no
browseable = no

[windows]
path=/windows
read only = no
writeable=yes
browseable=yes

[finances]
path=/data/finances
valid users = %G
read only = no
writeable = yes
browseable = yes
vfs objects = recycle

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
public = yes
guest ok = yes
writable = no
printable = yes
printer admin = root, @ntadmins

---

### Post by daxbau on 2011-06-07
do you need this filesystem to be mounted locally? 
if not - you can set up ubutnu on p4 and share theese files via vsftpd (could give you a very secure config example (and you can add a pam.db for users, that don't have to exist on the p4))

otherwise:

on the p4 machine you can share the drive (win net-drive) and mount it on the terminal machines (unix /etc/fstab)
//192.168.10.10/data/ /mnt/Bitsche/Drive_F cifs credentials=/root/smb/credentials,rw,iocharset=utf8,uid=1000,gid=1000 0 0

---

### Post by Hatsune Miku on 2011-06-07
> **daxbau said:**
> do you need this filesystem to be mounted locally? 
if not - you can set up ubutnu on p4 and share theese files via vsftpd (could give you a very secure config example (and you can add a pam.db for users, that don't have to exist on the p4))

otherwise:

on the p4 machine you can share the drive (win net-drive) and mount it on the terminal machines (unix /etc/fstab)
//192.168.10.10/data/ /mnt/Bitsche/Drive_F cifs credentials=/root/smb/credentials,rw,iocharset=utf8,uid=1000,gid=1000 0 0


I think a vsftpd would in the end be better. Could you please tell me what i would need to do?

---

### Post by daxbau on 2011-06-08
first of all
```

apt-get install vsftpd
```
then you can optionally generate a certificate
```
cd /etc/ssl/certs/
```
```
openssl req -x509 -nodes -days 7300 -newkey rsa:2048 \[FONT=monospace]
[/FONT]-keyout /etc/ssl/certs/vsftpd.pem -out /etc/ssl/certs/vsftpd.pem
```
now you can edit /etc/vsftpd/vsftpd.conf

take your time and read all the info. you can go to [http://en.gentoo-wiki.com/wiki/Vsftpd](http://en.gentoo-wiki.com/wiki/Vsftpd) to find at the bottom a script to generate your pam.db

use for example filezilla to connect

and dont't make a anonymous write to the server. you might get illegal stuff on your pc.

---

