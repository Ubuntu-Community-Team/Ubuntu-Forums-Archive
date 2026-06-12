---
title: "How to remove Login prompt from Samba File Server."
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by AsherSevyn on 2010-04-05
I have recently installed Ubuntu as a file server on a windows domain.

The Ubuntu machine is the only Linux box on the network.

Everything works fine except that when users browse and enter the Ubuntu share they are prompted for a user name and password. The funny thing is that you can enter any jibberish and it just lets you right in. We have no need for any sort of protection on this server. How do I turn the login prompt off? 

Here is my Smb.conf

#
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

  workgroup = KMLLC
            
# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)

# Windows Internet Name Serving Support Section:
# WINS Support - Tells the NMBD component of Samba to enable its WINS Server
#   wins support = no

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

   security = ADS


Realm = KMLLC.KNOWLEDGEMOSAIC.COM 

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

   unix password sync = no



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
;   domain logons = no 
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

;   idmap uid = 50-9999999999 
;   idmap gid = 50-9999999999

    idmap backend = lwopen
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
;[homes]
;   comment = Home Directories
;   browseable = no

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;   read only = yes

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
#    cdrom share is accesed. For this to work /etc/fstab must contain
#    an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#    is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

---

### Post by Morbius1 on 2010-04-05
What's even stranger is that you have no shares defined in your smb.conf.

Are you using Nautilus-share by any chance:

Open **Terminal**
Type **net usershare info**
Type **sudo net usershare info**

---

### Post by AsherSevyn on 2010-04-05
I have defined my share in the GUI by right clicking My Docs and specifying share.

I am not using Nautilus.

Yeah everyone on the network can see the share on the Ubuntu server. They can also write and delete files.

Could you show me the proper Samba entry for specifying a share?

---

### Post by AsherSevyn on 2010-04-05
Here is the result for **sudo net usershare info.**

[documents]
path=/home/ntilbrook/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/ubuntu share is not a well formed usershare file.
info_fn: Error was Path is not a directory.
ntilbrook@ufserver:~$

---

### Post by capscrew on 2010-04-05
> **AsherSevyn said:**
> Here is the result for **sudo net usershare info.**

[documents]
path=/home/ntilbrook/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

info_fn: file /var/lib/samba/usershares/ubuntu share is not a well formed usershare file.
info_fn: Error was Path is not a directory.
ntilbrook@ufserver:~$

This is doing things the hard way.  It is how (and where) you would define shares using a GUI interface.  

You should add the share to the end of your /etc/samba/smb.conf file.  Here is the basic format:```

[name of share]
path = /path/to/share
guest ok = yes

``` 

I recommend you see [**_Samba by Example _**]("http://www.samba.org/samba/docs/man/Samba-Guide/").

---

### Post by Morbius1 on 2010-04-05
capscrew, I knew a day would come when you and I would disagree on something. Given that he's creating a public share I see no reason why he can't use Nautilus-share:

> [documents]
path=/home/ntilbrook/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=y

Regardless of what method he uses I still don't know why he is being prompted for authentication on a public share.

---

### Post by AsherSevyn on 2010-04-05
I do recall specifying y for guest access: guest_ok=y

but It's not in the Smb.conf.

Would y instead of yes make a difference in the: "guest_ok" line?

Where can I find the file to configure which displays **net usershare info?**

And do I have to install Nautilus or is it native to Ubuntu 9.1?

Thanks for you're help guys, I would be lost without you.

~Ash

---

### Post by capscrew on 2010-04-05
> **Morbius1 said:**
> capscrew, I knew a day would come when you and I would disagree on something. ...


Morbuis I don't disagree with your way.  In some ways your knowledge is greater than mine.  All my Samba shares are configured with smb.conf.  

It certainly can be done the way the OP has done it.  It's just more obscure.

> 
Regardless of what method he uses I still don't know why he is being prompted for authentication on a public share.

I'll bet he doesn't have guest set up correctly

---

### Post by Morbius1 on 2010-04-05
I will defer to capscrew on this one. His beans are hidden so the rest of us won't feel inadequate :smile:


BTW, **net usershare info** is the way you find out how your shares are set up using Nautilus-share or Thunar-share. If you didn't use nautilus or thunar to set up your shares then I don't know how it was created.

---

### Post by capscrew on 2010-04-05
> **AsherSevyn said:**
> I do recall specifying y for guest access: guest_ok=y

but It's not in the Smb.conf.

Would y instead of yes make a difference in the: "guest_ok" line?

Where can I find the file to configure which displays **net usershare info?**

And do I have to install Nautilus or is it native to Ubuntu 9.1?

Thanks for you're help guys, I would be lost without you.

~Ash

Ahhh, I see now.  You ARE using Nautilus. It is the default file manager in Gnome.  I misunderstood how you configured your shares.

All of the configuration is stored at /var/lib/samba

---

### Post by capscrew on 2010-04-05
> **Morbius1 said:**
> I will defer to capscrew on this one. His beans are hidden so the rest of us won't feel inadequate :smile:

...


No no Morbius1.  You know more than I do in this area.  The OP is using a GUI and I missed that.  To me a Ubuntu server has NO GUI.  I believe he is using Nautilus (Gnome) not Thunar (KDE)

---

### Post by AsherSevyn on 2010-04-05
So which of Documents /ubuntu Share do I enter to change "y" to "Yes" in the guest configuration file? What is the name of the file that I must edit?

---

### Post by capscrew on 2010-04-05
> **AsherSevyn said:**
> So which of Documents /ubuntu Share do I enter to change "y" to "Yes" in the guest configuration file? What is the name of the file that I must edit?

As far as I know the files at /var/lib/samba are binary and can't be directly edited.  You need to use the GUI to edit them.

---

### Post by AsherSevyn on 2010-04-05
Ok so I changed "y" to "yes" in the Ubuntu share file.

Does the Acl look right?

#VERSION 2
path=/home/ntilbrook/Documents/untitled folder
comment=
usershare_acl=S-1-1-0:F
guest_ok=yes

---

### Post by Morbius1 on 2010-04-05
No. Unlike smb.conf, usershare is very picky about syntax.

If you go to /var/lib/samba/usershares you will see the file - documents.

For reasons known only to the developers what looks like this in **net usershare info**:
> [documents]
path=/home/ntilbrook/Documents
comment=
usershare_acl=Everyone:F,
guest_ok=yLooks like this in /var/lib/samba/usershares/documents:
> #VERSION 2
path=/home/ntilbrook/Documents
comment=
usershare_acl=S-1-1-0:F
guest_ok=yTrust me they mean the same thing.

There is nothing wrong with the share the problem is with something else. What I completely missed when I read your original post is this:
> realm = KMLLC.KNOWLEDGEMOSAIC.COM
    security = ADS
This is way beyond my area of expertise but doesn't this type of setup require a password server somewhere in the network. Maybe that's the password mechanism that's not working properly and not the samba share.

---

### Post by AsherSevyn on 2010-04-05
Yeah, this is a domain based share.

Our Domain Controller is a windows 2003 Server.

I had to authenticate onto AD through Ubuntu to set up the share.

---

### Post by theozzlives on 2010-04-05
True servers don't use GUI. That was Windows idea (and a stupid one at that). Use smb.conf, set your smbpasswd, and set your credentials in Windows. You'll be fine.

---

### Post by capscrew on 2010-04-05
> **AsherSevyn said:**
> Yeah, this is a domain based share.

Our Domain Controller is a windows 2003 Server.

I had to authenticate onto AD through Ubuntu to set up the share.

I saw that in your previous threads posted.  The problem is now revealed (with no resolution here).  It is a user authentication problem.  The answer is that Samba (the smbd daemon) is not provided what is needed to authenticate.  Yes *guest *is a form of authentication. 

This really demonstrates how one problem can lead to others.  You really need the help of **jrssystemsnet**.  He has previously installed AD controlled Samba shares.  My guess is that he will require you to configure all the shares via smb.conf.

---

### Post by Morbius1 on 2010-04-05
theozzlives,

I don't have a religious affiliation with either method. But I do know that he has created a public share. Using nautilus-share or classic-share ( smb.conf) he should not be asked for authentication to a public share.

Me thinks the problem is somewhere else. ;)

EDIT: capscrew , thanks for clearing that up. I really need to read the original posts more carefully.

---

### Post by AsherSevyn on 2010-04-05
Yeah  jrssystemsnet helped me set up the domain share. He was really helpful. The problem was when non-domain admins tried to access the share. Since my account 
is an admin account I can browse the files no problem but when end users try to
access it they are prompted for the login.

---

### Post by capscrew on 2010-04-05
> **AsherSevyn said:**
> Yeah  jrssystemsnet helped me set up the domain share. He was really helpful. The problem was when non-domain admins tried to access the share. Since my account 
is an admin account I can browse the files no problem but when end users try to
access it they are prompted for the login.

So you need to figure out what is a local (to the host) and what is a domain wide account. :-)  Admin or not is also in the equation.  This is an AD issue first.  Usershares work just like shares configured via smb.conf.  They both require authentication of the user to some database.  Did you set samba up to authenticate all types of users to Samba?

Once again talk to **jrssystemsnet **he seems like he would know the answer.

---

### Post by AsherSevyn on 2010-04-06
Yeah after  jrssystemsnetand I got the share working  everything seemed ok and  jrssystemsnet was gone. Any idea where I can find him?

---

### Post by capscrew on 2010-04-06
> **AsherSevyn said:**
> Yeah after  jrssystemsnetand I got the share working  everything seemed ok and  jrssystemsnet was gone. Any idea where I can find him?

You could PM him.  Go back to the thread with him and click on his name and look for *private message*.

---

