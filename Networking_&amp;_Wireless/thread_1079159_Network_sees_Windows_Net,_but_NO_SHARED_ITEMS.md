---
title: "Network sees Windows Net, but NO SHARED ITEMS"
date: 2009-02-24
forum: Networking &amp; Wireless
---

### Post by oldsoundguy on 2009-02-24
Did a downgrade to 8.04 for the sake of reclaiming control over my NVidia and monitor options .. that worked!
HOWEVER, when I go to Places> Network>  it sees the Windows network, but when I click on it .. NO SHARED items show up.
I can go to the Windows box and open Network and everything is there including all of the Linux items set up to share!
(yes, samba installed)
I can access the printers on those windows boxes and print to them, so the network IS working.

Suggestions?

---

### Post by Florida Cracker on 2009-02-24
Here is how I got mine to work:
I did a sudo gedit on my nsswitch.conf file and added wins in front of dns in the hosts:files line.
hosts:files ######## wins dns ####### (like this)
You also have to set the IP address in hosts tab in networking (through system/administration) for each machine you want to access. 

Hope this helps.

---

### Post by oldsoundguy on 2009-02-24
thanks .. but don't have anything in the nsswitch.conf file to change .. file is blank.

---

### Post by Florida Cracker on 2009-02-24
Give this a try
sudo gedit /ect/nsswitch.conf

---

### Post by sms0611 on 2009-02-24
I've just solved this exact same problem as follows:

1) my pc -> tools -> folder options
set enable simple file sharing ON

2) re-run network setup wizard

3) re boot 

It worked for me.

---

### Post by oldsoundguy on 2009-02-24
cracker ... that is the command I used .. nothing in the file to edit.

sms .. I am using XP on the boxes ..  no can do that way.  First off no "my pc" .. "my COMPUTER", yes .. and that option is not available under the folder options.

---

### Post by oldsoundguy on 2009-02-26
Follow Up:
Still no joy when gong to the network via places ........

BUT, I can get to the Windows machines via Nautilus .. VERY WEIRD!!!!!

Any ideas?

---

### Post by Florida Cracker on 2009-03-02
Just wondering if you solved your problem yet?
Forgive my ignorance (I'm new to linux) but shouldn't you have a nsswitch.conf file? I am running 8.04 desktop and I have one. Maybe something didn't get loaded when you downgraded. Just a thought.

---

### Post by oldsoundguy on 2009-03-02
nsswitch.conf file EXISTS .. just nothing to edit, no text in the file.

Getting to where I need to go via Nautilus right now .. a bit convoluted!  At least I can play the tunes stored on those Windows machines!  And I can move files INTO those drives via another method ... just would be nice to have them show up like they used to.  Was a LOT easier that way.

---

### Post by Florida Cracker on 2009-03-02
If you gedit something thats not there, it will create it as an empty file. Here is mine if it helps.

# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

When I put wins in the hosts: line all my windows computers showed up. I battled this problem for a long time and I know your frustration. Remember that I am a nube just trying to help. I know windows like the back of my hand but this linux is quite different.

---

### Post by Florida Cracker on 2009-03-02
I went into add/remove and looked to see what I had installed for networks and here is whats on mine:
Network
Network Tools
Samba
Services
Users and Groups

I tryed installing many things trying to get networking to work but when something didn't work I removed them. Maybe someone with more knowledge will chime in and tell us what nsswitch.conf is associated with and if it is included with the default install.

---

### Post by oldsoundguy on 2009-03-02
What you fail to understand here is THE NETWORK WORKS.  I can print to and from any computer, I can use Nautilus and see and access and download and upload files and folders, I am on line with all 7 units.  It is just that in:
Places> Network> Windows Network> MSHome (that is the default name and I kept it) .... NO WINDOWS computers show up. Yet, the MS network has been activated and the special files and folders granted access. (I can swap between Windows machines, so I know the net is working there!)

That particular method of access is the easiest when I want to migrate files and folders across the network as it is DRAG AND DROP.

---

### Post by Florida Cracker on 2009-03-02
Sorry for failing to understand.

---

### Post by bab1 on 2009-03-02
> **Florida Cracker said:**
> ...
I tryed installing many things trying to get networking to work but when something didn't work I removed them. Maybe someone with more knowledge will chime in and tell us what nsswitch.conf is associated with and if it is included with the default install.

Answering you question directly; the nsswitch file is used to set the order in which various data stores for host naming and user id are queried.  See here for a detailed explination:
[http://linux.die.net/man/5/nsswitch.conf]("http://linux.die.net/man/5/nsswitch.conf")

The naming service switch (nsswitch.conf) is not needed unless you are using WINS for NetBIOS or NIS and as such is not configured in a basic Samba install.  it's there but in its default config.  See the hyperlink above.


Maybe I can help with some concepts and ideas.  I have 2 Samba installations.  One is Gutsy (7.10) and the other is Hardy (8.10).  Both interact with Windows XP hosts in both directions eg. both sharing as seeing shares.

Probably the most important concept to grasp is that there are several ways to set up Samba.  First with the desktop environment (Gnome/Nautilus or Kubuntu).  I call this GUI.  You can also setup Samba with middle ware such as Webmin or eBox.  I call this helperware.  Lastly you can configure Samba with the direct config files.  This would be /etc/samba/smb.conf.  If you want to use NetBIOS for name service then you need WINS and the /etc/nsswitch file.

Before choosing a method to do the above, you should have the basic networking in place.  Most current installations use either a properly configured /etc/host file or DNS for naming services.  This means when we ping a host by its name we mean its hostname.  If we rely on NetBIOS/WINS and /etc/nsswitch then we are calling the host by its COMPUTER NAME. They are different.

Going back to the Samba config itself.  Straight out let me say that using webmin alters some essential core elements of Ubuntu and is not recommended for use by Debian or Ubuntu.  Furthermore from what I know it is not supported anymore by its developer.

If you wish to graphically configure Samba via helperware then I would suggest eBox.  If you use Gnome (Nautilus) then the config files are at /var/lib/samba.  

In my experience all of these are secondary to the manual (direct) configuration of the /etc/samba/smb.conf file.  You can completely configure samba with this basic file as long as you do not have any Win95/98/me or NT hosts in your network.  Windows has not required NetBIOS  (as these older versions did) since Win2k.

Of somewhat lesser concern, but still important to note, is the fact that Gnome sharing uses gvfs libs for sharing and the configuration that is setup via the /etc/samba/smb.conf uses the samba core libs and smbfs.  These can have different results and   causes confusion when the users get differing results.   

All of this means that you have to be specific and clear on what you are doing.

---

### Post by oldsoundguy on 2009-03-02
bab1, I just want the darn windows boxes to show up in the places/network!! LOL  For ease of transfer.  A bit too much work to move stuff around when I can't mount the darn drives/folders/files on the desktop!  Still can do it, but why, if I can get the places to WORK?

---

### Post by bab1 on 2009-03-02
> **oldsoundguy said:**
> bab1, I just want the darn windows boxes to show up in the places/network!! LOL  For ease of transfer.  A bit too much work to move stuff around when I can't mount the darn drives/folders/files on the desktop!  Still can do it, but why, if I can get the places to WORK?

So what are you saying?  If you are concise maybe I can help.

---

### Post by oldsoundguy on 2009-03-03
can't be much more concise than I have already been since I STARTED this thread.

---

### Post by bab1 on 2009-03-03
> **oldsoundguy said:**
> can't be much more concise than I have already been since I STARTED this thread.

Maybe that's why you haven't arrived at an answer.  If you want help you need to be willing to participate in the solution.

What have you done to diagnose the problem?  Were you ever able to  act as a client from the Linux host?  Are you even sure that the client part of the Samba suite is installed?

---

### Post by oldsoundguy on 2009-03-03
network works.
printers all share with each others.
all 7 computers ON LINE
all linux computers show up under places>network
NONE (2) of the Windows computers show up under places>network but the HOME NETWORK does .. just nothing listed under that icon.
I can access all of the computers permitted objects via using Nautilus entering the url of the machine and manipulate and use the files that way.  

I just want the computers to show up in NETWORK as it is easier to use the network that way.

---

### Post by bab1 on 2009-03-03
> **oldsoundguy said:**
> network works.
printers all share with each others.
all 7 computers ON LINE
all linux computers show up under places>network
NONE (2) of the Windows computers show up under places>network but the HOME NETWORK does .. just nothing listed under that icon.
I can access all of the computers permitted objects via using Nautilus entering the url of the machine and manipulate and use the files that way.  

I just want the computers to show up in NETWORK as it is easier to use the network that way.

I'm going to assume that the workgroup is the same for all hosts (Windows and Linux).  I have a suspicion that you have not installed smbfs.

This can be check in synaptics or you can just reinstall it.

From the CLI it would be:

```

sudo apt-get install smbfs

```

---

### Post by oldsoundguy on 2009-03-03
already done .. still and all, removed and re-installed .. still no joy!

---

### Post by bab1 on 2009-03-03
Thisis for sure a browsing problem.  usually I have probs when the browsemaster is undetermined (first starting up).  This usually means my entire network doen't appear when I click on the network icon.

As the workgroup defines the browse domain; are you absolutely sure that the windows hosts are in the workgroup defined in the /etc/samba/smb.conf file.  I have never set this part up with the GUI.  Is there someplace using the GUI you can check to make sure all the hosts are in the same workgroup?

Edit:  The browse domain will not stop you from connecting, just browsing the objects in Nautilus.  Just as you say your problem is...

---

### Post by dmizer on 2009-03-03
Please post the output of the following commands (copy paste):
```
cat /etc/samba/smb.conf
```
```
cat /etc/nsswitch.conf
```
```
ps aux | grep winbind
```
```
sudo iptables -L
```
```
smbtree
```

Please be sure to wrap each output in bbc markup code brackets like so:
[noparse]```
command output
```[/noparse]

---

### Post by oldsoundguy on 2009-03-03
Not sure how to wrap these up, so here they are, warts and all.

```
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



```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```


```
root      5245  0.0  0.1   8084  1336 ?        Ss   Mar02   0:00 /usr/sbin/winbindd
root      5282  0.0  0.1   8208  1680 ?        S    Mar02   0:00 /usr/sbin/winbindd
root      5309  0.0  0.1   8092  1272 ?        S    Mar02   0:00 /usr/sbin/winbindd
root      5313  0.0  0.0   8084   868 ?        S    Mar02   0:00 /usr/sbin/winbindd
dave      7506  0.0  0.0   3004   744 pts/0    R+   07:40   0:00 grep winbind
```


```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```         


```
WORKGROUP
	\\DAVE-DESKTOP   		dave-desktop server (Samba, Ubuntu)
		\\DAVE-DESKTOP\LaserJet_6MP   	HP Laserjet
		\\DAVE-DESKTOP\OFFICEJET-PRO-1150C	3 in 1
		\\DAVE-DESKTOP\OfficeJet_6110 	4 in 1 HP
		\\DAVE-DESKTOP\OfficeJet_Pro_1150C	3 in 1
		\\DAVE-DESKTOP\PDF            	PDF
		\\DAVE-DESKTOP\PhotoSmart_P1215	hpphoto
		\\DAVE-DESKTOP\Print_to_PDF   	Print to a PDF File
		\\DAVE-DESKTOP\Stylus_Photo_R1800	Epson Photoprinter
		\\DAVE-DESKTOP\IPC$           	IPC Service (dave-desktop server (Samba, Ubuntu))
		\\DAVE-DESKTOP\print$         	Printer Drivers
	\\ATRIUM         		atrium server (Samba, Ubuntu)
		\\ATRIUM\LaserJet_6MP   	Laser
		\\ATRIUM\OFFICEJET-PRO-1150C	3 in 1
		\\ATRIUM\OfficeJet_6110 	4 in 1
		\\ATRIUM\PhotoSmart_P1215	HP PhotoSmart
		\\ATRIUM\print$         	Printer Drivers
		\\ATRIUM\IPC$           	IPC Service (atrium server (Samba, Ubuntu))
MSHOME
	\\UBUNTUGUESTROOM		ubuntuguestroom server (Samba, Ubuntu)
		\\UBUNTUGUESTROOM\PhotoSmart_P1215	HP PhotoSmart
		\\UBUNTUGUESTROOM\print$         	Printer Drivers
		\\UBUNTUGUESTROOM\IPC$           	IPC Service (ubuntuguestroom server (Samba, Ubuntu))
	\\NONE-Y9Z4SBI3OS		Big Boy
		\\NONE-Y9Z4SBI3OS\G              	
		\\NONE-Y9Z4SBI3OS\F              	
		\\NONE-Y9Z4SBI3OS\M              	
		\\NONE-Y9Z4SBI3OS\Printer5       	Avery PLP9100
		\\NONE-Y9Z4SBI3OS\Printer4       	Avery PLP9100 (Copy 1)
		\\NONE-Y9Z4SBI3OS\Printer3       	EPSON Stylus Photo R1800
		\\NONE-Y9Z4SBI3OS\HPLaserJ       	HP LaserJet 6P/6MP PostScript
		\\NONE-Y9Z4SBI3OS\My Download Files	
		\\NONE-Y9Z4SBI3OS\Printer6       	Adobe PDF
		\\NONE-Y9Z4SBI3OS\D              	
		\\NONE-Y9Z4SBI3OS\hpoffice       	hp officejet 6100 series
		\\NONE-Y9Z4SBI3OS\print$         	Printer Drivers
		\\NONE-Y9Z4SBI3OS\SharedDocs     	
		\\NONE-Y9Z4SBI3OS\IPC$           	Remote IPC
	\\GUEST          		WinBLOWS bedroom box
		\\GUEST\G              	
		\\GUEST\DownloadFiles  	
		\\GUEST\QMSmagic       	QMS magicolor 2 DeskLaser
		\\GUEST\usbdrive1      	
		\\GUEST\M              	
		\\GUEST\hpphotos       	hp photosmart 1215 series
		\\GUEST\print$         	Printer Drivers
		\\GUEST\SharedDocs     	
		\\GUEST\IPC$           	Remote IPC
	\\DAVE-DESKTOP   		dave-desktop server (Samba, Ubuntu)
		\\DAVE-DESKTOP\LaserJet_6MP   	HP Laserjet
		\\DAVE-DESKTOP\OFFICEJET-PRO-1150C	3 in 1
		\\DAVE-DESKTOP\OfficeJet_6110 	4 in 1 HP
		\\DAVE-DESKTOP\OfficeJet_Pro_1150C	3 in 1
		\\DAVE-DESKTOP\PDF            	PDF
		\\DAVE-DESKTOP\PhotoSmart_P1215	hpphoto
		\\DAVE-DESKTOP\Print_to_PDF   	Print to a PDF File
		\\DAVE-DESKTOP\Stylus_Photo_R1800	Epson Photoprinter
		\\DAVE-DESKTOP\IPC$           	IPC Service (dave-desktop server (Samba, Ubuntu))
		\\DAVE-DESKTOP\print$         	Printer Drivers
	\\DAVE-CRASH-TEST		dave-crash-test-dummy server (Samba, Ubuntu)
		\\DAVE-CRASH-TEST\LaserJet_6MP   	HP Laserjet
		\\DAVE-CRASH-TEST\OFFICEJET-PRO-1150C	3 in 1
		\\DAVE-CRASH-TEST\OfficeJet_6110 	4 in 1 HP
		\\DAVE-CRASH-TEST\OfficeJet_Pro_1150C	3 in 1
		\\DAVE-CRASH-TEST\PhotoSmart_P1215	hpphoto
		\\DAVE-CRASH-TEST\Print_to_PDF   	Print to a PDF File
		\\DAVE-CRASH-TEST\Stylus_Photo_R1800	Epson Photoprinter
		\\DAVE-CRASH-TEST\IPC$           	IPC Service (dave-crash-test-dummy server (Samba, Ubuntu))
		\\DAVE-CRASH-TEST\print$         	Printer Drivers
```


As I have noted several times before and apparently most have not read, the issue is with the MSHOME icon which designated the windows machines in the past.  once that is reached, there  is nothing showing.  Neither of the Windows machines register there..

---

### Post by bab1 on 2009-03-03
> As I have noted several times before and apparently most have not read, the issue is with the MSHOME icon which designated the windows machines in the past. once that is reached, there is nothing showing. Neither of the Windows machines register there..

...and both dmizer and I are working towards that end.  I asked if you were sure that all the hosts were in the same workgroup.  This is needed to be able to browse them correctly.

Dmizer asked that you send the contents of the /etc/samba/smb.conf file and you sent only part of it.  The answer is in the part you did not send.  Send the [global] section of that file.

Reading the partial results from what you have sent indicates that you do NOT have everything in one workgroup

---

### Post by oldsoundguy on 2009-03-03
sorry, the highlight must had upscrewed:

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
# Any line which starts with a ; (semi-colon) or a # (hash) 
# is a comment and is ignored. In this example we will use a #
# for commentary and a ; for parts of the config file that you
# may wish to enable
#
# NOTE: Whenever you modify this file you should run the command
# "testparm" to check that you have not made any basic syntactic 
# errors. 
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
;   wins support = no

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
;   bind interfaces only = true



#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Cap the size of the individual log files (in KiB).
   max log size = 1000

# If you want Samba to only log through syslog then set the following
# parameter to 'yes'.
;   syslog only = no

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
;   security = user

# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.  
   passdb backend = tdbsam

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

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

# This option controls how nsuccessful authentication attempts are mapped 
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
;   logon path = \\%N\%U\profile

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U

# The following setting only takes effect if 'domain logons' is set
# It specifies the script to run during logon. The script must be stored
# in the [netlogon] share
# NOTE: Must be store in 'DOS' file format convention
;   logon script = logon.cmd

# This allows Unix users to be created on the domain controller via the SAMR
# RPC pipe.  The example command creates a user account with a disabled Unix
# password; please adapt to your needs
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u

########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
;   load printers = yes

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
   socket options = TCP_NODELAY

# The following parameter is useful only if you have the linpopup package
# installed. The samba maintainer and the linpopup maintainer are
# working to ease installation and configuration of linpopup and samba.
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &

# Domain Master specifies Samba to be the Domain Master Browser. If this
# machine will be configured as a BDC (a secondary logon server), you
# must set this to 'no'; otherwise, the default behavior is recommended.
;   domain master = auto

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
# Replace 'ntadmin' with the name of the group your admin users are
# members of.
;   write list = root, @ntadmin

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

### Post by bab1 on 2009-03-03
You have 2 workgroups defined.  Some of the hosts are in MSHOME and some hosts are in WORKGROUP.

This can be seen here.
```
WORKGROUP [COLOR="Red"]<--Browse domain (aka workgroup)[/COLOR]
\\DAVE-DESKTOP dave-desktop server (Samba, Ubuntu)
\\DAVE-DESKTOP\LaserJet_6MP HP Laserjet
\\DAVE-DESKTOP\OFFICEJET-PRO-1150C 3 in 1
\\DAVE-DESKTOP\OfficeJet_6110 4 in 1 HP
\\DAVE-DESKTOP\OfficeJet_Pro_1150C 3 in 1...

...\\ATRIUM\OfficeJet_6110 4 in 1
\\ATRIUM\PhotoSmart_P1215 HP PhotoSmart
\\ATRIUM\print$ Printer Drivers
\\ATRIUM\IPC$ IPC Service (atrium server (Samba, Ubuntu))
MSHOME  [COLOR="Red"]<- Browse domain (aka workgroup)[/COLOR]
\\UBUNTUGUESTROOM ubuntuguestroom server (Samba, Ubuntu)
\\UBUNTUGUESTROOM\PhotoSmart_P1215 HP PhotoSmart


```
And is confirmed here.
```

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = WORKGROUP [COLOR="Red"]<- Change this to match MSHOME[/COLOR]

```

**[COLOR="Blue"]Make a copy of the /etc/samba/smb.conf file.[/COLOR]**
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bkp
```

Then edit the file.

---

### Post by oldsoundguy on 2009-03-03
no joy again .. now I still have two workgroups (MSHOME and Workgroup and my Linux machines are now split between them.  Still no Windows machines.

Think I will wait on "fixing" this for several other inputs and opinions.

---

### Post by bab1 on 2009-03-03
As you wish.  We have found that the problem is worgroup related.  Make sure that ***all hosts*** in the network are in the same workgroup.

---

### Post by BajaPaul on 2009-03-03
OldSoundGuy,  I have the exact same problem with 8.04 and still have not figured it out yet.  It is very fustrating.  When I click Places>Home I have setup my Windows mounts in the sidebar so they are easy to get too such as smb://h1/public/

But it will not show me the windows root if I revise it to smb://h1/ by backspacing.  I just have a blank window and the Public folder or any other shares don't show up.  I can get to all my share by typing but can never see anything at the Windows root.  I am running Vista on the Windows side.

If you click Places>Network I get network:/// and a Windows Network icon shows up.  Click that and I get smb:/// but no more icons.

You can add the pyNeighborhood program thru Alpications>Add/Remove and it shows all my shares in a nice structured order but I can't mount any of them thru it.

You can add the sidebar shortcuts via Places>"Connect to Server" and choose windows share as service type, H1 in my case as Server, Public in my case as Share, then click add bookmark at bott of the window and give it a name such as "Public on H1".

It helps but has not fixed the problem...  Maybe it does explain it better so someone can help us all out.  Many are having this exact same problem.

I did enter a different name, used root, and it bought up a screen asking for my password but showed my workgroup as Domain.  It will not accept any password I know of.  Another clue?  Is a workgroup really a domain too?

Paul

---

### Post by dmizer on 2009-03-03
> **bab1 said:**
> Make sure that ***all hosts*** in the network are in the same workgroup.

Indeed. Doesn't matter how you accomplish this, but all your computers must be in the same workgroup. If you want your workgroup to be "mshome", you'll have to edit DAVE-DESKTOP and ATRIUM as bab1 outlined in post #27.

Also, you still need to edit /etc/nsswitch conf.

Enter this command in terminal:
```
gksudo gedit /etc/nsswitch.conf
```
Add "wins" to the file *_exactly_* like so:
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR="Red"]wins[/COLOR] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```

Save the file and reboot. If you edit this file and you discover that there is [nothing in the file](http://ubuntuforums.org/showpost.php?p=6794754&postcount=6), you've done something wrong, so please review the directions as you may have missed a character or typed something incorrectly.

To wrap terminal output in code boxes, use the bbc code markup I outlined earlier:

[COLOR="Red"]**[noparse]```
[/noparse]**[/COLOR]command output here[COLOR="Red"]**[noparse]
```[/noparse]**[/COLOR]

---

### Post by oldsoundguy on 2009-03-23
For those that had some validity in their posts, thanks  .. but had to do this one the hard way.
1)un-install the network manager (from synaptic)
2)shut down
3)remove network sharing from the Windows machines
4)turn on Ubuntu
5)re-install the network manager (from synaptic)
6)re-install network sharing on the Windows boxen
7)re-boot the Ubuntu machine
8)SUCCESS!!
What with 3 different platforms, a router, wired and wireless all involved, no way to find the problem via software.

---

