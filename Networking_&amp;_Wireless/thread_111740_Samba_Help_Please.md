---
title: "Samba Help Please"
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by Pretzal on 2006-01-02
I've managed to install samba ok and am trying to get 2 computers to talk to each other. The desktop is running Ubuntu and the Laptop is running XP. They are connected through a Dlink wireless ADSL Router (G604T) (10.1.1.1). They can happily share an internet connection but cant talk to each other. I have followed arnieboy's Samba how to but still cant get it to work. I can ping the laptop (10.1.1.3) from the desktop (10.1.1.2). The error I am getting at this stage is:

glasson@Ubuntu:~$ sudo mount -t smbfs -o username=glasson,password=*****,uid=`whoami`,gid=` whoami`,fmask=000,dmask=000 //ubuntu_samba_server/glasson /home/`whoami`/Network
9368: Connection to ubuntu_samba_server failed
SMB connection failed


Have attached a testparm in case that helps:

glasson@Ubuntu:~$ sudo testparm
Password:
Load smb config files from /etc/samba/smb.conf
Processing section "[homes]"
Processing section "[printers]"
Processing section "[print$]"
Processing section "[UbuntuHomeFolder]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

# Global parameters
[global]
workgroup = HOME
netbios name = UBUNTU_SAMBA_SERVER
server string = %h server (Samba, Ubuntu)
obey pam restrictions = Yes
passdb backend = tdbsam, guest
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
username map = /etc/samba/smbusers
syslog = 0
log file = /var/log/samba/log.%m
max log size = 1000
dns proxy = No
panic action = /usr/share/samba/panic-action %d
invalid users = root

[homes]
comment = Home Directories
read only = No
create mask = 0700
directory mask = 0700

[printers]
comment = All Printers
path = /tmp
create mask = 0700
printable = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers

[UbuntuHomeFolder]
path = /home
read only = No
guest ok = Yes
glasson@Ubuntu:~$

Any help greatly appreciated...

---

### Post by Pretzal on 2006-01-04
any ideas anyone?

---

### Post by JanvL on 2006-01-08
You must not forget to add users to the Samba password database.
Use:

/usr/bin/smbpasswd -a yourwindowsuser
password (enter your windowsuserspassword)

Hope this will help

Jan

---

### Post by Pretzal on 2006-01-09
Ok I have added a user to the samba password database, which is the same user I have for Ubuntu. That seemed to go OK. 

In addition to this I have added '10.1.1.3' to the etc/hosts file (which is the Laptop with windows XP) and the situation is:

1. the Ubuntu desktop can ping the laptop
2. the XP laptop cannot see the Ubuntu desktop
3. The Ubuntu desktop can see the Laptops files through firefox 'smb://10.1.1.3'
4. The laptop cannot see Ubuntu through [http://10.1.1.2](http://10.1.1.2) in Firefox (operation times out)
5. The Laptop XP can share files with the Windows XP Desktop (dual booted with Ubuntu).

Now I am trying to get access to the laptop via nautilus. When I open up Nautilus and try and browse the network I get windows Network but nothing in it. I would also like access to Ubuntu via the XP laptop too.

Can anyone help?

---

### Post by harisund on 2006-01-10
Hmm.. seems like we have a tough case on our hands.. 

1. First up, ensure all of samba smbfs and its dependancies are installed on the UBuntu machine (10.1.1.2)
2. What version of Windows XP (on 10.1.1.3) are you running? Home could be a pain. In any case, make sure you have turned on networking and enabled File sharing. I am assuming you know how to, besides, this is a Ubuntu forum. I could explain file sharing in Windows XP through email if you want. 
3. Set a workgroup name for your Windows machine.Use the same workgroup in your smb conf file. 
4. Do sudo smbpasswd -a <some user in your Ubuntu machine>  and enter a password for it. 
5. Finally you might want to reboot your Windows machine. Of course, Linux machines needn't be rebooted, all you need to do is sudo /etc/init.d/samba restart. 
6. From Windows if you need to see the Linux machine, go to Network Neighborhood and choose to see all workgroup machines. You can see the Linux machine. Open it, and when prompted for password, enter the Ubuntu username and password you used with the smbpasswd command. 
7. From Linux if you need to see the Windows machine, things might get a bit tough. You will need to type smb://10.1.1.3/name-of-the-shared-folder-in-Windows. You will need to share folders in Windows. Again, I am assuming you know to do that (that is what I said earlier.) 

Hope it is clear.. accessing linux partition from windows is easier than vice versa..

---

### Post by harisund on 2006-01-10
[QUOTE=Pretzal]4. The laptop cannot see Ubuntu through [http://10.1.1.2](http://10.1.1.2) in Firefox (operation times out)
[/QUOTE]

You can not use http:// because you might not have a http server running

---

### Post by Pretzal on 2006-01-10
[QUOTE=harisund]Hmm.. seems like we have a tough case on our hands.. 

1. First up, ensure all of samba smbfs and its dependancies are installed on the UBuntu machine (10.1.1.2)
2. What version of Windows XP (on 10.1.1.3) are you running? Home could be a pain. In any case, make sure you have turned on networking and enabled File sharing. I am assuming you know how to, besides, this is a Ubuntu forum. I could explain file sharing in Windows XP through email if you want. 
3. Set a workgroup name for your Windows machine.Use the same workgroup in your smb conf file. 
4. Do sudo smbpasswd -a <some user in your Ubuntu machine>  and enter a password for it. 
5. Finally you might want to reboot your Windows machine. Of course, Linux machines needn't be rebooted, all you need to do is sudo /etc/init.d/samba restart. 
6. From Windows if you need to see the Linux machine, go to Network Neighborhood and choose to see all workgroup machines. You can see the Linux machine. Open it, and when prompted for password, enter the Ubuntu username and password you used with the smbpasswd command. 
7. From Linux if you need to see the Windows machine, things might get a bit tough. You will need to type smb://10.1.1.3/name-of-the-shared-folder-in-Windows. You will need to share folders in Windows. Again, I am assuming you know to do that (that is what I said earlier.) 

Hope it is clear.. accessing linux partition from windows is easier than vice versa..[/QUOTE]


Before I start I have configured the ubuntu desktop to use static IP 10.1.2.1

1.On the Ubuntu desktop I have installed the following Samba components:
libsmbclient, samba, samba-common, smbclient and smbfs through synaptic

2. Both the desktop and Laptop are running XP Professional. I believe I have set it up for file sharing as both the XP desktop and XP Laptop can share files.

3. I have done this - I am using the HOME workgroup

4. Completed without a hitch

5. Done

6. Here lies a problem because I can navigate to the HOME workgroup but I can only see the Laptop. I cannot see the Ubuntu Desktop. I can ping the ubuntu desktop 10.1.2.1  from the laptop (10.1.1.2) but cannot see it. I do a search for computers on the network using a "*" search and nothing is returned. When I reboot the dektop in XP Pro I can share files ok.  ?????

7. If I open Nautilus or firefox and type smb://10.1.1.2 both display the C: from the laptop and the shared folder. I have access to everything in the shared folder and all but 'Program files' and 'Windows' folders from the C: Drive which I do not have permission to view the contents (which incidentally I would like). 

So I seem to have some success but not from the XP side of things. Thanks so much for your help so far :)

---

### Post by harisund on 2006-01-10
[QUOTE=Pretzal]
6. Here lies a problem because I can navigate to the HOME workgroup but I can only see the Laptop. I cannot see the Ubuntu Desktop. I can ping the ubuntu desktop 10.1.2.1  from the laptop (10.1.1.2) but cannot see it. I do a search for computers on the network using a "*" search and nothing is returned. When I reboot the dektop in XP Pro I can share files ok.  ?????

7. If I open Nautilus or firefox and type smb://10.1.1.2 both display the C: from the laptop and the shared folder. I have access to everything in the shared folder and all but 'Program files' and 'Windows' folders from the C: Drive which I do not have permission to view the contents (which incidentally I would like). 

[/QUOTE]

Hmm.. I am not able to understand why that is happening at all... really sorry .. 

How exactly do you "navigate to the HOME workgroup" ? Do you use the "My Network Places" and then the "View workgroup computers" ? 
make sure samba is correctly configured and running (to be on the safe side do a /etc/init.d/samba restart) But I am assuming you do have it running .. 
 
Ok.. one last resort.. they might have to be in the same subnet.. so do the following : 

do an ifconfig in the linux machine. On the second line you will see something like
inet addr: 10.1.2.1 Bcast: <something> Mask: <something> 
Note down what the mask is and BCast is. 

Then on the Windows machine look up internet properties, or on the command line (yes, Windows has one too! Albeit a nearly worthless one .. ) execute ipconfig
You will find: 
Connection specific DNS suffix: <something> 
IP address: 10.1.1.2
Subnet Mask: <something > 
Default Gateway:  <something> 

Now here is the deal, I am pretty sure the Subnet Masks (and consequently the Default Gateway) should be the same as the Mask value from Ubuntu's ifconfig. Could you please check that? I know I am not doing a great help by asking you to run more commands after commands, but I am pretty sure they need to be on the same subnet. 

The default gateway is not shown directly with the ifconfig in Ubuntu, but can be found out using other ways. However, if the subnet masks are the same and both can connect to the internet, that means they are likely to have the same gateway.

And to enable permission to c:\ I think you will need to right click on the C drive in Windows, choose the Sharing and security option, and choose to share the root drive and things should become obvious from then on ..

---

### Post by Pretzal on 2006-01-10
thanks once again Harisund

I typed in ifconfig and got:
pretzal@Ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:6B:E4:33:1A
          inet addr:10.1.2.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::209:6bff:fee4:331a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:11454660 (10.9 MiB)  TX bytes:3643834 (3.4 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8076777 (7.7 MiB)  TX bytes:8076777 (7.7 MiB)
 
and ipconfig in windows gave:

Connection specific DNS suffix: blank
IP address: 10.1.1.2
Subnet Mask: 255.0.0.0
Default Gateway: 10.1.1.1

I have also included the /etc/samba/smb.conf if this helps:
pretzal@Ubuntu:~$ cat /etc/samba/smb.conf
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
# "testparm" to check that you have not many any basic syntactic
# errors.
#

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = Home
  netbios name = ubuntu_samba_server

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


#### Debugging/Accounting ####

# This tells Samba to use a separate log file for each machine
# that connects
   log file = /var/log/samba/log.%m

# Put a capping on the size of the log files (in Kb).
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
# /usr/share/doc/samba-doc/htmldocs/ServerType.html in the samba-doc
# package for details.
   security = user
   username map = /etc/samba/smbusers
# You may wish to use password encryption.  See the section on
# 'encrypt passwords' in the smb.conf(5) manpage before enabling.
   encrypt passwords = true

# If you are using encrypted passwords, Samba will need to know what
# password database type you are using.
   passdb backend = tdbsam guest

   obey pam restrictions = yes

;   guest account = nobody
   invalid users = root

# This boolean parameter controls whether Samba attempts to sync the Unix
# password with the SMB password when the encrypted SMB password in the
# passdb is changed.
;   unix password sync = no

# For Unix password sync to work on a Debian GNU/Linux system, the following
# parameters must be set (thanks to Augustin Luton <aluton@hybrigenics.fr> for
# sending the correct chat script for the passwd program in Debian Potato).
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .

# This boolean controls whether PAM will be used for password changes
# when requested by an SMB client instead of the program listed in
# 'passwd program'. The default is 'no'.
;   pam password change = no


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

# When using [print$], root is implicitly a 'printer admin', but you can
# also give this right to other users to add drivers and set printer
# properties
;   printer admin = @ntadmin


######## File sharing ########

# Name mangling options
;   preserve case = yes
;   short preserve case = yes


############ Misc ############

# Using the following line enables you to customise your configuration
# on a per machine basis. The %m gets replaced with the netbios name
# of the machine that is connecting
;   include = /home/samba/etc/smb.conf.%m

# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
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

#======================= Share Definitions =======================

wins support = no
[homes]
   comment = Home Directories
   browseable = yes

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = yes

# File creation mask is set to 0700 for security reasons. If you want to
# create files with group=rw permissions, set next parameter to 0775.
   create mask = 0700

# Directory creation mask is set to 0700 for security reasons. If you want to
# create dirs. with group=rw permissions, set next parameter to 0775.
   directory mask = 0700

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
;   guest ok = yes
;   writable = no
;   share modes = no

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

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
;   writable = no
;   locking = no
;   path = /cdrom
;   public = yes

# The next two parameters show how to auto-mount a CD-ROM when the
#       cdrom share is accesed. For this to work /etc/fstab must contain
#       an entry like this:
#
#       /dev/scd0   /cdrom  iso9660 defaults,noauto,ro,user   0 0
#
# The CD-ROM gets unmounted automatically after the connection to the
#
# If you don't want to use auto-mounting/unmounting make sure the CD
#       is mounted on /cdrom
#
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom


[UbuntuHomeFolder]
path = /home
available = yes
browseable = yes
public = yes
writable = yes


Thanks once again Harisund

---

### Post by harisund on 2006-01-10
Everything seems identical as in my case with the exception of the following. So I suggest you make a backup copy of the smb.conf file and edit it according to these below, and restart samba and give it a shot. 

1. comment the 
```
netbios name = ubuntu_samba_server 
```
after the 
```
workgroup = Home
``` line. I think we need to deal with netbios names only if your machine is acting as a primary domain controller. 
2. Comment out the 2 lines
```

security = user
username map = /etc/samba/smbusers
```
3. comment out 
```
wins support = no
```
in the 
```
#======================= Share Definitions =======================
```
section. 

That way, you will get a .smb conf exactly similar to mine, and since mine works, yours might.. otherwise we will have to try something else..

---

### Post by Pretzal on 2006-01-10
Well I might be on the right track now. I've turned off firestarter firewall and can now see Ubuntu from the Laptop with XP. Unfortunately I can't access it yet as it says: "Ubuntu_samba_server is not accessible. You might not have persmission to access this network resource. Contact the administrator of this server to see if you have access permissions. Parameter is incorrect"

I'll keep trying to see if I can get this working....

---

### Post by Pretzal on 2006-01-11
Well it turns out that Firestarter was preventing the connection between XP and Ubuntu. Harisund - Apologies for making you go around the garden path on this one. Thanks all the same for the static IP help though. 

All I did to get it going was check the events tab to see the laptop 10.1.1.3 trying to get through, so I just right clicked and allowed connection from source on all the different attempts and now it works. I have also configured the laptop to use a static IP of 10.1.1.3 so that I wont have to enable all the different IP's that the router might assign.

Hope this might help anyone who's been banging their head against the wall like me.

---

### Post by s_p_a_r_k_y on 2006-01-11
people lets use nmap in the future to do real port scanning to see if other machines can knock on our open ports. Boot Windows machines with knoppix to do the scan of ubuntu machines or find a free windows port scanner. Firewall issues are tricky tricky to resolve especially when everything is setup correctly and "should" be working. Dunno how many hours I've spent fiddling with DNS server, just to learn that someone turned off UDP on the firewall for that port.

---

