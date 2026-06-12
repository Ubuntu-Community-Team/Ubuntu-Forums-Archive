---
title: "samba shares not showing up in XP Pro"
date: 2009-12-29
forum: Networking &amp; Wireless
---

### Post by maestrobwh1 on 2009-12-29
Shares show up in clients running Ubuntu/kubuntu/knoppix under "workgroup" when browsing in dolphin/konqueror/nautilus (smb://eee-box/MUSIC) for example where eee-box is the host name and 'MUSIC' would be the shared folder on the host.

Using Windows XP Pro clients, I only see the client machine itself under "workgroup"

I am not sure if I need to configure something on the host end or client end to get a client XP machine to browse shares.  I am not looking to "hard" mount a share if I can work around that.

Here is the smb.conf of the host machine.
```

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = WORKGROUP                                                       
Netbios name = eee-box                                                      
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

# added to speed up samba
read size = 1024         
socket options = TCP_NODELAY SO_KEEPALIVE SO_RCVBUF=2048 SO_SNDBUF=2048 IPTOS_LOWDELAY
getwd cache = yes                                                                     


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
# *security = user *  << Later posts here have this changed to 
**security = share**                                                   

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
create mask = 0700     

# Windows clients look for this share name as a source of downloadable
# printer drivers                                                     
[print$]                                                              
comment = Printer Drivers
path = /var/lib/samba/printers

# [NETLOGON]
# path = /var/lib/samba/netlogon
# guest ok = yes
# writable = no
# share modes = no

[MUSIC]
path = /media/30GB_SSD/Music/
guest ok = yes
read only = no

[SHARED]
path = /media/30GB_SSD/Shared/
guest ok = yes
read only = no

[TOMSNETFOLDE]
path = /media/30GB_SSD/TomsNetFolder/
guest ok = yes
read only = no

[CHRISTMAS_MU]
path = /media/My Book/Christmas_Music/
guest ok = yes
read only = no

[PICTURES]
path = /media/My Book/Pictures/
guest ok = yes
read only = no

[TOM'S_DOCUME]
path = /media/My Book/Tom's_Documents/
guest ok = yes
read only = no

[VIDEO]
path = /media/My Book/Video/
guest ok = yes
read only = no

[PUBLIC]
path = /home/brian/Public/
guest ok = yes
read only = no

```

---

### Post by dmizer on 2009-12-29
Change this line:
```
# security = user 
```
to this:
```
security = share
```
Reboot the machine or restart samba with the following command:
```
sudo /etc/init.d/samba restart
```

---

### Post by maestrobwh1 on 2009-12-30
I still am unable to see the "eee-box" host.  In XP, I only see the client machine "pc701" in 

Network Places > Microsoft Windows Network > Workgroup >

Odd.

I just tinkered a bit more with the XP box, making sure that the wizard is set up to be part of "workgroup"  It is.

I do see the "pc701" client in the smb://workgroup folder in dolphin, but when I click it, I DO not see the client's shared folders and the firewall is temporarily off.  I don't get an error when I enter that folder either.

I do not use XP very often.  If I boot another windows box, I do see shared folders between XP boxes so I am assuming it is still something in the smb.conf file.

---

### Post by Morbius1 on 2009-12-30
Could try a couple of tests on the XP box:

1 - temporarily turn off the firewall on WinXP to see if somehow it's getting in the way.

2 - This is more to see if any errors are generated:

On WinXP:

Open **Command Prompt** ( not the run command )
Type **net view**

Post the errors if there are any.

---

### Post by maestrobwh1 on 2009-12-30
I figured it out from this guide:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch12_:_Samba_Security_and_Troubleshooting) 

About 3/4 down the page, I needed to:

    * Click on the Network Connections icon in the Windows Control Panel.
    * Right-click on the network connection, and select Properties.
    * Click on the Internet Properties (TCP/IP) menu option and then click on the Properties button.
    * Click on the Advanced button and then on the WINS tab. 

I then added my host ip of 192.168.15.100 and then marked "Enable NetBIOS over TCP/IP"

I then went to the shell prompt and entered

C:\>net view \\eee-box 

and could see my shares.

They then ended up showing in Windows Explorer.

When I went back to recheck those steps, everything was back to the defaults?  I will post back if it does not take a reboot.

[EDIT]

I also had to do the other listed thing.  I opened C:\WINDOWS\system32\drivers\etc\hosts 

in notepad and added at the end of the file:

```
192.168.15.100   Eee-box
```

Where I PURPOSEFULLY capitalized the first letter, as that is what showed up in XP in the shell prompt.  I doubt if it matters, but since it was communicating with Linux which IS case sensitive, I figured it might be helpful.  

I also succeeded in finding my host printer after all of this:-)

Marking this solved and I hope any others who run into the same issue find this.

---

### Post by jamesisin on 2009-12-30
Excellent news.  Let us know.

---

