---
title: "Uninstall Samba and start again"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2009-06-14
Hi all,

How do I uninstall Samba and start again? I've played about with it on and off but now have had some time to start getting into it a bit more seriously and realise I have a 'dog's breakfast' after all my experimentation.

So, like to get back to square one and do it right this time (at least attempt to!). Uninstalling is simple as going to Synaptics and removing samba-common? Maybe a coupla other things? 

I did do it before but not sure I remember how, was awhile ago, but I remember it gave me some pretty scary messages regarding what it was going to uninstall along with samba, like 'ubuntu-desktop' but nothing drastic happened that I remember.

Any help?

---

### Post by superprash2003 on 2009-06-14
you could remove it from synaptics.. you could leave the samba client though and just remove samba server..

---

### Post by Bucky Ball on 2009-06-14
Thanks for that. Will this still allow me to transfer files? I was thinking about it and wondering if a server was necessary ... am a bit new to samba config. I have three machines and if one needs to be a server, that would mean if it wasn't on, the two clients couldn't communicate on the LAN?

As it happens, the wrong machine is the server! One of the reasons I wanted to start again.

---

### Post by dmizer on 2009-06-14
There should be no reason to uninstall and reinstall samba unless you installed from source. If you installed samba from source, then you'll have to run the uninstall script from the source directory.

Otherwise, all you have to do is properly configure smb.conf. 100% of how samba server works is controlled by /etc/samba/smb.conf so once you have the correct configuration file, you'll have a working samba server. Plus, if you followed directions I gave in your old thread, then you'll have a backup of the original smb.conf file you had before you started making changes (/etc/samba/smb.conf-old).

So rather than concentrating on how to uninstall and reinstall, just concentrate on making a correct samba server config file.

I still recommend NFS even though you only have a DHCP network. I've had a DHCP network for many years and use NFS as my file server. All you need is either a local DNS server or properly configured winbind for NetBIOS naming.

---

### Post by Bucky Ball on 2009-06-15
> **dmizer said:**
> So rather than concentrating on how to uninstall and reinstall, just concentrate on making a correct samba server config file.

I still recommend NFS even though you only have a DHCP network. I've had a DHCP network for many years and use NFS as my file server. All you need is either a local DNS server or properly configured winbind for NetBIOS naming.

1/ I was going to uninstall and re-commence proceedings so I could learn to do this from the beginning. As I say, I am trying things, reading help sites and basically wasting hours trying to unravel my mess.

2/ I can find no GUI for NFS. While I am comfortable using the terminal, my wife is not, and I really am after something with the ease of use of samba. I've looked at NFS, SSH, FTP. None of them really suit and none of them have an adequate interface for a non-terminal user.

3/ Yes, backed up smb.conf on all three machines, naturally, and now the ones I'm working with are pretty mangled. I could post all three smb.confs and you could maybe give me a hint as to what the hell I'm doing! If I have to have a server, which is unfortunate but the way it is, if is currently the wrong machine and I am having enough trouble figuring out how to change it to the right machine (Lappy, not Studio).

All I'm really after is the most simple, functioning smb.conf I can setup. I don't need anything exotic for the moment; I can learn the finer points of tweaking it as I go. Again, thought this might be better achieved by starting from the beginning and doing it right rather than attempting to pick the carrots out of this mess. But it probably ain't that hard, just missing some concepts for the moment.

So, that's about where I am now. Any more info happily provided. :)

---

### Post by dmizer on 2009-06-15
My parents use NFS for sharing files and they don't even know it.

I just used the mount command given in the tutorial and included the "users" option like so:
```
server:/shared/directory /media/mountpoint nfs users,rsize=8192,wsize=8192,timeo=14,intr
```
Then, I created a desktop link for /media/mountpoint (right click on the mount location and select "send to" > "desktop"

Then, tell your wife to click on the shared directory icon in order to see the files from the server. When she clicks on the folder, the drive will mount.

That's it. It takes CLI to set up the sharing. It does not take CLI to make use of the sharing. Unless I'm completely misunderstanding what you want to do, I think it should be much easier to simply click on a pre-configured directory to mount the share than trying to explain how to use "places" > "connect to server".

Conversely, rather than having her create a share every time she wants to share something, just provide a single directory for her to put things in that she wants to share out on the network. This significantly reduces confusion and really makes things easy for people who know nothing about file sharing. One directory to get files from the server, another one to make files available to the network.

Of course, the above can also be done with samba, but it's so much easier to do with NFS. A very basic smb.conf that would still provide for user created shares would probably look like this:
```
[global]
   workgroup = WORKGROUP
   netbios name = [COLOR="Red"]name-your-computer[/COLOR]
   name resolve order = lmhosts host wins bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .   pam password change = yes
   map to guest = bad user
   security = share
# Remove the comments to enable CUPS printer sharing via Samba (usually not necessary)
;   printing = cups
;   printcap name = cups

   usershare allow guests = yes

[[COLOR="Red"]sharename[/COLOR]]
    path = [COLOR="Red"]/shared/directory[/COLOR]
    read only = no
    guest ok = yes
```
You'll have to change the items marked in [COLOR="Red"]red[/COLOR] to match the needs of your own network.

---

### Post by Bucky Ball on 2009-06-15
This on the client machine (Studiobox):

```
bucky@studiobox:/$ sudo mount HPLappy:/media/bigboy/Anna /files
mount.nfs: can't get address for HPLappy
```

This from the server (HPLappy)

```
skulker@HPLappy:~$ sudo mount HPLappy:/media/bigboy/Anna /files
mount.nfs: access denied by server while mounting HPLappy:/media/bigboy/Anna
```

I am attempting to set the laptop as the NFS server, studiobox as client. I am presuming that would only require nfs-common, not nfs-kernel-server as well? (I have both installed on laptop/server). Question:

* Is there a problem with having two machines as servers? If Lappy is the server, then Studiobox and Lounge will not be able to share unless Lappy is on.

---

### Post by dmizer on 2009-06-15
**On HPlappy, do the following:**
1) Install samba:
```
sudo aptitude install samba
```

2) Use the following smb.conf file:
```
[global]
   workgroup = WORKGROUP
   netbios name = HPLAPPY
   name resolve order = lmhosts host wins bcast
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
```

3) Restart samba:
```
sudo /etc/init.d/samba restart
```

**On studiobox, do the following:**
1) Edit /etc/nsswitch.conf to look like the following example (changed line in red):
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

[COLOR="Red"]hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
[/COLOR]networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

2) Instal the winbind daemon:
```
sudo aptitude install winbind
```

3) Create a mountpoint (not /files) for on studiobox, and give it correct ownership:
```
sudo mkdir /media/hplappy
```
```
sudo chown annas-username:annas-username /media/hplappy
```

4) Create a symbolic link by right clicking on /media/hplappy > send to > desktop

5) Create an entry in /etc/fstab that looks like this:
```
hplappy:/media/bigboy/Anna /media/hplappy nfs users,rsize=8192,wsize=8192,timeo=14,intr
```

6) Test the mount with the following command:
```
mount /media/hplappy
```

Done, you should never have to look at the CLI again.

---

### Post by Bucky Ball on 2009-06-15
Thanks for that.

mount.nfs: access denied by server while mounting hplappy:/media/bigboy/Anna

Really have little idea what I'm doing but guess I'll work it out eventually. Time to study for uni exams, enough time on this. One of the truly not simple things about Linux, but maybe I'm to used to how easy it was in Windows. That is the only thing that was easier!

I intend to uninstall everything network, take it slow and study it properly after my exams. That way, I'll understand what I'm doing. At the moment, it is just a bunch of commands and steps.

:)

---

### Post by dmizer on 2009-06-15
Actually, you're really close. Maybe only one or two other things to do.

Please post your /etc/exports file from HPLappy, and post the output of (also from hplappy):
```
ifconfig
```

---

### Post by Bucky Ball on 2009-06-15
I had a feeling I was. Just need to drag myself away and study (rather be doing this right now, that is the frustrating part!).

Ok, if config:
```

skulker@HPLappy:/$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:02:b9:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3059 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3059 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:127569 (124.5 KB)  TX bytes:127569 (124.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:2b:0e:9f  
          inet addr:192.168.0.106  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6409153 (6.1 MB)  TX bytes:1263880 (1.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-2B-0E-9F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```And /etc/exports

```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
/**files 192.168.0.0/10**(rw,no_root_squash,async)
/*HPLappy 192.168.0.0/10(rw,no_root_squash,async)*
```* I have a feeling the part I have bolded could be the problem. The numbers in the tutorial ended 1.0
* The line in italics I just added but made not difference. 

My IPs are gonna drop somewhere between 192.168.0.3-10 (have routers at 0.1 and 0.2) so that is where I am going to want /files

```
exportfs: Warning: /HPLappy does not exist
```Persists on a restart of the nfs-kernel-server. Does this need to be set up as a mount point on HPLappy also?


***** UPDATE**: Yes! Managed to view HPLappy's /media/bigboy/Anna folder in the HPLappy folder mounted on the Studiobox desktop, and the contents thereof! Not completely sure how I did it, but something to do with my path syntax. I have fooled around with it again and broken it, but that is fine; there is hope!

Just tried it again and brilliant, not, it is still working. Will retrace my steps when I get back from volleyball and see if I can get it happening on the Lounge machine also. 

I think I'm starting to finally get it. Thanks for your persistence and help, dmizer. :)

---

### Post by Bucky Ball on 2009-06-15
Okay, that is working like a dream. I have tweaked the paths and have a slightly better understanding of what's going on. Thanks again.

I have the Desktop share folder 'HPLappy' on Studiobox and have that mounting /media/bigboy, the whole partition, not /media/bigboy/Anna, so that is great.

fstab from Studiobox:

```
# Entry for /media/HPLappy/bigboy
HPLappy:/media/bigboy /media/HPLappy nfs users,rsize=8192,wsize=8192,timeo=14,intr
```/etc/exports from HPLappy:

```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync) hostname2(ro,sync)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt)
# /srv/nfs4/homes  gss/krb5i(rw,sync)
#
# /files 192.168.0.0/10(rw,no_root_squash,async)
# /HPLappy 192.168.0.0/10(rw,no_root_squash,async)
/media/bigboy/ files 192.168.0.0/10(rw,no_root_squash,async)

```*** **UPDATE:** dmizer, this is great! Thanks so much for your help. Brilliant. I just set up Lounge and it took me less than five minutes before I was looking at a HPLappy folder holding the contents of /HPlappy/media/bigboy!

Now I really do have to study (what I am supposed to be studying that is), but you have helped me solve a problem I have been tinkering with ever since I got into Ubuntu and I much appreciate it. Glad you encouraged me to go that final inch and make it over the line! 

:)

... and another question: I am trying to share one back the other way now from Studiobox to HPLappy (didn't quite get to the boox!). Is this possible or do both machines need to be set up as servers? Could I set all three up as servers so any two could see each other (Studiobox and Lounge without HPLappy being on for example)?

From HPLappy:

```
skulker@HPLappy:~$ sudo mount -a
mount.nfs: can't get address for studiobox
```Final question! Does it go like this.

The partition on HPLappy is /bigboy. I could get more specific then, and set up a bunch of mount points on Studiobox for different folders on HPLappy within /bigboy?  

At the moment it is great; HPLappy on Studiobox has the contents of /bigboy, and I understand how I can get more granular (the contents of one folder). So I should set up mount points and fstab for individual folders on /bigboy, say Music, Pics, Documents for instance?

```
# Entry for /media/HPLappy/bigboy/Music
HPLappy:/media/bigboy/Music /media/HPLappy nfs users,rsize=8192,wsize=8192,timeo=14,intr

# Entry for /media/HPLappy/bigboy/Pics
HPLappy:/media/bigboy/Pics /media/HPLappy nfs users,rsize=8192,wsize=8192,timeo=14,intr

```Would that do the trick? And just one more thing; how secure is this setup? Could I make it more secure by tweaking anything? I will read up on that some more and NFS generally tomorrow. Cheers.

**Slight Problem**: I switched HPLappy off and things weren't good on Studiobox. Try to open 'Places->Anyplace' and you get the empty window with the cursor ball spinning instead of the files that are in the folder or partition 'Anyplace'. Should I have unmounted something first? I re-started the machine (log out/in didn't work) and things were back to normal. I saved the /fstab and then removed the in /fstab nfs share to stop it from trying to mount at reboot before I restarted.

**Further update**: Laptop gave an error booting up this morning but then worked fine. I think, 'HPLappy has no inet address(this is with Studiobox switched off). Does that sound right? I'll try again later.

---

### Post by frankhdz on 2009-12-18
THIS IS DRIVING ME NUTS!!!

I have followed all manner of tutorials on how to get samba working but none seem to work in my case. I am using Karmic Koala, I can see the shared folders but I cannot access the contents in the folder. I am trying to access from within VirtualBox and from another XP box on my network. The virtual machine is Windows 7 both are unable to access the contents of my shared folders. This is as close as I have come to creating shares with samba. 

```

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
	workgroup = workgroup
;	netbios name = frank-laptop
	;hosts allow = 127.0Yes
	;usershare owner only = False

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
	username map = /etc/samba/smbusers

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
;	encrypt passwords = yes

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
;	passdb backend = tdbsam

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
	guest ok = yes
	guest account = sambausr

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares.  This will share each
# user's home directory as \\server\username
[homes]
	comment = Home Directories
;	browseable = yes

# By default, the home directories are exported read-only. Change the
# next parameter to 'no' if you want to be able to write to them.
;	read only = yes

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

[projects]
	path = /media/ACER/document storage/projects
	writeable = yes
;	browseable = yes
	guest ok = yes

[document storage]
	path = /media/ACER/document storage
	writeable = yes
;	browseable = yes
	guest ok = yes
```

This is my smb.conf 

my sambausers is 
```
username = “sambausr”
```

I have added the users and synced them, I have tried making the sambausr the owner of the share and nothing. Please help!

---

### Post by frankhdz on 2009-12-18
Please help!!! Anyone!!

---

### Post by Bucky Ball on 2009-12-18
> **frankhdz said:**
> Please help!!! Anyone!!


You would be MUCH better off creating a new thread with a descriptive title and as much info as possible about your issues. You will not get much help on this very old thread buried a few posts deep. Try your luck. ;)

---

