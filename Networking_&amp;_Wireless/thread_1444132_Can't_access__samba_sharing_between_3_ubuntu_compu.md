---
title: "Can't access  samba sharing between 3 ubuntu computers"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by joaowojcikiewicz on 2010-03-31
Hello people.
First, I'm new on forums and I just came here to find some help with this problem, networking...
Well, my main computer hostname is *home*, and the others are *ubuntu* and *eduardo*.
In *home*, I try to configure samba, downloading it with "*sudo apt-get install samba*" and then downloading at the synaptic manager the *samba-common-bin* thing.
I shared my folders as ROOT in *home* and I cannot access from *ubuntu* and *eduardo*.
Then I googled and I found this site: 
> [http://dotgiri.com/2009/08/27/15-steps-to-configure-samba-on-ubuntu/](http://dotgiri.com/2009/08/27/15-steps-to-configure-samba-on-ubuntu/)
Well... I follow all steps and I can't access these files.
What I need to do to share files between these computers???

That's all, and please, sorry about some english mistakes, because I'm brazilian.

---

### Post by ant2ne on 2010-03-31
Try the samba link my signature. Give the steps a shot. If you have problems, lmk.

---

### Post by joaowojcikiewicz on 2010-04-01
> **ant2ne said:**
> Try the samba link my signature. Give the steps a shot. If you have problems, lmk.

That doesn't work T.T

---

### Post by ant2ne on 2010-04-01
> **joaowojcikiewicz said:**
> That doesn't work T.TOk, what didn't work? Did you get any error messages? There are alot of things that could be going wrong and you are not supplying any more information other than, "it doesn't work"

---

### Post by joaowojcikiewicz on 2010-04-01
I received various error messages when I was running the script, like:

> joaowojcikiewicz@ubuntu:~$ sudo /bin/smbadd
[sudo] password for joaowojcikiewicz: 
&#8220;Please enter the new system and samaba user&#8217;s name:&#8221;
test
&#8220;Please enter password for test:&#8221;
123456
&#8220;Making test a system and samba user&#8221;
&#8220;Enter the samba password twice. Hitting enter each time.&#8221;
123456
123456
Added user &#8220;test&#8221;.
&#8220;Verify the user is listed in the line below&#8221;
cat: /etc/samba/smbpasswd: No such file or directory
joaowojcikiewicz@ubuntu:~$ 



Also, here's my smb.conf

> #
# Sample configuration file for the Samba suite for Debian GNU/Linux.
#
#
# This is the main Samba configuration file. You should read the
# smb.conf(5) manual page in order to understand the options listed
# here. Samba has a huge number of configurable options most of which 
# are not shown in this example
#
# Some options that are often worth tuning have been included as
# commented-out examples in this file.
#  - When such options are commented with ";", the proposed setting
#    differs from the default Samba behaviour
#  - When commented with "#", the proposed setting is the default
#    behaviour of Samba but the option is considered important
#    enough to be mentioned here
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
# A well-established practice is to name the original file
# "smb.conf.master" and create the "real" config file with
# testparm -s smb.conf.master >smb.conf
# This minimizes the size of the really used smb.conf file
# which, according to the Samba Team, impacts performance
# However, use this with caution if your smb.conf file contains nested
# "include" statements. See Debian bug #483187 for a case
# where using a master file is not a good idea.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
;   wins server = w.x.y.z

# This will prevent nmbd to search for NetBIOS names through DNS.
   dns proxy = no

# What naming service and in what order should we use to resolve host names
# to IP addresses
;   name resolve order = lmhosts host wins bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0

# Only bind to the named interfaces and/or networks; you must use the
# 'interfaces' option above to use this.
# It is recommended that you enable this feature if your Samba machine is
# not protected by a firewall or is a firewall itself.  However, this
# option cannot handle dynamic or non-broadcast interfaces correctly.
;   bind interfaces only = yes



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
#   syslog only = no

# We want Samba to log a minimum amount of information to syslog. Everything
# should go to /var/log/samba/log.{smbd,nmbd} instead. If you want to log
# through syslog you should set the following parameter to something higher.
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

# "security = user" is always a good idea. This will require a Unix account
# in this server for every user accessing the server. See
# /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/ServerType.html
# in the samba-doc package for details.
#   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
   unix password sync = yes

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Ian Kahan <<kahan@informatik.tu-muenchen.de> for
# sending the correct chat script for the passwd program in Debian Sarge).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
   pam password change = yes

# This option controls how unsuccessful authentication attempts are mapped 
# to anonymous connections
   map to guest = bad user

########## Domains ###########

# Is this machine able to authenticate users. Both PDC and BDC
# must have this setting enabled. If you are the BDC you must
# change the 'domain master' setting to no
#
;   domain logons = yes
#
# The following setting only takes effect if 'domain logons' is set
# It specifies the location of the user's profile directory
# from the client point of view)
# The following required a [profiles] share to be setup on the
# samba server (see below)
;   logon path = \\%N\profiles\%U
# Another common choice is storing the profile in the user's home directory
# (this is Samba's default)
#   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
#   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

# This allows machine accounts to be created on the domain controller via the 
# SAMR RPC pipe.  
# The following assumes a "machines" group exists on the system
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u

# This allows Unix groups to be created on the domain controller via the SAMR
# RPC pipe.  
; add group script = /usr/sbin/addgroup --force-badname %g

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/Samba3-HOWTO/speed.html
# for details
# You may want to add the following on a Linux system:
#         SO_RCVBUF=8192 SO_SNDBUF=8192
#   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
#   domain master = auto

# Some defaults for winbind (make sure you're not using the ranges
# for something else.)
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash

# The following was the default behaviour in sarge,
# but samba upstream reverted the default because it might induce
# performance issues in large organizations.
# See Debian bug #368251 for some of the consequences of *not*
# having this setting and smb.conf(5) for details.
;   winbind enum groups = yes
;   winbind enum users = yes

# Setup usershare options to enable non-root users to share folders
# with the net usershare command.

# Maximum number of usershare. 0 (default) means that usershare is disabled.
;   usershare max shares = 100

# Allow users who've been granted usershare privileges to create
# public shares, not just authenticated ones
   usershare allow guests = yes

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
;   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
;   directory mask = 0700

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes
;   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;   comment = Users profiles
;   path = /home/samba/profiles
;   guest ok = no
;   browseable = no
;   create mask = 0600
;   directory mask = 0700

[printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   read only = no
   create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;   write list = root, @lpadmin

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes

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
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


---

### Post by ant2ne on 2010-04-01
```
cat: /etc/samba/smbpasswd: No such file or directory
```
Implies samba is not installed, or installed properly. Did you do the install part of my tutorial? Do an ls /etc/samba what is the output?

Your smb.conf wont work.

Goto the SAMBA SEVER section of the tutorial and perform those steps.

---

### Post by joaowojcikiewicz on 2010-04-01
Here's the output:

> joaowojcikiewicz@ubuntu:~$ ls /etc/samba
gdbcommands  smb.conf  smb.conf~  tls
joaowojcikiewicz@ubuntu:~$ 


And here's the terminal output for SAMBA SERVER, and I receive lots of error:

> joaowojcikiewicz@ubuntu:~$ sudo chmod +x /bin/smbadd
joaowojcikiewicz@ubuntu:~$ sudo /bin/smbadd
&#8220;Please enter the new system and samaba user&#8217;s name:&#8221;
secure
&#8220;Please enter password for secure:&#8221;
secur3
&#8220;Making secure a system and samba user&#8221;
&#8220;Enter the samba password twice. Hitting enter each time.&#8221;
secur3
secur3
&#8220;Verify the user is listed in the line below&#8221;
cat: /etc/samba/smbpasswd: No such file or directory
joaowojcikiewicz@ubuntu:~$ sudo /bin/smbadd
&#8220;Please enter the new system and samaba user&#8217;s name:&#8221;
guest
&#8220;Please enter password for guest:&#8221;
guest
&#8220;Making guest a system and samba user&#8221;
&#8220;Enter the samba password twice. Hitting enter each time.&#8221;
guest
guest
&#8220;Verify the user is listed in the line below&#8221;
cat: /etc/samba/smbpasswd: No such file or directory
joaowojcikiewicz@ubuntu:~$ sudo apt-get install samba samba-common smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
samba-common is already the newest version.
smbfs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joaowojcikiewicz@ubuntu:~$ sudo mkdir /data
mkdir: cannot create directory `/data': File exists
joaowojcikiewicz@ubuntu:~$ sudo mkdir /data/shares
mkdir: cannot create directory `/data/shares': File exists
joaowojcikiewicz@ubuntu:~$ sudo mkdir /data/shares/open
mkdir: cannot create directory `/data/shares/open': File exists
joaowojcikiewicz@ubuntu:~$ sudo mkdir /data/shares/secure
mkdir: cannot create directory `/data/shares/secure': File exists
joaowojcikiewicz@ubuntu:~$ sudo chmod -R 777 /data/share/open
chmod: cannot access `/data/share/open': No such file or directory
joaowojcikiewicz@ubuntu:~$ sudo chown -R guest /data/share/secure
chown: invalid user: `guest'
joaowojcikiewicz@ubuntu:~$ sudo chown -R secure:securegroup /data/share/secure
chown: invalid user: `secure:securegroup'
joaowojcikiewicz@ubuntu:~$ sudo chmod -R 751 /data/share/secure
chmod: cannot access `/data/share/secure': No such file or directory
joaowojcikiewicz@ubuntu:~$ 


---

### Post by ant2ne on 2010-04-01
ahh you caught a typeo in my script

```
sudo chmod -R 777 /data/share/open
```
should be
```
sudo chmod -R 777 /data/shares/open
```
and
```
sudo chmod -R 751 /data/share/secure
```
should be
```
sudo chmod -R 751 /data/shares/secure
```
I updated the blog. Run these commands again.

You still need a working smb.conf file.

```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.original
sudo nano /etc/samba/smb.conf
```
(Copy and Paste the following into that smb.conf)

    [global]

    netbios name = SambaServer

    name resolve order = host wins lmhosts bcast

    server string = My File Server

    workgroup = workgroup

    encrypt passwords = true

    wins support = true

    guest account = guest

    map to guest = guest

    guest ok = yes

    [Open]

    create mask = 0777

    directory mask = 0777

    path = /data/shares/open

    read only = no

    [Secure]

    create mask = 0751

    directory mask = 0740

    path = /data/shares/secure

    read only = no

    write list = secure

(End of copy and paste)

---

### Post by joaowojcikiewicz on 2010-04-01
But what about this:

> &#8220;Verify the user is listed in the line below&#8221;
cat: /etc/samba/smbpasswd: No such file or directory
joaowojcikiewicz@ubuntu:~$ 


When I try to add *guest* and *secure* this error showed up.

---

### Post by joaowojcikiewicz on 2010-04-01
wait, I read this site:

> [http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

And it work!
to IP address, I put *home*'s ip, 192.168.1.100
to port, 22
to folder I put /media/TERA/Programas (programs folder)
and username joaowojcikiewicz, because I have already configured this on smbpasswd

Thank you so much ;P

---

### Post by ant2ne on 2010-04-01
GET A WORKING SMB.CONF FIRST

I think this line...
```
encrypt passwords = true
```
...will generate the file...
```
/etc/samba/smbpasswd
```
You are trying to add users to an unworking system and then wondering why you can't add the users. Lets take this one step at a time. Maybe I need to clearify on the blog site the proper steps. For now, Modify the smb.conf file and then restart samba ```
/etc/init.d/samba restart
``` If we get no errors then we can think about adding users.

---

### Post by Objekt on 2010-04-01
Groovy.  I can't wait to try this when I get home.  I have been preoccupied with other Ubuntu issues, but most of them are now solved & I can dig in to sharing stuff over my home network.

I don't have a burning "need" to share folders/files/etc. to the Windows machines on my home LAN, but I want to make it work anyway.  I just like tinkering with things.  Also, I run Ubuntu most of the time.  Steam and one or two other Windows-only games are the only reason I use Windows XP any more at all.

I have gotten as far as marking a couple of folders as "Shared" in Nautilus, but they aren't accessible from the Windows machines yet.  They can see my Ubuntu machine as a member of the network workgroup, but can't access anything.  I'm sure it's a simple matter of permissions or logins or something like that.

---

### Post by ant2ne on 2010-04-01
Thanks for this opportunity to troubleshoot the steps in my tutorial. I have modified the text to be a little more explanatory to avoid this confusion in the setup steps. LMK if there are further problems or confusion.

---

### Post by ant2ne on 2010-04-01
> **joaowojcikiewicz said:**
> wait, I read this site:



And it work!
to IP address, I put *home*'s ip, 192.168.1.100
to port, 22
to folder I put /media/TERA/Programas (programs folder)
and username joaowojcikiewicz, because I have already configured this on smbpasswd

Thank you so much ;PDude, that is ssh file sharing using scp. Not the same thing as samba. But hey if it works for you...

---

