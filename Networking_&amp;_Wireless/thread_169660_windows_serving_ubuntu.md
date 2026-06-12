---
title: "windows serving ubuntu"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by dmizer on 2006-05-03
probably my weakest point in computers is networking, and i'm simply confused.

i have a windows machine hosting a shared folder full of mp3's.  i have a laptop i would like to play these from remote without loading them onto my computer.

now i can use nautilus to surf the windows shares with no problem.  and i can load them onto the ubuntu laptop no problem.  but as i understand it, the nautilus file sharing doesn't play with windows right, so i am unable to play the mp3's from the windows share.

i have installed samba and smbfs and i have looked at the samba wiki, but i have been unable to mount the shares with samba.  i have tried smbmount as well as "sudo mount -t smbfs -o username ..." and only get connection to MSHOME failed.

please help me figure this out.

---

### Post by Beard on 2006-05-03
i am having the same trouble

---

### Post by dmizer on 2006-05-04
here's what i get every time:
```
$ smbmount //sentra/nx2000 /home/dmizer/smb
10462: Connection to sentra failed
SMB connection failed
```
same here:
```
$ sudo mount -t smbfs //sentra/nx2000 /home/dmizer/smb
10517: Connection to sentra failed
SMB connection failed
```
what is wrong?  if i connect to the sentra server with nautilus, it works just fine.  i just can't play the mp3's saved on that computer.
here's my fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,unhide,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```
and my samba conf:
```
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME

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
;   security = user

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
   browseable = no

# By default, the home directories are exported read-only. Change next
# parameter to 'yes' if you want to be able to write to them.
   writable = no

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



[dmizer]
path = /home/dmizer/smb
available = yes
browseable = no
public = yes
writable = no
```

---

### Post by dmizer on 2006-05-04
also ... i am unable to view .jpg pictures.

if i double click to open the picture, i get the following error:
"Firefox does not know how to open this address, because the protocol (smb) isn't associated with any program."

the above occurs when i go to places > connect to server ... and then open the shared folder from the desktop.

---

### Post by Iowan on 2006-05-04
Something about the naming doesn't seem quite right - smbfs (or smbmount) may not know about **/home/dmizer/smb**.  To Samba, the share may be **/dmizer**.  

... but I've been wrong (many times) before.

---

### Post by afonit on 2006-05-04
I would suggest fuse and sshfs instead of samba

in synaptic install:
libfuse
sshfs
ssh

add the 'fuse' into
/etc/modules

system > admin > users and groups
create a group called 'fuse'
add yourself into that group

reboot

first test if you can ssh into your server

create a folder in your /media/ folder on linux, and make sure you the user has permissions to that folder

then do a 
sshfs usernameonserver@hostIP:/path/to/desired/folder(insert one space here)/media/whatyouwannacallit

now you have the server drive mapped to your /media/whatyouwannacallit folder

---

### Post by dmizer on 2006-05-04
[QUOTE=Iowan]Something about the naming doesn't seem quite right - smbfs (or smbmount) may not know about **/home/dmizer/smb**.  To Samba, the share may be **/dmizer**.  

... but I've been wrong (many times) before.[/QUOTE]
i think i remember trying that once before ... but i did it again just to be sure. it didn't work either.  different error though:
```
$ sudo smbmount //sentra/nx2000 /dmizer
Could not resolve mount point /dmizer
```
i'll try fuse next.

---

### Post by Iowan on 2006-05-04
How 'bout:
```
sudo mount -t smbfs //sentra/dmizer /home/dmizer/smb 
```
or
```
sudo smbmount //sentra/dmizer /home/dmizer/smb 
```
These presume the mount point /home/dmizer/smb already exists.
This also presumes that you're trying to share files from Samba server **sentra**.

---

### Post by dmizer on 2006-05-05
except there's no folder on sentra named dmizer, so //sentra/dmizer does not exist. :-k

and i know the server name is correct, because as i've said before, it mounts fine at places > connect to server ... when i list sentra as the server.

also note ... i have tried //SENTRA/NX2000 as well as //sentra/nx2000

i couldn't figure out how to get fuse to work.  i'll play with it some more later.

---

### Post by dmizer on 2006-05-05
okay ... i can ssh to my own machine just fine with no errors.

but with fuse, when i try to do the following:
```
sshfs dmizer@192.168.0.101:/nx2000 /media/sentra
```
it says no route to host.  192.168.0.101 is the ip for the machine hosting my shared files.

lol, now i have a folder on my desktop labled sentra and i can't unmount it.  i get an error that says:
Unable to unmount the selected volume.
Error: could not determine real path of the device: No such file or directory

---

### Post by neouser99 on 2006-05-05
try this
```
sudo mount -t smbfs -o username= //192.168.0.101/nx2000 /home/dmizer/smb
```

-neo

---

### Post by Iowan on 2006-05-05
Which machine has the files to be shared (name and IP)?
Which machine is trying to share the files (name and IP)?
Which machine has the Samba share [dmizer] with
path = /home/dmizer/smb ?

---

### Post by dmizer on 2006-05-05
[QUOTE=Iowan]Which machine has the files to be shared (name and IP)?
Which machine is trying to share the files (name and IP)?
Which machine has the Samba share [dmizer] with
path = /home/dmizer/smb ?[/QUOTE]
the machine with the files to be shared is windows.  ip is 192.168.0.101. name is nx2000.

my ubuntu laptop is trying to view the shared files.  ip is 192.168.0.103. name is dmizer.

my ubuntu laptop has samba installed with the path /home/dmizer/smb.  the smb/ folder is shared.

```
$ sudo mount -t smbfs -o username=administrator //192.168.0.101/nx2000 /home/dmizer/smb
Error connecting to 192.168.0.101 (No route to host)
9104: Connection to 192.168.0.101 failed
SMB connection failed
```

---

### Post by neouser99 on 2006-05-06
ok.. you don't need to tak on the nx2000 on the server location, should look like //192.168.0.101/dmizer <- (is the name that you specify when you start sharing that folder), that should be the share name that you want to connect to. second, humor me here, what does a ping 192.168.0.101 return? third, did you allow access on the windows firewall??

-neo

---

### Post by dmizer on 2006-05-06
first of all ... i sincerely appreciate you sticking with this.

the machine i am trying to connect to has no firewall as it is isolated.
i can ping just fine.
```
$ ping sentra
PING SENTRA.mshome.net (192.168.0.101) 56(84) bytes of data.
64 bytes from SENTRA.mshome.net (192.168.0.101): icmp_seq=1 ttl=128 time=3.58 ms
64 bytes from SENTRA.mshome.net (192.168.0.101): icmp_seq=2 ttl=128 time=2.67 ms
64 bytes from SENTRA.mshome.net (192.168.0.101): icmp_seq=3 ttl=128 time=2.66 ms
64 bytes from SENTRA.mshome.net (192.168.0.101): icmp_seq=4 ttl=128 time=3.65 ms
```
```
$ ping 192.168.0.101
PING 192.168.0.101 (192.168.0.101) 56(84) bytes of data.
64 bytes from 192.168.0.101: icmp_seq=1 ttl=128 time=2.76 ms
64 bytes from 192.168.0.101: icmp_seq=2 ttl=128 time=2.64 ms
64 bytes from 192.168.0.101: icmp_seq=3 ttl=128 time=2.83 ms
64 bytes from 192.168.0.101: icmp_seq=4 ttl=128 time=2.66 ms
64 bytes from 192.168.0.101: icmp_seq=5 ttl=128 time=2.65 ms
```
i tried the //102.168.0.101/dmizer but only got the following:
```
$ sudo mount -t smbfs -o username=administrator //192.168.0.101/dmizer /home/dmizer/smb
Password:
15808: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed
```
i am assuming that the password it asks for is the password for the share not for root access.  although i get the same results if i type in the share password or my root password.

edit to add: it's probably noteworthy at this point to indicate that my windows machine can't see my ubuntu laptop.

---

### Post by neouser99 on 2006-05-06
the first password will be for the sudo, depending on how long ago you last ran sudo or how it is setup. as for the error, it speaks for itself. samba is working, but you are trying to connect to a share that doesn't exist on the destination machine. when you set the share up on windows, it will ask for what you want to name it... default, share, something like that. usually it defaults to the name of the folder i think.

for instance, this is the windows box @ 192.168.0.101 with a share
C:\share and its name is "Share", here is the samba command
```
sudo mount -t smbfs -o username= //192.168.0.101/Share /home/path/to/dir
```

-neo

---

### Post by dmizer on 2006-05-06
[QUOTE=neouser99]samba is working, but you are trying to connect to a share that doesn't exist on the destination machine. when you set the share up on windows, it will ask for what you want to name it... default, share, something like that. usually it defaults to the name of the folder i think.

-neo[/QUOTE]
thank you.:KS :KS 

that's the part i was missing.  the folder name on the shared machine ... i knew it was something stupid simple.

---

### Post by neouser99 on 2006-05-06
no prob... let us know if there is anything else.

-neo

---

