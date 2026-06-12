---
title: "Samba from outside of LAN"
date: 2009-09-19
forum: Networking &amp; Wireless
---

### Post by x5x_tim on 2009-09-19
Hi,

I am currently doing this project with a friend, for wich we need a work-space. We're using MS Office OneNote as some sort of project book, and we both want to acces it.
I've got an old pc to run Ubuntu for me a while ago, that does all sorts of server-ish things. 
That's how I got notice of samba, and I've used the pc as a network drive since then.
Everething works great, but now I want to have my friend connect to that share (without the help of hamachi or that kind of programs). 

So I've added the following NAPT entries:

12 Temp 10.0.0.2:137 unspecified:137 udp NONE
13 Temp 10.0.0.2:138 unspecified:138 udp NONE
14 Temp 10.0.0.2:139 unspecified:139 tcp NONE
15 Temp 10.0.0.2:445 unspecified:445 tcp NONE

(The trained eye will notice that these are entries 12 up to and including 15, so I kinda know how this NAPT thing works.)

However, when I tell my friend to try to connect to \\myip\sharename , he gets a timeout. When I try a portscan from outside the network ([RadioToolbox]("http://www.radiotoolbox.com/online_tools/cantheygetin.php")) I get a time-out.

So, does samba block outsiders, or am I doin' something wrong with the routing?

Here's my samba configuration: (pretty much basic)
```
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

create mask = 0644
directory mask = 0755

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP

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



I hope someone can help me :)

x5x_tim

---

### Post by pdc124 on 2009-09-19
try reposting your samba config with 
grep ^[A-Za-z\ ] /etc/samba/smb.conf

ie any line beginning with a character or a space 
to remove the comment lines.
ten its easier to see what is happening

---

### Post by x5x_tim on 2009-09-19
```
workgroup = WORKGROUP
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes
   comment = All Printers
   browseable = no
   path = /var/spool/samba
   printable = yes
   guest ok = no
   read only = yes
   create mask = 0700
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

```

Here it is :) (Sorry, didn't know I could do that :mrgreen:)

x5x_tim

---

### Post by x5x_tim on 2009-09-19
Nobody with a bit of samba experience?

---

### Post by pdc124 on 2009-09-19
have a read of [http://www.webmasterworld.com/forum40/1686.htm](http://www.webmasterworld.com/forum40/1686.htm)

not likely to be straightforward. 
you may be better with ssh /winscp or subversion to share documents

if you do get samba working let us know

---

### Post by x5x_tim on 2009-09-19
Thanks for that link. I'll look into it tomorrow :)

x5x_tim

---

### Post by nautilus on 2009-09-19
Well, the first thing I would do is ensure there's connectivity between the two endpoints.

For starters one could login to the samba server, disable samba for a moment, then run:

```
$ sudo nc -l -p 139
```

(That program is called Netcat, which you can install with your apt of choice)

Then on the remote end, telnet to the IP on that port.  That won't only test your NAT forwarding, but it'll also ensure the Samba server in question has a route to the remote endpoint.

That said, as I understand it, SMB was intended for use strictly on a LAN.  NMB for example broadcasts exclusively on LAN via multicast, last I checked.  Still, provided the TTL of SMBD and of course the Win32 client at the remote location is sufficiently high enough to make the hops between ISPs and such, it should work.  That said, are you sure you really want to run a file sharing protocol intended for a controlled ("trusted") environment over a publically used network?

sshfs may be a little more secure on the network standpoint, but takes a bit more setup and care on the server filesystem side.

---

### Post by x5x_tim on 2009-09-20
Thank you, I'll try that.
Yes, I'm pretty sure I want it this way. I'll only have files there that need to be public, so I don't mind (and samba has an option to only allow local users in, doesn't it?)
If these things don't work out, I'll try to make a win app that SSH's in the pc with samba installed, and just check whether local or remote is newer and sync it.
So thanks for the help, I'm going to disable samba and check the route :)

x5x_tim

---

### Post by x5x_tim on 2009-09-20
Mmmm, that's wierd...

I've stopped samba and started netcat:
[IMG]http://www.easy-upload.nl/index.php/file/94ab5dd2d1949e[/IMG]

When I try to connect (from my LAN first, just in case) to 10.0.0.2:139, Windows telnet ignores the port and just tries to connect to 23 :P
But when I start PuTTY, and set it to telnet 139 (I even deleted my username in the Data>Connections>Auto login option) PuTTY go to xterm for a split second, shows 10.0.0.2 - PuTTY in the top bar, and just exits. (if I connect with SSH mode active I get a connection refused, RAW does the same as telnet, but shows (inactive) in the top bar while closing and Rlogin does the same as telnet)

I'm getting more confused every second (A)

x5x_tim

---

### Post by badger_fruit on 2009-09-20
Good morning
To get samba working on my Linux machines, I simply copy and paste the template file below:-

```

[global]
        printing = cups
        printcap name = cups
        cups options = raw
        map to guest = Bad User
        include = /etc/samba/dhcp.conf
        usershare allow guests = Yes
        netbios name = MYCOMPUTERNAME
        workgroup = MYWORKGROUP
        server string = "COMPUTER DESCRIPTION"
        name resolve order = bcast host lmhosts wins

[A_SHARE]
        comment = SHARE COMMENTS
        path = /path/to/share
        guest ok = yes
        read only = no
        force user = name_of_local_user

```I copied this into my /etc/samba/smb.conf (over-writing whatever was in there originally), restarted the samba service and then could browse, add/delete/move files in there.  Files I changed/created took their ownership from the name_of_local_user.

If I alter my firewall to allow TCP ports 137 to 139 onto the server, I can then remotely connect to them from outside of my LAN.

To access you can't use \\computername\share unless you've added an entry in the hosts file on the remote computer (Windows: C:\Windows\System32\etc\drivers\hosts; Linux: /etc/hosts).  You could also use \\public_ip_or_internetDNS_name\share

I hope this helps.

---

### Post by x5x_tim on 2009-09-20
Wow! Thanks! Totally unexpected :D

Gonna try it right away!

---

### Post by badger_fruit on 2009-09-20
Cool, good luck!
[COLOR=Red]**oh, if you do open your SMB to the evil internet, be sure to restrict on your firewall what IP addresses can see it!!**[/COLOR]

---

### Post by x5x_tim on 2009-09-20
> **badger_fruit said:**
> Cool, good luck!
[COLOR=Red]**oh, if you do open your SMB to the evil internet, be sure to restrict on your firewall what IP addresses can see it!!**[/COLOR]

Thanks, of course I will :) But first lets just test it. There's no harm to my LAN if the internets can see one share right?

and btw: can I make up something for MYCOMPUTERNAME or has it got to be the same name I gave it when configuring Ubuntu?

x5x_tim

---

### Post by badger_fruit on 2009-09-20
> **x5x_tim said:**
> There's no harm to my LAN if the internets can see one share right?

No, it should be OK for testing; after all, the access to the file-system is limited to the user_account you specify in your smb.conf

> **x5x_tim said:**
>  can I make up something for MYCOMPUTERNAME or has it got to be the same name I gave it when configuring Ubuntu?



I think that you can make up any name you want - I know that if you wanted to change the hostname of the machine then simply edit the /etc/hostname file.

It's waaay too early on a sunday morning to recall the differences in smb.conf vs hostname; i think (and don't quote me on this) in smb.conf it's just the name that's seen in (for example) windows explorer.

---

### Post by x5x_tim on 2009-09-20
mmm, did this, but radiotoolbox still gets a timeout.

It's located @ \\sambatestshare.no-ip.biz right now...

---

### Post by badger_fruit on 2009-09-20
> **x5x_tim said:**
> mmm, did this, but radiotoolbox still gets a timeout.

It's located @ \\sambatestshare.no-ip.biz right now...


ok, find your public ip address: [www.whatismyipaddress.com](www.whatismyipaddress.com)
then get the remote computer to try to browse to \\xxx.xxx.xxx.xxx\sharename (replace xxx with your public Ip address).

if that does not work, have you forwarded the correct TCP ports to the samba server (ports 137, 138 and 139)?

---

### Post by x5x_tim on 2009-09-20
> **badger_fruit said:**
> ok, find your public ip address: [www.whatismyipaddress.com](www.whatismyipaddress.com)
then get the remote computer to try to browse to \\xxx.xxx.xxx.xxx\sharename (replace xxx with your public Ip address).

if that does not work, have you forwarded the correct TCP ports to the samba server (ports 137, 138 and 139)?

Lol :P I know my public IP adress, I work with it a lot. sambatestshare.no-ip.biz is an alias because broadcasting an IP with open ports on a forum doesn't seem like a good idea to me :P
Share is called test share, so it would be
\\sambatestshare.no-ip.biz\test share

But I'm starting to think my ISP blocks port 139 and 445, it seems pretty common.

x5x_tim

---

### Post by x5x_tim on 2009-09-20
Yep. It's my ISP already...
Well, I guess I'll have to do it over FTP somehow.

Does anyone know a similar protocol to mount it directly on the remote conputer so I can use it in OneNote?

---

### Post by badger_fruit on 2009-09-20
> **x5x_tim said:**
> Lol :P I know my public IP adress, I work with it a lot. sambatestshare.no-ip.biz is an alias because broadcasting an IP with open ports on a forum doesn't seem like a good idea to me :P
Share is called test share, so it would be
\\sambatestshare.no-ip.biz\test share

But I'm starting to think my ISP blocks port 139 and 445, it seems pretty common.

x5x_tim


Naturally, hence my PM ;)

I don't think that that share would not work as there is a space in it... amend the share name in your smb.conf to something without spaces - eg test_share - oh and don't forget to restart samba when you make changes to this file ;)

I wouldn't expect ISPs to block any ports - that would be down to YOU to block.




Ah, I just saw your reply, that is unusual ... you could use WebDAV instead; I found it difficult to set up and configure but once that headache was over, i have ICS format calendars which can be read and written to over the net.  I also use it for various other tools ..

accessed using (say in visio)

file > open > [http://mydomain.net/mydavfolder/myfile](http://mydomain.net/mydavfolder/myfile)

---

### Post by x5x_tim on 2009-09-20
See:
[http://translate.google.com/translate?js=y&prev=_t&hl=nl&ie=UTF-8&u=http://www.mxstream.nl/support/technischevragen-dadsl.html%23105&sl=nl&tl=en&history_state0=](http://translate.google.com/translate?js=y&prev=_t&hl=nl&ie=UTF-8&u=http://www.mxstream.nl/support/technischevragen-dadsl.html%23105&sl=nl&tl=en&history_state0=)

It's not up to me. I'll give them a call tomorrow. Maybe we can work something out.

[COLOR="Red"]Mmm, I just learned programs that mount an ftp drive already exsist. :D
Maybe thats the solution :D[/COLOR]

---

### Post by falconindy on 2009-09-20
> **x5x_tim said:**
> [COLOR=Red]Mmm, I just learned programs that mount an ftp drive already exsist. :D
Maybe thats the solution :D[/COLOR]
I've been using fuseftp pretty happily. It's a bit of a pain in the butt to setup if you're not familiar with Perl and CPAN though.

[http://freshmeat.net/projects/fuseftp/](http://freshmeat.net/projects/fuseftp/)

---

### Post by x5x_tim on 2009-09-20
> **falconindy said:**
> I've been using fuseftp pretty happily. It's a bit of a pain in the butt to setup if you're not familiar with Perl and CPAN though.

[http://freshmeat.net/projects/fuseftp/](http://freshmeat.net/projects/fuseftp/)

I'm not fammiliar with either :P and it's suppost to work with MS Windows (note the MS OneNote :P)
But thanks anyway. It's just really frustrating to try to do these things over ftp... OneNote already hangs when I try to add the notebook..

x5x_tim

---

