---
title: "Best way to view mythtv recorded videos on a windows computer?"
date: 2009-11-01
forum: Mythbuntu
---

### Post by williammanda on 2009-11-01
I am trying to figure out the best way to view recorded videos (stream not download then view) from my backend via a windows computer? I have seen ways: mythweb, xbmc, etc... Please advise.
Thanks

---

### Post by nickrout on 2009-11-01
> **williammanda said:**
> I am trying to figure out the best way to view recorded videos (stream not download then view) from my backend via a windows computer? I have seen ways: mythweb, xbmc, etc... Please advise.
Thanks

you have a few choices:

1. compile mythtv for windows. This is not for the faint hearted.

2. xbmc via mythbox [http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)

3. xbmc via its native myth:// protocol

4. mythtvplayer, works for me but not tried it against 0.22 yet [http://www.sudu.dk/mythtvplayer/](http://www.sudu.dk/mythtvplayer/)

5. streaming in mythweb.

6. use mythrename.pl to rename your episodes to something readable (make sure you do the symlink method, not overwriting the existiong file names). Then mount the diretory via smb/cifs and play with a windows media player like smplayer or kantaris or vlc or whatever.

7. Use a player that can find stuff via upnp.

---

### Post by williammanda on 2009-11-01
> **nickrout said:**
> you have a few choices:

1. compile mythtv for windows. This is not for the faint hearted.

2. xbmc via mythbox [http://code.google.com/p/mythbox/](http://code.google.com/p/mythbox/)

3. xbmc via its native myth:// protocol

4. mythtvplayer, works for me but not tried it against 0.22 yet [http://www.sudu.dk/mythtvplayer/](http://www.sudu.dk/mythtvplayer/)

5. streaming in mythweb.

6. use mythrename.pl to rename your episodes to something readable (make sure you do the symlink method, not overwriting the existiong file names). Then mount the diretory via smb/cifs and play with a windows media player like smplayer or kantaris or vlc or whatever.

7. Use a player that can find stuff via upnp.

As for 2 through 4...I tried this but this is only for recordings not videos. 
5. I tried mythweb but I understand that it will download the video file only...I could be wrong. Also my files are iso & vob which can't be streamed under .22 yet.
Thanks

---

### Post by nickrout on 2009-11-01
> **williammanda said:**
> As for 2 through 4...I tried this but this is only for recordings not videos. 
If you have xbmc then just add a source pointing towards the videos on your backend. if I recall correctly mythbuntu serves them up as samba/cifs shares by default, one called videos, one called recorded.

---

### Post by williammanda on 2009-11-01
> **nickrout said:**
> If you have xbmc then just add a source pointing towards the videos on your backend. if I recall correctly mythbuntu serves them up as samba/cifs shares by default, one called videos, one called recorded.
[quote]

Would you please be more specific on how to do this? I'm not using mythbuntu. I installed ubuntu 9.10 and then mythbuntu control center so I don't believe that samba is installed. Also would you help out on the samba setup?
Thanks

---

### Post by nickrout on 2009-11-01
> **williammanda said:**
> [QUOTE=nickrout;8219617]If you have xbmc then just add a source pointing towards the videos on your backend. if I recall correctly mythbuntu serves them up as samba/cifs shares by default, one called videos, one called recorded.


Would you please be more specific on how to do this? I'm not using mythbuntu. I installed ubuntu 9.10 and then mythbuntu control center so I don't believe that samba is installed. Also would you help out on the samba setup?
Thanks

you'll have to wait until I am home tonight and I will go through my setup.

---

### Post by nickrout on 2009-11-02
OK xbmc to videos/recorded.

On mythbackend machine your /etc/samba/smb.conf reads:
```

[global]
workgroup = MSHOME
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share

[recordings]
comment = TV Recordings
path = /var/lib/mythtv/recordings
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[videos]
comment = Videos
path = /var/lib/mythtv/videos
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

[music]
comment = Music
path = /var/lib/mythtv/music
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

[pictures]
comment = Pictures
path = /var/lib/mythtv/pictures
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

```

On your xbmc machine go to videos|add source|browse|windows network (smb)|MSHOME|hostname of your backend|videos|OK|set the name to something sensible|Ok

---

### Post by williammanda on 2009-11-02
Here's what I have my smb.conf files has:

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

Do I need to replace this with what you have or add your info to the existing smb.conf?
Thanks

---

### Post by williammanda on 2009-11-02
OK I went back and installed samba through myhbuntu control center and got the same smb.conf you have. I restarted the computer that has the backend with the videos. I entered smb://MSHOME/C2Q/videos for the source but the XBMC computer says it couldn't retrieve directory information...due to the network not being connected.

---

### Post by nickrout on 2009-11-02
> **williammanda said:**
> OK I went back and installed samba through myhbuntu control center and got the same smb.conf you have. I restarted the computer that has the backend with the videos. I entered smb://MSHOME/C2Q/videos for the source but the XBMC computer says it couldn't retrieve directory information...due to the network not being connected.

I haven't seen that error before. I suggest the xbmc forums.

---

### Post by sk8er3810 on 2009-11-02
Try it without the MSHOME.  I presume "C2Q" is the Myth backend's hostname?

Also make sure you can view the shared directories in Windows Explorer as well

---

### Post by nickrout on 2009-11-02
> **sk8er3810 said:**
> Try it without the MSHOME.  I presume "C2Q" is the Myth backend's hostname?

Also make sure you can view the shared directories in Windows Explorer as well

I ususally navigate through the menus rather than type the url in. That way you know your xbmc machine can actually see the directories.

---

### Post by williammanda on 2009-11-02
> **sk8er3810 said:**
> Try it without the MSHOME.  I presume "C2Q" is the Myth backend's hostname?

Also make sure you can view the shared directories in Windows Explorer as well

OK that worked for the recordings - smb://C2Q/recordings but it still doesn't work for the other three directories. I tested videos, pictures and music in windows explorer using \\192.168.1.100 but unable to connect. The only common thing between three directories and not for recordings directory was that the three directories were symlinks to another drive /media/sdb1/var/lib/mythtv/*. I changed the path in the smb.conf from /var/lib/mythtv/videos to /media/sdb1/var/lib/mythtv/videos but the same result. Also how do you restart the samba server?
Thanks

---

### Post by sk8er3810 on 2009-11-02
```
sudo /etc/init.d/samba restart
```
actually stops the server and the starts it again
or
```
sudo /etc/init.d/samba reload
```
which only re-reads your smb.conf

if that doesn't work also check the permissions of your folders as well so that they may be readable by group

---

### Post by nickrout on 2009-11-02
> **williammanda said:**
> OK that worked for the recordings - smb://C2Q/recordings but it still doesn't work for the other three directories. I tested videos, pictures and music in windows explorer using \\192.168.1.100 but unable to connect. The only common thing between three directories and not for recordings directory was that the three directories were symlinks to another drive /media/sdb1/var/lib/mythtv/*. I changed the path in the smb.conf from /var/lib/mythtv/videos to /media/sdb1/var/lib/mythtv/videos but the same result. Also how do you restart the samba server?
Thanks

```
sudo service samba restart
```

I think by default samba doesn't follow symlinks. You may need to add into smb.conf:

```
Follow symlinks = yes
Wide links = yes

```

Also take a good look at permissions. They can be a real trap.

---

### Post by williammanda on 2009-11-02
OK success! I had to change owner of sdb1 to root from me.

---

### Post by NickPrecision on 2009-11-04
I just tried MythTV Player on .22 and it doesn't work. It didn't officially work with .21 but if you changed the XML to talk to the newer protocol it would play back. MythTV Player is supposed back under active development, hopefully they get it going with .22 soon because I used it almost every day to watch a few shows in the corner of my Windows PC while getting other work done.

---

### Post by perlLlama on 2009-11-04
Hi all

In XMBC you should be able to add a new video source from the Myth uPnP server.

I use XBMC on an orginal Xbox using this method and it works quite well..

Cheers

Stefan

---

### Post by badger_fruit on 2009-11-04
> **williammanda said:**
> I am trying to figure out the best way to view recorded videos (stream not download then view) from my backend via a windows computer? I have seen ways: mythweb, xbmc, etc... Please advise.
Thanks

Post # 2 is correct when they say that Myth for Windows is a nightmare!
I found that the latest version of "MythTV Player" does now allow live TV to be watched although I find it very unstable in that if I try to FF or RW it hangs and I have to end-task it.

Still, a quick and simple way to watch live TV or recordings from Myth on Windows.
Oh, I'm also using Myth .21 not the newer version so I can't comment on if it works or not.

---

