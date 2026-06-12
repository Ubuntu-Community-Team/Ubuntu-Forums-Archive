---
title: "Grsync backup to NAS – Can't see it..."
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by fisheater on 2009-07-19
Grsync backup to NAS – Can't see it...	Can't backup to it.	

Hi,

Problem: 
1.Linux n00b 
2.Want to back up my computers on home network to NAS
1.1 desktop ubuntu 9.04 64 bit, 1 laptop ubuntu 9.04 32 bit, 1 laptop winxp
3.Tried to use Grsync, but unable to see my NAS in the list of possible places to store it.
4.Tried a few others, but they are too baffling. Like Grsync, want to keep using it.
5.How to set it up and see the NAS for backup so I can use Grsync?
6.Pls explain in very simple terms. 
7.Mmmm also, how do I set up Grsync to backup and ONLY add or remove the changed files on the NAS? (save time and data transfer if only the changed stuff gets moved).

Please point me in the direction of any online help also.

Thanks!

FE

---

### Post by fisheater on 2009-07-20
bump. thx!

---

### Post by jamest09 on 2009-07-20
Never used grsync, but have had very very good results using rsnapshot

[http://rsnapshot.org/](http://rsnapshot.org/)

---

### Post by fisheater on 2009-07-20
Thanks, I will have a look at it now.

---

### Post by fisheater on 2009-07-24
bump.

Still drowning in the technical nature of trying to get my desktop ubuntu 9.04 to see my NAS via grsync/rsync.

I have it mapped when I use Nautilus - with full access and ease of use. However, when I try to backup via grsync (synctron, sbackup, etc) I can not see it as a directory to save to.

Advice?

FE

---

### Post by fisheater on 2009-07-26
Update:

Ubuntu -1   WinXP +1

So backing up made complicated.

Steps:
1.Ubuntu 9.04 backup to 2nd harddrive in desktop.
2.Relog WinXP
3.Start syncron
4.Back up data to NAS
5.Periodically back up NAS (Via WinXP) to 3rd HD.

Want to set up ubuntu to see my NAS when using Grsync. Suggestions?

Going to look through this list, see if any work: [http://en.wikipedia.org/wiki/File_synchronization](http://en.wikipedia.org/wiki/File_synchronization)

Thx!

FE

---

### Post by fisheater on 2009-07-30
Help! (bump)

ty

---

### Post by Kobalt on 2009-07-30
How do you mount your NAS partition : is it a CIFS (Samba) or a NFS partition? 
I use rsync with a NFS and it's 100% successful.

---

### Post by fisheater on 2009-07-31
Ummmm that may be the problem. I didnt know to mount my NAS and dont know how to mount it. I will google the two things (CIFS (Samba) or a NFS) you have mentioned and see if I can make some sense of it.

Thanks for your reply.

FE

---

### Post by dmizer on 2009-07-31
Yes, you will have to mount the NAS as a local drive for grsync to work as Grsync only works with local volumes.

To mount your NAS as a local drive, please see the second link in my sig.

---

### Post by fisheater on 2009-08-02
Shoot. My computer (my main) is not booting after trying to mount my NAS.

Help.

What I did:
sudo aptitude install smbfs (this uninstalled 200= MB of stuff)
sudo mkdir /media/sharename
sudo nano /etc/nsswitch.conf
from this: hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
to this: hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4



then I stopped because I didnt understand where it was going. I rebooted and not it hangs at 'starting samba services'


How can I fix this?
Very least how can I get access to my files! 

thx

FE

This is double posted in Main and networking. Sry.

---

### Post by fisheater on 2009-08-02
Thanks for your help, fixed the boot problem. 

NAS mount remains elusive.

FE

---

### Post by fisheater on 2009-08-03
Success. Thanks.

This was the info I used ([http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)) thanks for making it simple.

That said, when I first tried to do it I only was 1/2 way through and stopped then rebooted the computer. It wouldnt reboot was hung at 'starting samba servers'.

I rebooted into rootnet access and sudo apt-get remove smbfs (on forums advice - thanks russo.mic ([http://ubuntuforums.org/showthread.php?t=1229338](http://ubuntuforums.org/showthread.php?t=1229338)) then it restarted. then it wouldnt. it has been flaky.

I followed the steps from start to finished. Now I have managed to get it up and running, I will back it up and reboot my computer, fingers crossed, it will restart.

Thanks again.

FE

---

### Post by cariboo on 2009-08-03
Can you access your NAS using ssh? If you can then your destination should look something like this:

```
user@server:/path-to-storage-directory
```

---

### Post by fisheater on 2009-08-03
> **cariboo907 said:**
> Can you access your NAS using ssh? If you can then your destination should look something like this:

```
user@server:/path-to-storage-directory
```

Thanks for that, but I admit I am a bad *nix user. There isnt p/w on my network. That said, I know I should...

Now that I have mounted my NAS, suggestions on how to put a p/w on it? (it took me a few weeks of part-time sleuthing to get my NAS mounted). Remember -> new to linux.

thx!

FE

---

### Post by dmizer on 2009-08-03
> **fisheater said:**
> 
Now that I have mounted my NAS, suggestions on how to put a p/w on it? (it took me a few weeks of part-time sleuthing to get my NAS mounted).

You'll have to refer to the documentation on your NAS for that. Once you've configured password protected shares on your NAS, then you can refer to the second link again for how to add the password on your Ubuntu box.

---

### Post by fisheater on 2009-08-04
Ok, here's the current problems (thanks for the hand holding through this process). I have read the security info and will do it after this is set up (thx).

1.When I use g/rsync to back up my system, it backs up all the attached HDs &#8211; which includes my NAS. So I am backing up my desktop and my NAS to the NAS.
a.I have tried to exclude it from back up with &#8211;exclude=&#8221;.gvfs&#8221; with no avail.

2.I have tried to exclude some junk files with:
a.&#8211;exclude=&#8217;*.iso&#8217; &#8211;exclude=&#8221;.nautilus&#8221; &#8211;exclude=&#8221;.Trash&#8221; &#8211;exclude=&#8221;.thumbnails&#8221; &#8211;exclude=&#8221;.gvfs&#8221; 
b.Not working.

3.Initially back up was failing because 'unable to set time on NAS'
 
This is the most recent error codes:
rsync: link_stat "/home/lith/&#8211;exclude=&#8217;*.iso&#8217;" failed: No such file or directory (2)
rsync: link_stat "/home/lith/&#8211;exclude=&#8221;.nautilus&#8221;" failed: No such file or directory (2)
rsync: link_stat "/home/lith/&#8211;exclude=&#8221;.Trash&#8221;" failed: No such file or directory (2)
rsync: link_stat "/home/lith/&#8211;exclude=&#8221;.thumbnails&#8221;" failed: No such file or directory (2)
rsync: change_dir "/home/lith/&#8211;exclude=&#8221;.gvfs" failed: No such file or directory (2)
rsync: link_stat "/home/lith/on" failed: No such file or directory (2)
rsync: link_stat "/home/lith/192.168.1.120&#8221;" failed: No such file or directory (2)
rsync: readdir("/home/lith/.gvfs/volume_1 on 192.168.1.120/.systemfile"): Permission denied (13)
rsync error: received SIGINT, SIGTERM, or SIGHUP (code 20) at rsync.c(544) [sender=3.0.5]

Thx 

FE!

---

### Post by dmizer on 2009-08-04
Do you have any trouble moving or saving files to your NAS manually (rather than grsync)?

---

### Post by fisheater on 2009-08-04
> **dmizer said:**
> Do you have any trouble moving or saving files to your NAS manually (rather than grsync)?

Thanks for the reply, I will try and flesh it out a bit.

I am able to see the NAS as a harddive and move files freely between my desktop and NAS via nautilus.

I also have it set up as a media server and can use rhythmbox to see the drive.

Hm, thinking about this, I may have a solution. Before I mapped the drive (thanks to your help) I had set it up as a 'bookmark' in nautilus. Perhaps if I delete the bookmark it will vanish from my .gvfs folder and that may resolve one problem. (The book mark was a pointer to the IP on my home network, a workaround until i mapped it).

I will try and remove it when I get home.

Thanks for your ongoing interest!

FE

---

### Post by fisheater on 2009-08-05
More problems:

1. Main computer will not boot with the wins workaround
After many long and scary moments, I got it to boot after undoing a few steps. This command line change make it work
FROM: 
hosts:          files mdns4_minimal [NOTFOUND=return] _wins_ dns mdns4
TO:
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

Now I can reboot, but of course my NAS is no longed mapped.

Suggestions? My NAS was fully mapped and usable. I could use both Nautilus and rsync to see it and use it.

Thanks

FE

---

### Post by dmizer on 2009-08-05
> **fisheater said:**
> More problems:

1. Main computer will not boot with the wins workaround
After many long and scary moments, I got it to boot after undoing a few steps. This command line change make it work
FROM: 
hosts:          files mdns4_minimal [NOTFOUND=return] _wins_ dns mdns4
TO:
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

Now I can reboot, but of course my NAS is no longed mapped.

Suggestions? My NAS was fully mapped and usable. I could use both Nautilus and rsync to see it and use it.

Thanks

FE

Are you using Firestarter? What is the output of:
```
sudo iptables -L
```

Also, try "simple backup" in lieu of grsync. It can be found in synaptic by searching on sbackup. I find it to be more intuitive and very simple to use.

---

### Post by dmizer on 2009-08-05
> **fisheater said:**
> More problems:

1. Main computer will not boot with the wins workaround

Please also post the contents of /etc/samba/smb.conf

---

### Post by fisheater on 2009-08-05
Thanks for your ongoing help.

1. I am now using Back in Time ([http://backintime.le-web.org/](http://backintime.le-web.org/)) to back up, it is another GUI for rsync. My brain and this interface work.

2. I have put the info you asked about below, hope that it helps figure out what is gone wrong. The only thing I have changed after mounting my NAS was the line listed 3 posts up (remove hosts: wins). Computer boots, NAS not mounted.

3. NAS is 192.168.1.110

Thx! 

FE

```
sudo iptables -L

Chain INPUT (policy DROP)
target     prot opt source               destination         

ACCEPT     tcp  --  k2                   anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN 

ACCEPT     udp  --  k2                   anywhere            

ACCEPT     all  --  anywhere             anywhere            

ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 

DROP       all  --  anywhere             255.255.255.255     

DROP       all  --  anywhere             192.168.1.255       

DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            

DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 

DROP       all  --  255.255.255.255      anywhere            

DROP       all  --  anywhere             0.0.0.0             

DROP       all  --  anywhere             anywhere            state INVALID 

LSI        all  -f  anywhere             anywhere            limit: avg 10/min burst 5 

INBOUND    all  --  anywhere             anywhere            

LOG_FILTER  all  --  anywhere             anywhere            

LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Input' 



Chain FORWARD (policy DROP)

target     prot opt source               destination         

ACCEPT     icmp --  anywhere             anywhere            limit: avg 10/sec burst 5 

LOG_FILTER  all  --  anywhere             anywhere            

LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Forward' 



Chain OUTPUT (policy DROP)

target     prot opt source               destination         

ACCEPT     tcp  --  lith-desktop    k2                  tcp dpt:domain 

ACCEPT     udp  --  lith-desktop    k2                  udp dpt:domain 

ACCEPT     all  --  anywhere             anywhere            

DROP       all  --  BASE-ADDRESS.MCAST.NET/8  anywhere            

DROP       all  --  anywhere             BASE-ADDRESS.MCAST.NET/8 

DROP       all  --  255.255.255.255      anywhere            

DROP       all  --  anywhere             0.0.0.0             

DROP       all  --  anywhere             anywhere            state INVALID 

OUTBOUND   all  --  anywhere             anywhere            

LOG_FILTER  all  --  anywhere             anywhere            

LOG        all  --  anywhere             anywhere            LOG level info prefix `Unknown Output' 



Chain INBOUND (1 references)

target     prot opt source               destination         

ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 

ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 

ACCEPT     all  --  192.168.1.100        anywhere            

ACCEPT     all  --  192.168.1.101        anywhere            

ACCEPT     all  --  192.168.1.102        anywhere            

ACCEPT     all  --  192.168.1.104        anywhere            

ACCEPT     all  --  192.168.1.103        anywhere            

ACCEPT     all  --  192.168.1.106        anywhere            

ACCEPT     all  --  192.168.1.105        anywhere            

ACCEPT     all  --  192.168.1.110        anywhere            

ACCEPT     all  --  SILVER               anywhere            

ACCEPT     all  --  192.168.1.111        anywhere            

ACCEPT     all  --  orange-laptop        anywhere            

LSI        all  --  anywhere             anywhere            



Chain LOG_FILTER (5 references)

target     prot opt source               destination         



Chain LSI (2 references)

target     prot opt source               destination         

LOG_FILTER  all  --  anywhere             anywhere            

LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 

DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN 

LOG        tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 

DROP       tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/RST 

LOG        icmp --  anywhere             anywhere            icmp echo-request limit: avg 1/sec burst 5 LOG level info prefix `Inbound ' 

DROP       icmp --  anywhere             anywhere            icmp echo-request 

LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Inbound ' 

DROP       all  --  anywhere             anywhere            



Chain LSO (0 references)

target     prot opt source               destination         

LOG_FILTER  all  --  anywhere             anywhere            

LOG        all  --  anywhere             anywhere            limit: avg 5/sec burst 5 LOG level info prefix `Outbound ' 

REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 



Chain OUTBOUND (1 references)

target     prot opt source               destination         

ACCEPT     icmp --  anywhere             anywhere            

ACCEPT     tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED 

ACCEPT     udp  --  anywhere             anywhere            state RELATED,ESTABLISHED 

ACCEPT     all  --  anywhere             anywhere     


/etc/samba/smb.conf

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

	workgroup = k2home



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

	client lanman auth = yes



#### Networking ####



# The specific set of interfaces / networks to bind to

# This can be either the interface name or an IP address/netmask;

# interface names are normally preferred

	interfaces = lo eth0



# Only bind to the named interfaces and/or networks; you must use the

# 'interfaces' option above to use this.

# It is recommended that you enable this feature if your Samba machine is

# not protected by a firewall or is a firewall itself.  However, this

# option cannot handle dynamic or non-broadcast interfaces correctly.

	bind interfaces only = yes







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

;	encrypt passwords = yes



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

;	printing = cups

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

;	usershare max shares = 100



# Allow users who've been granted usershare privileges to create

# public shares, not just authenticated ones

	usershare allow guests = yes

;	guest ok = no

;	guest account = nobody



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

;	guest ok = no

;	read only = yes

	create mask = 0700



# Windows clients look for this share name as a source of downloadable

# printer drivers

[print$]

	comment = Printer Drivers

	path = /var/lib/samba/printers

;	browseable = yes

;	read only = yes

;	guest ok = no

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

### Post by dmizer on 2009-08-05
Well, it looks like you have some iptables rules in place. What tool did you use to configure your firewall? Do you have a particular need for a firewall?

If the NAS is always at the same IP address, then just use the IP address instead of the host name.

---

### Post by fisheater on 2009-08-05
Hi,

1. I use firestarter to config, just the ip addresses on my home network. I (thought) I was putting those there so I could use my network. Do I even need those rules? As you can see this is all new to me.

2. My NAS has been set to a static IP (192.168.1.110). Where would I insert the IP instead of the name?

3. Will #2 help if I read wins to hosts? When wins is in the line of code, my computer hangs on reboot 'Starting Samba Daemons'.

Thx!

FE

---

### Post by dmizer on 2009-08-05
I'm not sure I understand what you mean in point number one. Could you give me an idea of how your network is configured (tell me what is connected to what). Also, it seems as though you may be running static IP on your LAN. Is that correct?

Firestarter interferes with a lot of network traffic, so unless you really understand Firestarter and iptables well, you will end up doing more harm than good by using it. In this case, Firestarter is what prevented your system from booting rather than the wins edit in /etc/nsswitch.conf. Firestarter prevented the samba daemons from starting correctly.

In the second link in my sig, I gave some sample /etc/fstab lines that you would need to modify for your own network. It looks like this:
```
//netbiosname/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```
For your network, you would simply replace "netbiosname" with the IP address of your NAS device. So your /etc/fstab line would look something like this instead:
```
//[COLOR="Red"]192.168.1.110[/COLOR]/sharename    /media/sharename        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

---

### Post by fisheater on 2009-08-05
As you can tell by my questions and set up of my network, this is all very rudimentary. I really have no background in this and have been putting it together as I stumble along.

1. Setup:

Cable internet
-	wireless router
o	laptop 1 - wireless (wireless router assigns IP)
o	laptop 2 - wireless (wireless router assigns IP)
o	Desktop via LAN cable (wireless router assigns IP)
o	Printserver via LAN (wireless router assigns IP)
o	NAS via LAN (static IP, option set in NAS setup)

2. Firewall
I thought a firewall was a basic necessity for safe computing. Let me ask you a question: If I remove my rules and uninstall firestarter, does that disable or uninstall my firewall? Do I need to do anything more than trust in the IP tables shipped with Ubuntu 9.04?

3. Not booting
I understand what you are saying, and will make the changes when I get home.
- remove firestarter
- edit fstab
- re-enter wins
- then reboot

Thanks again for all your help, I feel that we are getting close!

FE

---

### Post by dmizer on 2009-08-05
> **fisheater said:**
> 2. Firewall
I thought a firewall was a basic necessity for safe computing. Let me ask you a question: If I remove my rules and uninstall firestarter, does that disable or uninstall my firewall? Do I need to do anything more than trust in the IP tables shipped with Ubuntu 9.04?
You are correct, a firewall is a basic necessity for safe computing. But unless you've disabled it, your router has one. There's no need for two.

Let me know how your changes turn out.

---

### Post by fisheater on 2009-08-05
Hi.

Changes to date.

1.Removed all firewall rules in firestarter then uninstalled via synaptic.
2.Added wins back into hosts
3.Rebooted
4.Stuck at same place on boot up, ~90% of the bar on the start up screen, then text reading 'Starting Samba daemons'. After 30 min no progress on booting.
5.Tried editing //netbiosname/sharename to //192.168.1.110/sharename
6.Reboot, stuck at same spot of boot up.

If this is a firewall problem blocking samba, then I must not have deleted all the firewall settings when I deleted firestarter. Is there a way to view my firewall/iptable rules? When I do 'sudo iptables -L' in rootshell of recovery:

Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination

Of interest, when I boot into recovery with net access &#8211; i see the samba daemons are up and running. 

Thx.

FE

More info: I sudo apt-get upgrade/install from recovery, had some updates, then it rebooted and worked! Then I rebooted to see if it would do it again, and no. Still stuck with my samba daemons.

thx

---

### Post by dmizer on 2009-08-05
Please post your current /etc/samba/smb.conf file.

---

### Post by fisheater on 2009-08-05
My information is below.

I was reading through this conf file and see that I have not set this WINS info:

# Windows Internet Name Serving Support Section:

# WINS Support - Tells the NMBD component of Samba to enable its WINS Server

#   wins support = no



# WINS Server - Tells the NMBD components of Samba to be a WINS Client

# Note: Samba can be either a WINS Server, or a WINS Client, but NOT both

;   wins server = w.x.y.z


So, if I change wins support = yes and wins server = (?my NAS 192.168.1.110) will this solve the problem?

Also, I can boot with the following work around.
1.Failed method: normal boot.
2.Work around: boot into recovery, go to root with net access, type 'exit' then option 1 – resume startup. 

Thx.

FE

```
sudo iptables -L


Chain INPUT (policy ACCEPT)

target     prot opt source               destination         



Chain FORWARD (policy ACCEPT)

target     prot opt source               destination         



Chain OUTPUT (policy ACCEPT)

target     prot opt source               destination   

/etc/samba/smb.conf

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

	workgroup = k2home



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

	client lanman auth = yes



#### Networking ####



# The specific set of interfaces / networks to bind to

# This can be either the interface name or an IP address/netmask;

# interface names are normally preferred

	interfaces = lo eth0



# Only bind to the named interfaces and/or networks; you must use the

# 'interfaces' option above to use this.

# It is recommended that you enable this feature if your Samba machine is

# not protected by a firewall or is a firewall itself.  However, this

# option cannot handle dynamic or non-broadcast interfaces correctly.

	bind interfaces only = yes







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

;	encrypt passwords = yes



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

;	printing = cups

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

;	usershare max shares = 100



# Allow users who've been granted usershare privileges to create

# public shares, not just authenticated ones

	usershare allow guests = yes

;	guest ok = no

;	guest account = nobody



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

;	guest ok = no

;	read only = yes

	create mask = 0700



# Windows clients look for this share name as a source of downloadable

# printer drivers

[print$]

	comment = Printer Drivers

	path = /var/lib/samba/printers

;	browseable = yes

;	read only = yes

;	guest ok = no

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

### Post by dmizer on 2009-08-05
> **fisheater said:**
> So, if I change wins support = yes and wins server = (?my NAS 192.168.1.110) will this solve the problem?

No. You do not want this.

Are you connecting wirelessly? If so, are you using a network configuration GUI other than network-manager (WICD for example)?

I've seen your problem several times, and I'm seriously interested in pursuing a fix for it. I'm currently on a business trip and won't be back until tomorrow. For the time being, I suggest this:

Remove the wins option from /etc/nsswitch.conf before you shut down your computer. After you've rebooted, readd the wins option, and restart your network. This way, you won't have to mess with the recovery session every time you boot.

---

### Post by fisheater on 2009-08-05
Thanks for your time, this has become a bigger problem that I was prepared for.

I connect directly to my router with a LAN cable.

Also, I will try your suggested work around. Thanks for your help.

FE

---

### Post by dmizer on 2009-08-07
okay ... try this:

1) Install
gnome-network-admin

2) Uninstall
network-manager

3) Configure your wired network from System > Administration > Network

See if that fixes your problem.

---

### Post by fisheater on 2009-08-12
Dmizer,

Thanks for your help and persistence. I have managed to get my NAS up and running. My plan is to back up my system to my NAS and then try to reboot. Hopefully it will restart and get past the samba daemons.

Will let you know. Nice work, thanks for all the input.

FE

---

### Post by Engenia on 2009-08-19
I'm a Linux virgin. I've been struggling with this for the last couple of days, and this is how I've managed to get grsync to work:-

ubuntu Jaunty, 64 bit
NAS drive:
 - WD MyBook World edition
 - set to 1TB RAID 1
 - ip: 192.168.15.151 (//wdg2nc2)
 - 2 shares:
 -- public (unprotected)
 -- engenia (user/password protected)

mount in terminal with:
      (refer to [http://ubuntuforums.org/showthread.php?t=1214189&highlight=mounting+NAS+drive](http://ubuntuforums.org/showthread.php?t=1214189&highlight=mounting+NAS+drive))

errol@934engenia-desktop:~$ gvfs-mount smb://wdg2nc2/public
&
errol@934engenia-desktop:~$ gvfs-mount smb://wdg2nc2/engenia

(curiously, no password is requested, or given, when mounting "engenia" - don't know why / how it works)

"public" mount point is    /home/errol/.gvfs/public on wdg2nc2
"engenia" mount point is /home/errol/.gvfs/engenia on wdg2nc2

grsync :-
 - unable to preserve times - operation not supported (95) - so don't select it
 - select Skip newer
 - source       /home/errol/Project/Engenia/Records/Cash Book/
 - destination /home/errol/.gvfs/engenia on wdg2nc2/SyncFiles/CashBook/

Works a treat.
Just need to work out how to mount the NAS drive at bootup.:-k

---

### Post by dmizer on 2009-08-19
> **Engenia said:**
> 
Just need to work out how to mount the NAS drive at bootup.:-k

Check here: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)

---

### Post by Engenia on 2009-08-20
> **dmizer said:**
> Check here: [http://ubuntuforums.org/showthread.php?t=1186877](http://ubuntuforums.org/showthread.php?t=1186877)
Thanks dmizer. Problem solved.

---

### Post by fisheater on 2009-08-25
Update:

Mounting NAS a success. I removed wins from the hosts: line and put in my IP (192.168.1.***) and it seems to work and lets me reboot. However there is an error message on shutdown. I will write it down when I next reboot.

I have attached a picture of my network schematic for my next issue.

I am able to rsync from my desktop to my 2nd HD (NTFS) in the tower.
I am able to rsync from my NAS to my 2nd HD (NTFS) in the desktop 1 tower.

I am unable to rsync from my desktop main HD (ext3) to my NAS (ext2). I get “Operation not permitted (1)” error. It writes all the file folders to my NAS but they are all empty.

(rsync: failed to set times on "/media/K2/Personal Backup – FULL/Chris/grsync /Documents/Australia": Operation not permitted (1)

[[IMG]http://img165.imageshack.us/img165/4693/networkk.th.png[/IMG]](http://img165.imageshack.us/i/networkk.png/)

Suggestions?

Kind regards 

FE

---

### Post by dmizer on 2009-08-25
Your problem is probably that there is a space in your folder name "Personal Backup"

Rename this folder so it does not contain a space, and edit your rsync command likewise.

---

### Post by fisheater on 2009-10-27
Thanks for all your help/input for making my home network better. I have mapped my NAS but have not been able to successfully use rsync to back up. I have been backing up to my HD in the tower. Then my work around has been to use WinXP and syncron to backup my backup...

Has this complicated workaround been addressed in 9.10? I would happily change to make backing up less complicated (and yes, the problem is likely in my rudimentary understanding of linux).

I tried this workaround ([http://ubuntuforums.org/showthread.php?t=1186877&page=4](http://ubuntuforums.org/showthread.php?t=1186877&page=4)) but it seems to only map the NAS drive, not mount it. It turns up in Nautilus as a folder, not as a drive. As such, I am unable to see in in Grsync.

Thanks!

FE

---

### Post by dmizer on 2009-10-27
What NAS device do you have (please post make and model number)?

---

### Post by fisheater on 2009-10-28
> **dmizer said:**
> What NAS device do you have (please post make and model number)?

D-link DNS 323 ([http://www.dlink.ca/products/?pid=509](http://www.dlink.ca/products/?pid=509))

ty for helping with this setup!

FE

---

### Post by fisheater on 2009-11-04
> **dmizer said:**
> Your problem is probably that there is a space in your folder name "Personal Backup"

Rename this folder so it does not contain a space, and edit your rsync command likewise.

Dmizer (et al),

Question about using file names on my NAS - I have many, many folder names with spaces (Personal backup, Summer Photos, etc). Do you think this is at the heart of my problem with backing up? Do I have to rename all the folders on my NAS to exclude spaces? Further on that topic, do my files need to have names without spaces? (i.e. rename everything?)

As for the mounting, that seems to be working well. I have the NAS found on startup, the only problem now is that my computer hangs for ~30 sec on shutdown.

So far so good!  

TY

FE

---

### Post by dmizer on 2009-11-06
> **fisheater said:**
> D-link DNS 323 ([http://www.dlink.ca/products/?pid=509](http://www.dlink.ca/products/?pid=509))

ty for helping with this setup!

FE
Sorry for the late reply. For some reason I missed this.

Your device has an FTP server. Try configuring grsync to accessing your files via FTP instead of Samba.

---

### Post by fisheater on 2009-11-07
Thanks for your ongoing interest/support in my adventure to set up my NAS!

Good news: my desktop is set up to mount the NAS. Grsync fails – I will rename the folders to exclude folders then try again.

Current issue: now setting up my 2 laptops to mount the NAS, but have hit a road block. I have followed your directions to the end.

It didn’t work so I went back to each step. I think this step is the issue: 

My NAS is 192.168.1.111, and I set it up:
//192.168.1.111/k2    /media/K2       cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

But when I try smbtree to confirm it I get this message:
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK
Server requested LANMAN password (share-level security) but 'client lanman auth' is disabled
failed tcon_X with NT_STATUS_OK
(I am naughty, there is no p/w to access it...)

I will look at my desktop config and see if there is any clues there.

Thanks!

FE

---

### Post by dmizer on 2009-11-08
Try this:
```
/192.168.1.111/k2 /media/K2 cifs guest,[COLOR="Red"]sec=none,[/COLOR]rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

If that doesn't work, try using sec=ntlmv2 instead.

I still think this is going to be much easier for you if you use FTP instead of Samba.

---

### Post by fisheater on 2009-11-13
Thanks for all your help. I have botched my desktop (working it out in another thread, almost back to normal) and will have to try this in a bit.

Thanks for the suggestion, I will put it into practice and get back to you.

Is there any others out there who have used 9.1 for setting up a NAS? What have been you experiences? Simple, complicated, what method did you use (?#2 in Dmizer's sig or an alternate?) Anyone else doing NAS backup?

TY 

FE

---

### Post by edanto on 2011-07-27
Oh my word.  I am trying to do the same thing as fisheater.... but really dread going through all the trouble to achieve it.

I just want to mount my NAS?!  Is there an easier way now?!

Apologies if it's bad form to drag up such an old thread, but the only other threads on this subject I can find on the forum describe very complicated procedures.

Complicated to me - very complicated.  :-?

---

### Post by dmizer on 2011-07-29
> **edanto said:**
> Oh my word.  I am trying to do the same thing as fisheater.... but really dread going through all the trouble to achieve it.

Then (as suggested above) use FTP instead of Samba. You can mount FTP via GUI rather than trying to add lines to FSTAB, and Grsync works fine over FTP.

---

### Post by gpfnz on 2011-09-16
> **edanto said:**
> Oh my word.  I am trying to do the same thing as fisheater.... but really dread going through all the trouble to achieve it.

I just want to mount my NAS?!  Is there an easier way now?!

Apologies if it's bad form to drag up such an old thread, but the only other threads on this subject I can find on the forum describe very complicated procedures.

Complicated to me - very complicated.  :-?

I haven't read every post in this thread - so someone else may have already suggested this but here goes...  I only started using ubuntu a month ago and had the same question as you almost immediately. After scouring the web for hours I put together these steps which work well for me:

[LIST=1]
[*]Create folder to mount your NAS folder, in /media like this: /media/NASBackup (may have to use root login "gksudo nautilus" can't remember)
[*]Run this command to mount network share:  sudo mount -t cifs "\\\\192.168.1.200\backups" /media/NASBackups
[*]I use the graphical backup utility "grsync" which is a lot friendlier than having to learn all the rsync switches ;). I enter my source: /media/D_750gb/ (which is my local NTFS D drive pre-mounted) and destination: /media/NASBackups/Dell/D/.
[*]Once set-up, it's painless. I added the command to mount the NAS drive (step 2) in the grsync optional command "Execute this command before rsync" so it mounts the NAS share before backing up. You could no doubt also run a similar command to unmount it when finished backup using the "execute this command after rsync".
[/LIST]
Hope this helps someone and if there's an easier method - let me know!! ):P

---

