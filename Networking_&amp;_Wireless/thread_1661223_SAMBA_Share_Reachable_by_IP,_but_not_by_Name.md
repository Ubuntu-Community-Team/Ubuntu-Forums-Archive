---
title: "SAMBA Share Reachable by IP, but not by Name"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by mateo305ci on 2011-01-06
I've been struggling to configure my Samba server.  As of right now, I can access the share manually on a Windows machine by manually entering the IP of my server (e.g. \\192.168.84.250).  I cannot see my share on the Windows network, and cannot access it by manually typing the name of the share (e.g. \\whirlwind-samba).  I'm posting my smb.conf file...any solutions?

Thanks in advance!

> 
[global]
netbios name = whirlwind-server
server string = Samba file and print server
workgroup = MSHOME
security = share
hosts allow = 127. 192.168.84.
interfaces = 127.0.0.1/8 192.168.84.250/24
bind interfaces only = yes
remote announce = 192.168.84.255
remote browse sync = 192.168.84.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = true
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = yes
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = yes
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = yes
printable = no
share modes = yes
locking = no

[movies]
comment = Movies
path = /media/DATAWIN/WWSERVE/xampp/htdocs/WWSHARE1/public/Movies
read only = no
available = yes
browseable = yes
writeable = yes
guest ok = yes
public = yes
printable = no
share modes = yes
locking = no

[music]
comment = Music
path = /media/DATAWIN/WWSERVE/xampp/htdocs/WWSHARE1/public/Music
read only = no
available = yes
browseable = yes
writeable = yes
guest ok = yes
public = yes
printable = no
share modes = yes
locking = no

[programs]
comment = Programs
path = /media/DATAWIN/WWSERVE/xampp/htdocs/WWSHARE1/public/Programs
read only = no
available = yes
browseable = yes
writeable = yes
guest ok = yes
public = yes
printable = no
share modes = yes
locking = no

[tv]
comment =TV
path = /media/DATAWIN/WWSERVE/xampp/htdocs/WWSHARE1/public/TV
read only = no
available = yes
browseable = yes
writeable = yes
guest ok = yes
public = yes
printable = no
share modes = yes
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = no
browseable = no
writable = yes
guest ok = no
public = no
printable = no
share modes = yes
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = yes
public = no
printable = yes
share modes = yes
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = no
browseable = no
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = no
guest ok = no
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =


---

### Post by endotherm on 2011-01-06
I see a couple odd things in your config, but in terms of naming, I notice that you have enabled a wins server in your samba config. have the windows clients been configured to use the wins server on your samba box? 
I also notice that your server is not set to any level of browse master. 

also I've never seen 'Host Lookup = no' in a smb.conf, but it does seem to have some relevance to the topic at hand. 

check out this tutorial on browsable samba config. shoudl help solve several issues for you:
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

---

### Post by mateo305ci on 2011-01-06
Yes, my Windows machines are set to look at the Samba server for WINS.

---

### Post by endotherm on 2011-01-06
on the windows machine, what output do you get from 
```
nbtstat -n
```

and on the server, what do you get from 
```
smbtree
```

---

### Post by mateo305ci on 2011-01-06
Here are the results, respectively...

---

### Post by mateo305ci on 2011-01-06
I just finished reading the  tutorial on browsable samba config. I made a few changes to my smb.conf file, but still no progress..

---

### Post by endotherm on 2011-01-06
well, which box is the ubuntu one? Dell3000 appears to be a windows box, and matt-PC is vissible to both boxes (but does not have any shares). is that the issue, that you can see teh server root, but not the shares within it? that can happen with a fine samba config if the folders being shared do not allow access to the user accessing the share. I also notice that you have "Security=share". I always turn that to "Security=user" so that I can specify what users may perform what actions on the share.

---

### Post by mateo305ci on 2011-01-06
DELL3000 & Matt-PC are both Windows boxes.  The issue is that the netBios name is not appearing in this network, but the shares are accessible via IP.

---

### Post by mateo305ci on 2011-01-06
I just solved my own problem...

The netBios name in my smb.conf file, "WHIRLWIND-SERVER" was 16-digits, and netbios only recognizes up to 15-digits.

I changed the netbios name to "SMBSERVER" and it showed right up on my Windows boxes.  I can't believe I overlooked that.

---

### Post by endotherm on 2011-01-07
> **mateo305ci said:**
> I just solved my own problem...

The netBios name in my smb.conf file, "WHIRLWIND-SERVER" was 16-digits, and netbios only recognizes up to 15-digits.

I changed the netbios name to "SMBSERVER" and it showed right up on my Windows boxes.  I can't believe I overlooked that.
I noticed that myself, but i was under the impression that that limitation was no longer in place. glad you got it working.

---

