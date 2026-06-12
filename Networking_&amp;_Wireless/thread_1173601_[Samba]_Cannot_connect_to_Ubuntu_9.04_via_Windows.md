---
title: "[Samba] Cannot connect to Ubuntu 9.04 via Windows"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by irishbluto on 2009-05-29
I have been trying to setup samba on my Ubuntu 9.04 machine to share files over my network with a couple of Windows XP machines.  This setup was working in Ubuntu 8.10, however, I reformatted my system before upgrading to 9.04 and can no longer get Samba to work.  All of my windows machines can see the Samba server in My Network Places --> View workgroup computers, but get the following error when attempting to connect:

\\Ubuntu is not accessible.  You might not have permission to use this network resource...

I have spent hours looking to find an answer, and have gone through many a website and Ubuntu Forum to find the answer.  Here is my smb.conf, and testparm output.  Any help would be greatly appreciated.  A few notes:  My home network is named HOMENET.  I can see the shared directories on this machine when I go to Places --> Network --> Windows Network --> HOMENET --> Ubuntu (same system, only have 1 Ubuntu machine).  I can also connect to each XP machine from each other.

smb.conf:
#======================= Global Settings =======================

[global]

## Browsing/Identification ###
   workgroup = HOMENET
   netbios name = UBUNTU
   server string = %h server (Samba, Ubuntu)

wins support = yes
;   wins server = w.x.y.z

   dns proxy = no
;   name resolve order = lmhosts host wins bcast

#### Networking ####

;   interfaces = lo wlan0
;   bind interfaces only = yes

#### Debugging/Accounting ####

   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0

# Do something sensible when Samba crashes: mail the admin a backtrace
   panic action = /usr/share/samba/panic-action %d


####### Authentication #######

security = share
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user

########## Domains ###########

;   domain logons = yes
;   logon path = \\%N\profiles\%U
;   logon drive = H:
;   logon script = logon.cmd
; add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
; add machine script  = /usr/sbin/useradd -g machines -c "%u machine account" -d /var/lib/samba -s /bin/false %u
; add group script = /usr/sbin/addgroup --force-badname %g


############ Misc ############

;   include = /home/samba/etc/smb.conf.%m
;   message command = /bin/sh -c '/usr/bin/linpopup "%f" "%m" %s; rm %s' &
;   idmap uid = 10000-20000
;   idmap gid = 10000-20000
;   template shell = /bin/bash
;   winbind enum groups = yes
;   winbind enum users = yes

usershare owner only = false
usershare allow guests = yes

;   usershare max shares = 100

  

#======================= Share Definitions =======================
;   comment = Home Directories
browseable = yes
;   read only = yes
;   create mask = 0700
;   directory mask = 0700
;   valid users = %S
;[netlogon]
;   comment = Network Logon Service
;   path = /home/samba/netlogon
   guest ok = yes
;   read only = yes
;   share modes = no
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

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no

# A sample share for sharing your CD-ROM with others.
;[cdrom]
;   comment = Samba server's CD-ROM
;   read only = yes
;   locking = no
;   path = /cdrom
;   guest ok = yes
;   preexec = /bin/mount /cdrom
;   postexec = /bin/umount /cdrom

[My Documents]
path = /home/ubuntuuser/My Documents
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes

TESTPARM:
Load smb config files from /etc/samba/smb.conf
Processing section "[downloads]"
Processing section "[My Documents]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = HOMENET
	netbios name = UBUNTU
	security = SHARE
	auth methods = guest
	domain master = No
	wins support = Yes

[downloads]
	comment = mi home
	path = /home/downloads
	read only = No
	guest ok = Yes

[My Documents]
	path = /home/irishbluto/My Documents
	read only = No
	guest ok = Yes

Thanks Again

---

### Post by superprash2003 on 2009-05-30
are you able to ping the ubuntu machine from windows.. try \\x.x.x.x where x.x.x.x is the ip of the ubuntu machine

---

### Post by dmizer on 2009-05-30
Lots of problems ... I may miss some.

At the top of smb.conf, remove "wins support = yes" It doesn't do what you think it does. Refer to man smb.conf for more information on why.

Remove the ";" from in front of this line:
```
; name resolve order = lmhosts host wins bcast
```

You have a space in your path here:
```
[[COLOR="Red"]My Documents[/COLOR]]
path = /home/irishbluto/[COLOR="Red"]My Documents[/COLOR]
read only = No
guest ok = Yes
```
Both of those could cause problems. Either rename the share and path to something without a space, or put quotes around the path like so:
```
[My-Documents]
path = /home/irishbluto/"My Documents"
read only = No
guest ok = Yes
```

That's all I could find quickly.

---

### Post by irishbluto on 2009-05-30
Thanks for the comments.  To answer the question, I can ping the Ubuntu machine from XP.  I have removed the line:

wins support = yes

And uncommented the line:

name resolve order = lmhosts host wins bcast

And placed quotes around "My Documents", however, still cannot connect to the Ubuntu machine.

---

### Post by superprash2003 on 2009-05-30
did you try accessing via ip.. did you restart samba after making changes

sudo /etc/init.d/samba restart

---

### Post by irishbluto on 2009-05-30
I have run sudo /etc/init.d/samba restart after every edit of smb.conf.  Also, I am unable to access the machine via //ipaddress, get the same 'Ubuntu is not accessible' error as when I go through My Network Places --> View workgroup computers --> Ubuntu

---

### Post by roman_platonov on 2009-05-30
the better way to enable correct acces from XP set:
security = user
create. and enable guiest account
or set
allow guest = true;

for required share.

i'm have the same problem problem with XP sometime (i don't now why). xp try to make full authentication and.

---

### Post by dmizer on 2009-05-30
Please post the output of:
```
sudo iptables -L
```

---

### Post by irishbluto on 2009-05-30
Here is the output from sudo iptables -L:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
RH-Lokkit-0-50-INPUT  all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
RH-Lokkit-0-50-INPUT  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain RH-Lokkit-0-50-INPUT (2 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:60006 flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ssh flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:telnet flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:ftp flags:FIN,SYN,RST,ACK/SYN 
ACCEPT     udp  --  anywhere             anywhere            udp spts:bootps:bootpc dpts:bootps:bootpc 
ACCEPT     udp  --  anywhere             anywhere            udp spts:bootps:bootpc dpts:bootps:bootpc 
ACCEPT     all  --  anywhere             anywhere            
REJECT     tcp  --  anywhere             anywhere            tcp dpts:0:1023 flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:nfs flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp dpts:0:1023 reject-with icmp-port-unreachable 
REJECT     udp  --  anywhere             anywhere            udp dpt:nfs reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpts:x11:6009 flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable 
REJECT     tcp  --  anywhere             anywhere            tcp dpt:font-service flags:FIN,SYN,RST,ACK/SYN reject-with icmp-port-unreachable

---

### Post by dmizer on 2009-05-30
Is there some reason you've configured your firewall as above? It's blocking access to your Samba. You'll either have to add rules to allow the following ports, or you'll have to disable the firewall:

Port 135/TCP - used by smbd
Port 137/UDP - used by nmbd
Port 138/UDP - used by nmbd
Port 139/TCP - used by smbd
Port 445/TCP - used by smbd

---

### Post by irishbluto on 2009-05-31
I have tried to open these ports, however unsuccessfully.  What is the command to open these ports?  I have tried the following:

sudo iptables -A INPUT -p tcp --destination-port 135 -j ACCEPT
sudo iptables -A INPUT -p udp --destination-port 137 -j ACCEPT
sudo iptables -A INPUT -p udp --destination-port 138 -j ACCEPT
sudo iptables -A INPUT -p tcp --destination-port 139 -j ACCEPT
sudo iptables -A INPUT -p tcp --destination-port 445 -j ACCEPT

However, when I check I receive the following:

sudo nc -z -v 127.0.0.1 135
localhost [127.0.0.1] 135 (loc-srv) : Connection refused

sudo nc -z -v 127.0.0.1 137
localhost [127.0.0.1] 137 (netbios-ns) : Connection refused

sudo nc -z -v 127.0.0.1 138
localhost [127.0.0.1] 138 (netbios-dgm) : Connection refused

sudo nc -z -v 127.0.0.1 139
localhost [127.0.0.1] 139 (netbios-ssn) open

sudo nc -z -v 127.0.0.1 445
localhost [127.0.0.1] 445 (microsoft-ds) open

I'm not quite sure where I've gone wrong on ports 135, 137 and 138.

Thanks for your help

---

### Post by irishbluto on 2009-05-31
I should note that if I disable the firewall:

sudo iptables -F

I can connect to the Ubuntu machine.  This is progress, at least I know it is a firewall problem.

---

### Post by dmizer on 2009-05-31
Again, is there some particular reason you've configured your firewall as above, do you actually need the firewall?

If you're behind a router, the router has a built in firewall so a local firewall on your Ubuntu computer isn't really necessary in most situations.

---

### Post by superprash2003 on 2009-06-01
you could always flush your iptables.. its probably screwed up , or maybe firestarter or ufw is overwriting it..

---

