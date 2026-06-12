---
title: "Samba why is it so recalcitrantly imposible with windows7?"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2012-11-10
simply following guides always leads to failures on my home network

like just tried this one
[http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/)

nothing works with samba and me for a long long time and many ubuntu versions.

How can I share ubuntu files onto a windows 7 PC easily?

---

### Post by critin on 2012-11-10
I'm sorry it doesn't work for you.  This is the guide I used when creating the lan for my ubuntu, XP, Win8 machines.  Though I had a bit of trouble in the beginning, after I figured out it wanted both the password for the workgroup and then the password for ubuntu, it worked and have had no real issues since.

I have noticed more than one Samba download in the Software Manager-- Be sure and use the same one in the tutorial.

I can't help you and I regret that.  I wish I could but you've probably followed the guide to a T already.    Samba is the simplest IMO, because there is no messing with paths, etc. 

Have you gotten anywhere at all?

---

### Post by sdowney717 on 2012-11-10
Not yet.
I noticed the win7 pc workgroup name is "WORKGROUP"

When I try to type "WORKGROUP" into the server field in Samba, close and reopen is always lowercase. Does case matter?

---

### Post by sdowney717 on 2012-11-10
[http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/](http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/)

This here worked!

you have to do a run command in win7

> To access the shares from Windows 7, go to Start &#8211;> All Programs &#8211;> Accessories &#8211;> Run and type the share path as shown below.

\\IP Address or Hostname\shared_name

at least I was able to access a shared folder this way.
For some reason, win7 I can not see any shares, I have to type in a direct link.
Why is that!

---

### Post by uclugLee on 2012-11-10
For simplicity, create a folder on the root of the C drive on the Windows 7 machine and call it whatever you want, but for this we'll call it Files.  Once the file is created, right-click on it and go to properties.  Now click on the sharing tab and click the share button.  Hit the dropdown box to show "Everyone" and hit Add.  Now change the permissions to "Everyone" to "read/Write".  Hit Share and you will get a confirmation message that the folder is now shared with the folder path: \\192.168.1.254\Files (or whatever your computer IP address or hostname is)

Now on your Ubuntu machine, open your home folder, and then select File - Connect to server.

On the Connect To Server screen, fill it out like this:
[IMG]http://webpages.charter.net/ucluglee/Linux/Screenshot%20from%202012-11-10%2022:55:09.png[/IMG]
Change type to Windows Share
Server: IP or hostname of your Windows 7 computer
Share: Shared folder you created on your Win7 computer
Username and Password: Windows 7 computer credentials
Select the Remember This Password box to keep the connection alive.

If this doesn't work, check your Windows firewall settings or possibly any firewall software installed on the Win7 computer.

---

### Post by sdowney717 on 2012-11-10
ok, thanks I will give these ideas a go.
So far I was able to forcefeed windows the server location.

I thought win7 would automatically discover the Ubuntu machine? But no, I had to type in like \\192.168.1.102\sharedfoldername in order for windows to even see it from the run command. once I did that, I was able to see all the other shared folders. The first guide left out that step, the second one worked.

---

### Post by critin on 2012-11-10
> **sdowney717 said:**
> Not yet.
I noticed the win7 pc workgroup name is "WORKGROUP"

When I try to type "WORKGROUP" into the server field in Samba, close and reopen is always lowercase. Does case matter?

Mine is lower case also, and it works.  I really don't remember if I typed it that way or not, probably not.

---

### Post by critin on 2012-11-10
> **sdowney717 said:**
> [http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/](http://www.liberiangeek.net/2012/05/windows-7-vs-ubuntu-12-04-how-to-enable-advanced-file-sharing/)

This here worked!

you have to do a run command in win7



at least I was able to access a shared folder this way.
For some reason, win7 I can not see any shares, I have to type in a direct link.
[COLOR=Red]**Why is that!**[/COLOR]

I don't know, but it's exactly what I don't like to do--paths.  I don't have to and really can't understand why it isn't easy for others.

Be sure and allow shares in windows when you're setting up the network group.

Since I have nothing to hide or lose, I have no restrictions at all.  No encrypted passwords that I enter once and then tell windows to remember forever so I don't have to enter each time.  I allow everyone in Samba users.  The user is 'share',  the guest is 'nobody' no password.  Most people prefer not to be this lenient.

I just added a new system to the network and all I did was install Samba, allowed shared folders and files, let samba install the permissions there, and bingo!  I can use it on any machine.  I just tested it.  I'm not doing anything special so it must be the machines.

You do have to restart them.

---

### Post by critin on 2012-11-10
> The first guide left out that step, the second one worked.

Again, I used the first guide and did not have to add the IP.   
Glad you got it working!!

---

### Post by sdowney717 on 2012-11-11
I did do several restarts on both machines, however the win7 machine displays nothing, you must enter in the server share addresses every single time.

So it is partially solved and partially still mysterious as ever for me using samba.

---

### Post by Morbius1 on 2012-11-11
Based only on your posts some possible issues:

[1] NMBD isn't running. Try starting it:
```
sudo service nmbd start
```[2] Your host name is too long.

Run the following command:
```
hostname
```Count the number of characters. If it 16 or more no one can see your machine. The easiest way to fix this is through Samba itself:

Edit smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```Add a line to the [global] section:
```
netbios name = something
```[COLOR=Blue]*"something" must be 15 characters or less in length.*[/COLOR]

Then restart samba:
```
sudo service smbd restart
sudo service nmbd restart
```Wait a few minutes for the network to settle down and see if the Windows box can see your Linux machine.

---

### Post by sdowney717 on 2012-11-11
looks ok here
> scott@scott-P5QC:~$ sudo service nmbd start
[sudo] password for scott: 
start: Job is already running: nmbd
scott@scott-P5QC:~$ hostname
scott-P5QC
scott@scott-P5QC:~$ gksu gedit /etc/samba/smb.conf



Here is ny samb config netbios name = something, what does it do?
I dont see netbios name listed.
I do see this
> # This will prevent nmbd to search for NetBIOS names through DNS.
	dns proxy = no

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
	workgroup = workgroup

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
	username map = /etc/samba/smbusers
	security = user
;	guest ok = no
;	guest account = nobody

#======================= Share Definitions =======================

# Un-comment the following (and tweak the other settings below to suit)
# to enable the default home directory shares. This will share each 
# user's home director as \\server\username
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
# with access to the samba server. Un-comment the following parameter
# to make sure that only "username" can connect to \\server\username
# The following parameter makes sure that only "username" can connect
#
# This might need tweaking when using external authentication schemes
;   valid users = %S

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   read only = yes

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

[Downloads]
	path = /home/scott/Downloads
;	available = yes
;	browsable = yes
	public = yes
;	writable = No

[CM93ed2_2009]
	path = /home/scott/CM93ed2_2009
;	writeable = No
	browseable = no
	guest ok = yes

[movies]
	path = /media/26E82022E81FEEB5/movies
	writeable = yes
;	browseable = yes
	guest ok = yes

[392 ih rebuild]
	path = /home/scott/392 ih rebuild
	writeable = yes
;	browseable = yes
	guest ok = yes
```

---

### Post by sdowney717 on 2012-11-11
ok I just put netbios name = something in the config and did a restart

> cott@scott-P5QC:~$ sudo service smbd restart
[sudo] password for scott: 
smbd stop/waiting
smbd start/running, process 8538
scott@scott-P5QC:~$ sudo service nmbd restart
nmbd stop/waiting
nmbd start/running, process 8552
scott@scott-P5QC:~$ 


---

### Post by sdowney717 on 2012-11-11
ok, still not working for discovery on win7

screen shot from the win7 pc does not show the ubuntu machine

---

### Post by critin on 2012-11-11
I think the issue is in the windows setup. Check each step again from the first link you posted. Especially allowing connection to all networks.

One thing I do that you didn't is change the workgroup / homegroup name.  I gave windows workgroup a new group name (greentea)  and it gave me a password.  I entered that name in all machines Samba. 

 I did have to enter the group password on all 'buntu's the first time, then the 'buntu password, then the files open.

---

### Post by sdowney717 on 2012-11-11
Whats in a name, what would be the difference really between leaving it 'workgroup' or something else.

Your green tea should be my workgroup. 

Wife is using the PC at the moment so dont want to disturb what we got working. One thing is the files dont show up with image icons. She is working with pictures and would like to see them like small images appear in Ubuntu file manager. Is that some issue with networking, not doing that? So she has to click on a picture to open it in photo viewer, and if she likes it she writes the file name down, unbelievable, considering she has hundreds to look at.

I am telling her to try and use Ubuntu PC. It is working with shutterfly ok on the web.

---

### Post by Morbius1 on 2012-11-11
[1] Change the name resolution order:
Edit smb.conf and under the workgroup line add the following:
```
name resolve order = bcast host lmhosts wins
```
The restart samba:
```
sudo service smbd restart
```

And remember to wait a few minutes after each samba restart before trying to see the machine from a client.

[2] If that doesn't fix it post the output of this command:
```
smbtree
```

[3] I personally don't change the workgoup name itself and I have 4 on my network. It shouldn't be an issue if you are all connected to the same router.

---

### Post by critin on 2012-11-11
> **sdowney717 said:**
> Whats in a name, what would be the difference really between leaving it 'workgroup' or something else.

Your green tea should be my workgroup. 

Wife is using the PC at the moment so dont want to disturb what we got working. One thing is the files dont show up with image icons. She is working with pictures and would like to see them like small images appear in Ubuntu file manager. Is that some issue with networking, not doing that? So she has to click on a picture to open it in photo viewer, and if she likes it she writes the file name down, unbelievable, considering she has hundreds to look at.

I am telling her to try and use Ubuntu PC. It is working with shutterfly ok on the web.

What's in a name indeed.  lol   Windows has priority on the name 'workgroup/homegroup'  They don't like intruders.  Adding a workgroup to windows means 'adding another group', not adding to their workgroup.  Another group will have another name, logical?  Windows will add other windows all day long, but a buntu -- not so quickly.  It goes to that 'other' group.  lol

She should be able to open the machine from Browse Network in filemanager.  The pics will be in their folder and it will open as it does in windows.  I must use a viewer or slide show in windows to see each pic, so it works the same for me.

---

### Post by sdowney717 on 2012-11-11
ok here it is, still not showing on win7 pc

```
scott@scott-P5QC:~$ smbtree
Enter scott's password: 
WORKGROUP
	\\SOMETHING      		scott-P5QC server (Samba, Ubuntu)
		\\SOMETHING\Kristinwedding 	539gb
		\\SOMETHING\392rebuild     	
		\\SOMETHING\pics           	539gb
		\\SOMETHING\maps           	
		\\SOMETHING\my_pix         	539gb
		\\SOMETHING\kristinjune262005	126gb
		\\SOMETHING\camerapictures 	126gb
		\\SOMETHING\392ihrebuild   	
		\\SOMETHING\jessicajune262005	126gb
		\\SOMETHING\1kristinpicture	126gb
		\\SOMETHING\jessica        	126gb
		\\SOMETHING\HP-LaserJet-4000	HP LaserJet 4000
		\\SOMETHING\IPC$           	IPC Service (scott-P5QC server (Samba, Ubuntu))
		\\SOMETHING\392 ih rebuild 	
		\\SOMETHING\movies         	trial
		\\SOMETHING\Downloads      	
		\\SOMETHING\print$         	Printer Drivers
scott@scott-P5QC:~$ 

```

---

### Post by gerowen on 2012-11-11
I've always had terrible luck with Samba.  It has always been slow for me, when it worked, and sometimes even stalls during transfers.  Even the built-in Windows FTP client runs really slow for some reason so hosting your files via FTP doesn't seem to make any real difference, although it has been what I've done, and just use Filezilla as a client to download files.

Depending on how much information  you're sharing you could give Ubuntu One a try, they have a Windows client for it.
[https://one.ubuntu.com/downloads/windows/](https://one.ubuntu.com/downloads/windows/)

---

### Post by critin on 2012-11-11
Opening my pic folder gives me icons,  in preferences you can choose to show thumbnails.

---

### Post by sdowney717 on 2012-11-11
yes, but she is on the win7 pc and it does not show the files as images like Ubuntu does. Your showing me your ubuntu PC, how about a view from a win7 PC accessing picture files on an ubuntu PC?
What do you see then?

---

### Post by Morbius1 on 2012-11-11
There's 5 things required for browsing by host name

You've done 3:

** Netbios name has to be 15 characters or less in length.
** bcast should be listed first in the name resolve order - in a home network anyway.
** nmbd has to be running

Just 2 more things should be checked:

[] Are the Windows box and the Linux box in the same subnet?

[] Firewall is in the way.

Install the following package:
```
sudo apt-get install nmap
```Then run the following command twice and post the output:
```
sudo nmap -sS -sU -T4 192.168.0.100
```Run it first substituting the ip address of your Linux box for 192.168.0.100 and again with the ip address of the Windows machine.

---

### Post by sdowney717 on 2012-11-11
ok, I am 192.168.1.103
> eth1      Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe54:faa6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:953377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1516736 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:263069084 (263.0 MB)  TX bytes:1970178230 (1.9 GB)
          Interrupt:45 


```
scott@scott-P5QC:~$ sudo nmap -sS -sU -T4 192.168.1.103

Starting Nmap 5.21 ( http://nmap.org ) at 2012-11-11 13:05 EST
Nmap scan report for scott-p5qc.hr.cox.net (192.168.1.103)
Host is up (0.0024s latency).
Not shown: 1989 closed ports
PORT     STATE         SERVICE
22/tcp   open          ssh
111/tcp  open          rpcbind
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
2049/tcp open          nfs
68/udp   open|filtered dhcpc
111/udp  open          rpcbind
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm
2049/udp open          nfs
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.27 seconds
scott@scott-P5QC:~$ 

```


> scott@scott-P5QC:~$ nmblookup \*
querying * on 192.168.1.255
192.168.1.103 *<00>
scott@scott-P5QC:~$ 


ipconfig from the win7 machine

---

### Post by Morbius1 on 2012-11-11
So far so good.

Now is the Windows box in the same 192.168.1.XXX range?

And if you run the nmap command with the WIndows IP address do you get these ports open:
> 139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgmIf not turn the Windows firewall off to see if that is the issue.

---

### Post by sdowney717 on 2012-11-11
> scott@scott-P5QC:~$ sudo nmap -sS -sU -T4 192.168.0.2

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2012-11-11 13:16 EST
Note: Host seems down. If it is really up, but blocking our ping probes, try -PN
Nmap done: 1 IP address (0 hosts up) scanned in 2.04 seconds
scott@scott-P5QC:~$ 


So is the win7 machine on a different subnet?
The adapter settings for it are automatically assigned.

OK, yes the win7 machine is plugged into a voip linksys router, so it is getting it's IP from the voip router.

---

### Post by Morbius1 on 2012-11-11
They are in fact in different subnets. Normal default browsing isn't going to work.

Are both of these machines connect to the same router? If they are both getting their ip address from the same router I'm not sure how they can be in a different subnet.

If you issue this command from "Run" in Windows can it even access the Linux machine:
\\192.168.1.103

---

### Post by sdowney717 on 2012-11-11
All my main wireless router ports are full. 
I have plugged in
my PC
laserjet 4000
my voip router which has one in and one out, out goes to this win7 pc
my line running downstairs to my theatre PC for netflix etc...

So is there anything to do?

---

### Post by sdowney717 on 2012-11-11
> **Morbius1 said:**
> They are in fact in different subnets. Normal default browsing isn't going to work.

Are both of these machines connect to the same router? If they are both getting their ip address from the same router I'm not sure how they can be in a different subnet.

If you issue this command from "Run" in Windows can it even access the Linux machine:
\\192.168.1.103

yes, that brings up the folders.
we are able to share, but cant easily browse by way of the gui. So the wife has to type in IP numbers rather than click in the windows network icon. And that is more difficult. Because I could not see the Ubuntu PC shares.

Course, once the browse shares page is open, you can navigate the folders. Ubuntu machine though is invisible in network neighborhood.

If I share from the win PC, can Ubuntu see the windows PC?

And could I put the IP printer laser jet 4000 running off the voip router on a different subnet?

---

### Post by Morbius1 on 2012-11-11
I'm trying to think of an easy way around this issue ........

One thing you can do is "map" the Linux "network drive" in Windows 7 to say \\192.168.0.103\pics

But:

** You'd have to do that to all the shares individually.

[COLOR=Blue]**EDIT**[/COLOR]: Or you can create one shared folder on your Linux box say at /home/scott/Shared then create subfolders like pics, music, whatever so that only one mapping has to be made on the Windows end.

** And for this to work you'd have to give your Linux box a static ip address otherwise the next time it boots you might have a different ip address.

---

### Post by critin on 2012-11-11
> **sdowney717 said:**
> yes, but she is on the win7 pc and it does not show the files as images like Ubuntu does. Your showing me your ubuntu PC, how about a view from a win7 PC accessing picture files on an ubuntu PC?
What do you see then?

Not fair!  I don't use windows and had to search for 30 minutes for something called a 'snip tool' to even take a screenshot.   ubuntu simply uses the keyboard...then another 30 min finding where they were stored!  It said they would be on the clipboard, but where is the clipboard?  Search wouldn't tell me.     Ubuntu goes straight to them.

Windows does not give the option of thumbnails or even to view in an image viewer, not in right click anyway.  This is where ubuntu excels in yet another job.  User friendly?  You bet!

screenshots of network and picture folder in ubuntu as requested.

---

### Post by sdowney717 on 2012-11-11
You can use some built in windows tools to take screenshots and it is not as easy as Ubuntu.

Simpy when your on a screen hit cntrl-printscreen  together. this copies the image to the clipboard.
Clipboard is just a copy into memory of an image or text.
Then open paint under accessories.
Type cntrl-v to paste as an image.
then save the image.

I agree that Ubuntu can be much nicer to use.
Ubuntu screen shot has built in cropping which I use all the time.
 Wife is used to windows and gets stressed on Ubuntu. claims everything is all over the place. I use Gnome 3 and like it.

---

### Post by critin on 2012-11-11
> Clipboard is just a copy into memory of an image or text.

Of course!  Thanks.   I used to know that but it's been so long since I've used windows I'd forgotten the term.  lol  Copy/paste makes more sense.  heehe.  

My WinXP shows thumbnail view pics, but you probably don't have XP.  Sometimes, moving ahead in technology is actually going backwards.

---

### Post by sdowney717 on 2012-11-11
I am going to mark this solved since you guys were a big help figuring out the subnet issue and showing me some things. Also being an encouragement when I wanted to give up. Very much appreciated, thank you :P

---

### Post by theDaveTheRave on 2012-11-14
Hi,

just thought I would add a note for anyone else who comes across this thread.

You mention previously your setup for your wireless router....

> **sdowney717 said:**
> All my main wireless router ports are full. 
I have plugged in
my PC
laserjet 4000
my voip router which has one in and one out, out goes to this win7 pc
my line running downstairs to my theatre PC for netflix etc...

So is there anything to do?

If your main router is anything like a "standard" one (by that I mean all the ones that I have ever used) you should be able to make use of 2 particular setting within your network.

If you have a dedicated ubuntu pc that you use to store your <shared> folders and files, you may decide to set that up as a the principle DNS server. Then point all your equipment to this terminal for obtaining the local IP addresses. This will require you to turn of the ability of your router to give IP addresses (so it it no longer a DHCP controller, ie it should be 'de-activated'). Then if you have each client with it's own 'name' then you should be able to connect to it using that name as well as the IP address (client names are more stable than IP addresses)


You may need to perform a similar thing with your VOIP router, and you will most likely need to tell it where to get it's IP from.

The other method.

Set up the principle router as being the only DHCP server. 
In you main router you will have the option to set pre determined IP address to given MAC addresses.
If you connect each item one at a time you will see them connect and you can set the IP address for them from the router (I'm sure you can do this from a server also, but I have never done so), the only downside arrives when you change ISP and you have to reset up your box with the exact same details, not a problem if you only have a few clients, but now everyone has a phone, pad, laptop, desktop, cooker. fridge.... my pet dogs has a computer chip in her... sorry I digress...

When you connect your widows pc that is hooked in via the VOIP router you should see it appear on your main router and be able to allocate it a dedicated IP address. If not it may be that you need to find a way of changing the way your VOIP router works (I personaly have no experience of these, but I'm sure they are similar to normal routers in that they can give out specified IP addresses).

The problem with the VOIP router may be simply a way in setting up your network to pass through this box directly to your connected windows pc using the port forwarding ability of the VOIP router (if it has one).

It may also be expedient to perform an
```

nmap <IP.address.of.VOIProuter>

```

these are just thoughts for others to try and help out if they are trying to trouble shoot problems.

---

