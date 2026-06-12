---
title: "Ubuntu 9.10 - Is Samba Configuration Still Necessary in 9.10?"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by umechanism on 2010-09-02
I'm really confused with all the new printers setups available for Linux/Windows networks.  I have my printer connected to my Linux desktop which is on the same network as all my Windows laptops and the laptops could print (via Samba) to the printer.  All was working perfectly.

Then I upgraded from 8.10 to 9.04 then to 9.10.  Now I cannot print or see my shares anymore.  9.10 has a nice GUI for printer configuration under System>Administration>Printing that wasn't there in 8.10...so I went here to configure my printer.  But, there is still the /etc/samba/smb.conf file out there that seems to need configuring as well.  Aren't these two things the same?  If I configure printer sharing with the GUI, do I still need to manually configure the smb.conf file too?

Just as a test, I went to my Vista laptop, found the Printers, and tried to print a test page to my printer.  Nothing happened.  Then, I tried browsing out to my Linux desktop via the network.  I could see it but when I tried to browse I was prompted for a password.  I entered every password I knew of...none of them worked.  What the heck?

I even tried to restart the samba server by using /etc/init.d/samba restart but I get this error:
```
@ubuntu-dell:~$ sudo /etc/init.d/samba restart
sudo: /etc/init.d/samba: command not found

```  I checked Synaptic Package Manager and Samba's server and client appeared to be installed.  I even reinstalled it.  No change.

Like I said, this used to work great.  I'm really, really, really confused.  Any help would be appreciated.

---

### Post by clrg on 2010-09-02
Try /etc/init.d/smbd instead of /etc/init.d/samba, that might help a lot.

Also, I recomment you don't use GUIs to configure services. I know they can come in handy and save some time, but they tend to mess up things. I think it'd be best if you stick to smb.conf.

During the upgrade, I'm sure you were prompted if smb.conf were to be overwritten with the package maintainer's version. If you chose yes, you need to rewrite it.

---

### Post by endotherm on 2010-09-02
starting with 9.x (forget which) the init.d approach was largely replaced with teh 'service' command
```
sudo service smbd restart
```
```
sudo service <servicename> <start|stop|status|restart>
```

if you are confused about the service name, one way to get by is to run ps -ef to find the name of the executable tied to that service (samba => smbd).

---

### Post by dca on 2010-09-02
Are you sure 'service' is used? I could've sworn it still requires the 'chkconfig' (which installs insrv) package in 9.04 - current repos?

---

### Post by endotherm on 2010-09-02
> **clrg said:**
> Try /etc/init.d/smbd instead of /etc/init.d/samba, that might help a lot.

Also, I recomment you don't use GUIs to configure services. I know they can come in handy and save some time, but they tend to mess up things. I think it'd be best if you stick to smb.conf.

During the upgrade, I'm sure you were prompted if smb.conf were to be overwritten with the package maintainer's version. If you chose yes, you need to rewrite it.
samba is now kind of split between 2 paradigms: classic text based, and the gui Nautilus-share. Nautilus-share is only half a framework however so it uses some of the configuration from the smb.conf, and adds some per user information about shares and whatnot. it can be useful, but making it work with traditional methods for samba configuration and troubleshooting can be a real pain. my best advice is to pick one paradigm and stick with it. I generally recommend the text based approach, but whatever you wanna do.

---

### Post by endotherm on 2010-09-02
> **dca said:**
> Are you sure 'service' is used? I could've sworn it still requires the 'chkconfig' (which installs insrv) package in 9.04 - current repos?
no idea. i believe the change relates to the integration of the new init system, but beyond that, it's out of my depth. I have noticed however that some older init.d scripts are still required and have not been replaced by service varients. for instance, you still need to 
'/etc/init.d/networking restart'. the op is using karmic, and yes, i am sure that lucid is not the first version of ubuntu to use the 'service' command. jaunty may still use the old init system.

---

### Post by umechanism on 2010-09-03
So can I delete the samba configuration file (text file) and just use the Gui?  Yeah, still confused here.

Also, shouldn't there be a "samba" running in my processes?  I do not see one.

Thank you.

---

### Post by clrg on 2010-09-03
> **umechanism said:**
> So can I delete the samba configuration file (text file) and just use the Gui?  Yeah, still confused here.

Also, shouldn't there be a "samba" running in my processes?  I do not see one.

Thank you.

Don't delete smb.conf! Samba needs it.

The Samba process is called "smbd".

---

### Post by umechanism on 2010-09-03
I checked the processes.  There isn't anything, "smbd" or "samba" running.  See attached.

---

### Post by clrg on 2010-09-03
I don't like that thing you are using. If you want to check for a process, open a terminal and run

```
ps -ef
```

If you want to search for a particular one, do

```
ps -ef | grep <proc>
```

For example:

```
ps -ef | grep smbd
```

You can also check whether a service is running or not using the service command:

```
service smbd status
```

If its not running, start it

```
sudo service smbd start
```

---

### Post by umechanism on 2010-09-03
ps -ef found:
root      3101  3097  0 07:54 ?        00:00:00 smbd -F

so it looks like it is running even though, "Processes" does not show it.  Okay...now that it is running, back to my original question of GUI vs smb.conf.  Do the changes I make to smb.conf overide, compliment, or have no affect on settings made in the GUI under System>Administration>Printing?

---

### Post by clrg on 2010-09-03
[QUOTE=umechanism]
Okay...now that it is running, back to my original question of GUI vs smb.conf. Do the changes I make to smb.conf overide, compliment, or have no affect on settings made in the GUI under System>Administration>Printing?[/QUOTE]

[QUOTE=endotherm]samba is now kind of split between 2 paradigms: classic text based, and the gui Nautilus-share. Nautilus-share is only half a framework however so it uses some of the configuration from the smb.conf, and adds some per user information about shares and whatnot. it can be useful, but making it work with traditional methods for samba configuration and troubleshooting can be a real pain. my best advice is to pick one paradigm and stick with it. I generally recommend the text based approach, but whatever you wanna do.[/QUOTE]

I recommend you use the text based approach. I've had many problems with people mixing config files with GUI tools. The most stable and persistent method to configure something is to write a configuration file(s).

---

### Post by umechanism on 2010-09-03
I'm taking the text approach but now, after some changes, I can't see my Ubuntu machine on my network from my Vista laptop.  Do you see anything odd in my smb.conf file:

```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = mshome1971

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
  wins support = yes

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
  #wins server = w.x.y.z

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
   security = share

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
  load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   printcap name = cups
#I added the next line per instructions on the user forum.
use client driver = yes

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
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

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

[test]
path = /home/michael/test
available = yes
valid users = michael
read only = no
browsable = yes
public = yes
writable = yes

```

---

### Post by clrg on 2010-09-03
Limit your domain name to 8 characters. Don't use numbers.

---

### Post by umechanism on 2010-09-03
Why?  Is there a specific naming convention?

---

### Post by clrg on 2010-09-03
There is. Not more than 8 characters, no special characters, no numbers.

---

### Post by redmk2 on 2010-09-03
> **clrg said:**
> There is. Not more than 8 characters, no special characters, no numbers.

Are we talking about this?```
workgroup = mshome1971
```

Where does it state that it can't be more than 8 characters and no numbers?

---

### Post by clrg on 2010-09-03
Yes we are. I think its some kind of restriction in netbios, I'm not sure. Google it yourself :)

---

### Post by Morbius1 on 2010-09-03
Have we moved away from a printer issue to a general file sharing issue?

You have two peculiar option in your smb.conf:
> security = SHARE
wins support = Yes

You can use share level security I suppose but the modern default is now "USER". and "wins support = yes" has turned your linux box into a wins server. Nothing wrong with that but you'll need to set that box with a static ip address and then configure every other box on the network to point to it. Was this an experiment to try to resolve your issue?

There is a netbios name restriction of 15 characters, there is a share name restriction of 12 character ( doesn't really apply unless you have a Win98 box in your network ) but I never heard of an 8 character limit on WORKGROUP name.

---

### Post by redmk2 on 2010-09-03
> **clrg said:**
> Yes we are. I think its some kind of restriction in netbios, I'm not sure. Google it yourself :)

You think?  No guessing here.  The OP wasn't asking for your "best guess".

I did Google it and the only restriction I can see is 15 characters.  See here:> "Samba workgroup names need to be limited to 15 characters. If it is longer than 15 characters samba will truncate. Not too much of an issue but if the user ever looks in /var/log/messages then they will see a significant number of error messages about the issue."

---

### Post by umechanism on 2010-09-03
> **Morbius1 said:**
> Have we moved away from a printer issue to a general file sharing issue?

You have two peculiar option in your smb.conf:

You can use share level security I suppose but the modern default is now "USER". and "wins support = yes" has turned your linux box into a wins server. Nothing wrong with that but you'll need to set that box with a static ip address and then configure every other box on the network to point to it. Was this an experiment to try to resolve your issue?

There is a netbios name restriction of 15 characters, there is a share name restriction of 12 character ( doesn't really apply unless you have a Win98 box in your network ) but I never heard of an 8 character limit on WORKGROUP name.

My peculiar options are really just pulling guesses out of the air.  I am having trouble understanding all of this.  I changed my workgroup to, "mshome", "wins support = no" and set security back to, "user".  

Now, from a Vista laptop, I can browse to my share, "/home/me" which is good.  However, when I try to add a new printer in Vista (by Adding New Network Printer and browsing out to my Ubuntu machine), I can see a "Printer Folder" I can browse into from Vista but I can not see any printers inside.  It is empty.

Getting closer.  Any ideas?

---

### Post by Morbius1 on 2010-09-03
*[1] Make sure the Ubuntu attached printer works on Ubuntu itself*

*[2] Samba if configured correctly ( in my opinion ) should only be used as a pass-through to CUPS. You need to make sure the printer is shared and published:*

Step 1: Enable Sharing of that Printer.
Administration > Printing > Right Click the attached printer > Properties > Policies
Check Enabled, Accepting Jobs, and Shared

Step 2: Enable Publishing of the Shared Printer
Administration > Printing > Server > Settings > Check "Publish Shared Printers connected to this system"

*[3] You need to make sure all of the samba related services are running:*
```
sudo service smbd status
sudo service nmbd status
```If they are not running start them:
```
sudo service smbd start
sudo service nmbd start
```*[4] If you don't want to be pestered with prompts for username and passwords then you only need to change one entry in smb.conf:*
> [printers]
   comment = All Printers
   browseable = yes
   path = /var/spool/samba
   printable = yes
[COLOR=Blue]    guest ok = yes[/COLOR]
   read only = yes
   create mask = 0700Then restart all services:
```
sudo service smbd restart
sudo service nmbd restart
```Now, from the Ubuntu machine that has the printer, issue the following command and see if the printer is listed:
```
smbtree
```If it is then see if Vista can now browse to that printer.

---

### Post by umechanism on 2010-09-03
I made all the changes you suggested then coded, "smbtree".  Here is the result:

```
michael@ubuntu-dell:~$ smbtree
Enter michael's password: 
MSHOME
	\\UBUNTU-DELL    		ubuntu-dell server (Samba, Ubuntu)
		\\UBUNTU-DELL\michael        	Home directory of michael
		\\UBUNTU-DELL\IPC$           	IPC Service (ubuntu-dell server (Samba, Ubuntu))
		\\UBUNTU-DELL\print$         	Printer Drivers
		\\UBUNTU-DELL\homes          	
	\\HPMEDIAVAULT   		HPMediaVault
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_ACCESS_DENIED
michael@ubuntu-dell:~$ 


```

I have a HP Deskjet F4180 printer that I can print to from the Ubuntu computer but I do not see it listed.  I rebooted the Ubuntu machine and still no change.

Edit:  I just checked Vista and I cannot see the printer connected to the Ubuntu machine.

---

### Post by Morbius1 on 2010-09-03
Go into smb.conf and place a # in front of these two lines:
   >  printcap name = cups
    use client driver = YesSo that it looks like this:
>  #printcap name = cups
    #use client driver = Yes
then restart smbd.

---

### Post by umechanism on 2010-09-03
I made the change, rebooted the machine, then tried adding the printer from my Vista laptop.  Still, no printer is visible.  I can browse out to the Ubuntu based share from Vista but I just can't find the printer.  The printer folder is empty.

The changes I made are shown here:
```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = mshome

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
  wins support = no

# WINS Server - Tells the NMBD components of Samba to be a WINS Client
# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both
  #wins server = w.x.y.z

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
   security = user

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
  load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
   printing = cups
   #printcap name = cups
#I added the next line per instructions on the user forum.
#use client driver = yes

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
 #[homes]
  #comment = Home Directories   
  #browseable = yes

[homes]
path = /home/michael
available = yes
valid users = michael
read only = no
browsable = yes
public = yes
writable = yes


# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
   read only = no

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0775

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0775

# By default, \\server\username shares can be connected to by anyone
# with access to the samba server.  Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# This might need tweaking when using external authentication schemes
   valid users = %S

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
   #comment = All Printers
   #browseable = yes
   #path = /var/spool/samba
   #printable = yes
   #guest ok = yes
   #read only = yes
   #create mask = 0700

[printers]
path = /var/spool/samba
printable = yes
guest ok = yes
browseable = yes
printer name = HPDeskjetF4180
comment = Ubuntu Printer
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


```

---

### Post by Morbius1 on 2010-09-04
I keep trying to reset you back to the default samba configuration and you keep going where no man has gone before:
> [printers]
path = /var/spool/samba
printable = yes
guest ok = yes
[COLOR=Blue] browseable = yes[/COLOR]
[COLOR=Blue] printer name = HPDeskjetF4180[/COLOR]
[COLOR=Blue] comment = Ubuntu Printer[/COLOR]
read only = yes
create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
[COLOR=Blue]    browseable = yes[/COLOR]
[COLOR=Blue]    read only = yes[/COLOR]
   [COLOR=Blue]guest ok = no[/COLOR]Since we are at an impasse let's try not using samba at all. On Vista don't browse for it. Try either one of these two methods either by machine-name or by ip address :

Method1:
```
\\ubuntu-dell\HPDeskjetF4180
\\192.168.0.100\HPDeskjetF4180

```Method2:
```
ipp:\\ubuntu-dell:631\printers\HPDeskjetF4180
ipp:\\192.168.0.100:631\printers\HPDeskjetF4180
```[COLOR=Blue]*I'm not sure at this moment what direction the "/" should be on windows when using ipp. The Unix way is "ipp://" but windows likes to do things reversed.*[/COLOR] [COLOR=Blue]*Try it both ways.*[/COLOR]

If that doesn't work , especially if you use ip addresses, I don't know what to tell you.

BTW, there is no "printer folder" in samba. There is a "printers$" share which has nothing of interest in it and a "printers" folder". Despite the fact that you tried to make it browseable, it is in fact not browseable - samba will ignore your option

---

