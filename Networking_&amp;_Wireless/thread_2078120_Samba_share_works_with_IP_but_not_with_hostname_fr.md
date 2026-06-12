---
title: "Samba share works with IP but not with hostname from Windows 7"
date: 2012-10-30
forum: Networking &amp; Wireless
---

### Post by hari_pk on 2012-10-30
Hi,
I went through lot of threads with the same topic of not able to access samba share present in my Kubuntu machine from a Windows machine but couldnt resolve the problem, hence starting a new thread. Both the kubuntu and windows machines are in the same LAN. The hostname of my Kubuntu machine is 'ocean'. Some observations:

1. 'ping ocean' works fine in my windows machine
2. \\10.10.8.108 works fine in my windows machine where 10.10.8.108 is ip of the kubuntu machine
3. when i try \\ocean, getting error.

Please let me know how to resolve this problem.

---

### Post by Zorael on 2012-10-30
Are you in the same workgroup? (I'm not sure if it matters.)

---

### Post by hari_pk on 2012-10-31
Hi,
I checked in my Windows machine "Computer->Properties". Only domain name is set, Workgroup is not set to anything.

---

### Post by hari_pk on 2012-10-31
Contents of my smb.conf is as below:

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
   security = domain
   workgroup = WORKGROUP

# server string is the equivalent of the NT Description field
   server string = %h server (Samba, Ubuntu)
   netbios name = ocean

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
    name resolve order = wins lmhosts hosts bcast

#### Networking ####

# The specific set of interfaces / networks to bind to
# This can be either the interface name or an IP address/netmask;
# interface names are normally preferred
;   interfaces = 127.0.0.0/8 eth0
    interfaces = 10.10.8.108/255.255.255.0

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

[hari]
        path = /home/hari
        read only = no
;       browseable = yes
        valid users = hari

---

### Post by Morbius1 on 2012-10-31
Keep in mind that I don't use KDE so ....

The usual suspects:

** A service isn't running so start it:
```
sudo service nmbd start
```** Firewall is in the way:
```
sudo nmap -sS -sU -T4 10.10.8.108
```You need the following ports to be open:
> PORT     STATE         SERVICE
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
137/udp  open          netbios-ns
138/udp  open|filtered netbios-dgm** Unless you had a specific reason for doing so your "name resolve order" is literally the opposite of what it should be. It should be this:
```
name resolve order = bcast host lmhosts wins
```[COLOR=Blue]*BTW, it's host not hosts*[/COLOR]

---

### Post by hari_pk on 2012-11-01
Hi Morbius,

1. sudo service nmbd start shows "start: Job is already running: nmbd"

2. sudo nmap -sS -sU -T4 10.10.8.108 shows below:


Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2012-11-01 09:45 GMT
Interesting ports on ocean (10.10.8.108 ):
Not shown: 1991 closed ports
PORT     STATE         SERVICE
22/tcp   open          ssh
139/tcp  open          netbios-ssn
445/tcp  open          microsoft-ds
901/tcp  open          samba-swat
68/udp   open|filtered dhcpc
69/udp   open|filtered tftp
137/udp  open|filtered netbios-ns
138/udp  open|filtered netbios-dgm
5353/udp open|filtered zeroconf

Nmap done: 1 IP address (1 host up) scanned in 1.55 seconds


3. I modified smb.conf as per your comments and restarted smbd.

Even after these, still facing the same problem in windows.

---

### Post by Zorael on 2012-11-01
> **Morbius1 said:**
> Keep in mind that I don't use KDE so ....

The usual suspects:

Well, as far as I understand the problem was to get W7 to resolve the hostname when expressed as **\\hostname**? While a normal ping resolve worked.

From the linux machine do you really need nmbd for this? I mean, for me it's enough to just have [**libnss-winbind**](apt://libnss-winbind) installed and **/etc/nsswitch.conf** set up to resolve netbios names. Admittedly that package does pull [**winbind**](apt://winbind) and [**samba**](apt://samba) installs nmbd, but I disable them from starting.
```
$ grep '*wins*' /etc/nsswitch.conf 
hosts:          files mdns4_minimal [NOTFOUND=return] **wins** dns mdns4

$ ps aux | grep '*winbind\|nmbd\|avah*i' | grep -v '*grep*'
*# no output*

$ grep '*resolve order*' /etc/samba/smb.conf 
;   name resolve order = lmhosts host wins bcast
*# commented*

$ ping -c1 **g0game**
PING **g0game** (*10.0.0.25*) 56(84) bytes of data.
64 bytes from *10.0.0.25*: icmp_req=1 ttl=128 time=1.21 ms
*# truncated*

$ grep -c '***g0game***' /etc/hosts
0

$ smbclient -L **g0game**
Enter zorael's password: 
Domain=[G0GAME] OS=[Windows 7 Home] Server=[Windows 7 Home]

        Sharename       Type      Comment
        ---------       ----      -------
        D               Disk      
        pleiades        Disk      
        pub             Disk      
*# truncated*
```


**@hari_pk**;
You could try to add a static '*10.10.8.108 ocean*' line to ***%SystemRoot%*\system32\drivers\etc\hosts**, but if the ip ever changes you'd have to update it to point to the new one.

---

### Post by Morbius1 on 2012-11-01
>  3. I modified smb.conf as per your comments and restarted smbd.You need to start both:
sudo service smbd restart
sudo service nmbd restart

Then wait a few minutes. Everyone on the lan goes through a musical chairs process when the samba services are restarted for you have to wait until things settle down.

> Well, as far as I understand the problem was to get W7 to resolve the hostname when expressed as **\\hostname**? While a normal ping resolve worked.

From the linux machine do you really need nmbd for this?By default nmbd has to be running for anyone to see the Linux machine. The default name - to - ip - address mechanism is:
> name resolve order = lmhosts wins host bcastlmhosts doesn't exist and the host file isn't set up by default for Samba so they are ignored. wins is a WINS server which also doesn't exist by default and if there were one this particular smb.conf isn't specifying it so it's also ignored. That leaves bcast which Windows also uses ( broadcast ). Without nmbd on the Linux server no name is being broadcast so there is nothing for the client to see. Since bcast is the only working default mechanism in Linux one should place it first because the wins option gets in the way and can stall the name resolve process. Some folks actually remove the wins parameter entirely. 

As far a winbind is concerned I'm a veteran of 2 winbind wars and I thought the winbind thing was dead and buried. I'm not going to go through this again because life's too short. If you want to use it that's fine by me but if you have a slow internet connection ( as I do ) it will just slow things down ( [http://ubuntuforums.org/showthread.php?t=1496488](http://ubuntuforums.org/showthread.php?t=1496488) ).

On my network I do not have Active Directory set up so there is no place for winbind. As a side observation I can also not ping by hostname ( unless I use avahi - i.e., hostname.local ) although pinging by hostname and browsing by netbios name are 2 different things. But that does not prohibit anyone ( Windows, OSX, and Linux ) from seeing this server since bcast takes care of this for me. 

There is one thing that can defeat bcast however and that is it cannot transcend subnets. So the next set of questions are:

** Are all the machines on this network connected to and receiving ip addresses from the same router?

** And what is the output of the following command:
```
smbtree
```It should list the Linux server in the output. If the Linux samba client ( smbtree ) can't see the Linux samba server on the same machine then Windows won't either.

---

### Post by reptilezone2002 on 2012-11-01
did u try adding your samba servers host name to /etc/hosts file

---

### Post by Zorael on 2012-11-04
> **Morbius1 said:**
> By default nmbd has to be running for anyone to see the Linux machine. [...]
Very informative, cheers!

---

### Post by hari_pk on 2012-11-05
> **reptilezone2002 said:**
> did u try adding your samba servers host name to /etc/hosts file

Hi,
Yes, my hosts file looks like this:
hari@ocean:~$ cat /etc/hosts
127.0.0.1       localhost
#127.0.1.1      ocean
10.10.8.108     ocean

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by hari_pk on 2012-11-05
Hi Morbius1,
1. I restarted both smbd and nmbd.
2. "smbtree" doesnt show anything as output

---

### Post by Morbius1 on 2012-11-05
Please post the output of the following command:
```
testparm -sv | grep "name resolve order"
```

---

### Post by hari_pk on 2012-11-05
> **Morbius1 said:**
> Please post the output of the following command:
```
testparm -sv | grep "name resolve order"
```

Hi,
Here it is:
hari@ocean:~$ testparm -sv | grep "name resolve order"
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[hari]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
        name resolve order = bcast host lmhosts wins

---

### Post by Morbius1 on 2012-11-05
Well, after 6 days of this I think it's time you pack it in. You have bigger problems:
>  2. "smbtree" doesnt show anything as outputYou Linux box can't even see itself on the network.

Run the following command and see if your file manager brings up your Linux box:
```
dolphin smb://ocean.local
```If it doesn't then make sure avahi is running:
```
sudo service avahi-daemon restart
```And try it again.

** If you happen to have either iTunes or Safari installed on your Windows box you can access ocean the same way: \\ocean.local

** If you don't have either of those installed you can install bonjour for Windows: [http://support.apple.com/kb/DL999](http://support.apple.com/kb/DL999)

And if that doesn't work, you don't want to install anything on your Windows box, or avahi is also broken on your Linux install then make your ip address on your Linux box static and get used to accessing it by ip address.

---

### Post by hari_pk on 2012-11-06
> **Morbius1 said:**
> Well, after 6 days of this I think it's time you pack it in. You have bigger problems:
You Linux box can't even see itself on the network.

Run the following command and see if your file manager brings up your Linux box:
```
dolphin smb://ocean.local
```If it doesn't then make sure avahi is running:
```
sudo service avahi-daemon restart
```And try it again.

** If you happen to have either iTunes or Safari installed on your Windows box you can access ocean the same way: \\ocean.local

** If you don't have either of those installed you can install bonjour for Windows: [http://support.apple.com/kb/DL999](http://support.apple.com/kb/DL999)

And if that doesn't work, you don't want to install anything on your Windows box, or avahi is also broken on your Linux install then make your ip address on your Linux box static and get used to accessing it by ip address.


Hi Morbius1,
A quick update, I re-installed samba and now smbtree shows all servers in my office backbone. Even now, am facing the same problem. \\10.10.8.108 works but \\ocean fails in windows.

---

### Post by SeijiSensei on 2012-11-06
If you only need to access the server from a couple of Windows machines, just add entries to their "hosts" files.  See [this](http://en.wikipedia.org/wiki/Hosts_%28file%29) to determine where the file is stored in your version(s) of Windows.

If you need to support a large number clients, it's probably time to consider adding a DNS server to your network.  However, if you are using your router to handle DNS, it's often possible to add static entries to its tables.  Browse around in the router configuration and see.

---

### Post by hari_pk on 2012-11-06
> **SeijiSensei said:**
> If you only need to access the server from a couple of Windows machines, just add entries to their "hosts" files.  See [this](http://en.wikipedia.org/wiki/Hosts_%28file%29) to determine where the file is stored in your version(s) of Windows.

If you need to support a large number clients, it's probably time to consider adding a DNS server to your network.  However, if you are using your router to handle DNS, it's often possible to add static entries to its tables.  Browse around in the router configuration and see.

Hi,
I have done this also but still its not working

---

### Post by hari_pk on 2012-11-06
Hi,
I checked "dolphin smb://ocean.local" in the linux machine and its working fine. able to access my samba share folders

---

### Post by hari_pk on 2012-11-16
Hi,
I was able to temporarily resolve this issue by running the command "net use \\ocean /user:hari" and give my samba share password when prompted. After this, \\ocean in Run command worked. However, I have to give this command each and every time I reboot the machine

---

### Post by tombert on 2013-07-16
Hi, I know it's an old post but I wanted to tell you that I have the exact same problem. When the hostname is in the systems32/drivers/etc/hosts then the network drive mapping in W7 does not work. It only works when using the IP or when the hostname is resolved via DNS.
This is an old Windows problem.

---

