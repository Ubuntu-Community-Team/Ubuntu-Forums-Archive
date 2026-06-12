---
title: "Why can't i connect to my ubuntu os remotly?"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by aviramof on 2010-03-22
i have ubuntu 10.04 lucid i used gnome-file-share-properties to enable remote desktop i have samba i have ping from remote computer to my ip address and computer name and etc but still i can't connect remotely via rdp or at least not via windows xp rdp what do i need to fix to enable this?

thanks in advance.

---

### Post by sahabcse on 2010-03-22
Go system>> Preference >> Remote Desktop and there select "Allow other users to view your Desktop"

---

### Post by aviramof on 2010-03-22
i did that but i still can't and i don't understand why i even disabled firestarter which i use in order to share internet with my other computer but still no luck.

---

### Post by sahabcse on 2010-03-22
is there any log file check?

---

### Post by aviramof on 2010-03-22
not that i can see windows xp just don't want to connect and i don't think it's a problem with the xp.

---

### Post by Gregorybekkers on 2010-03-22
Blame Microsoft :P
or Use VNC :)

---

### Post by aviramof on 2010-03-22
i have just installed samba 4 replaced the smb.conf with the new version and edited it a bit and i'm using GADMIN-SAMBA 0.2.8 and i also found in security this line:
connection denied from ::ffff:192.168.137.2 which is my second computer.

so what do you think about my new smb.conf file? is there something that i did wrong or that i should fix?

thanks in advance.

```

[global]
netbios name = Samba24
server string = Samba file and print server
workgroup = home
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
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
encrypt passwords = yes
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
client use spnego = non
client signing = no
client schannel = yes
server signing = no
server schannel = yes
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
hostname lookups = yes
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
winbind nested groups = yes
winbind nss info = yes
winbind refresh tickets = yes
winbind offline logon = yes

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = yes
locking = no
strict locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = yes
locking = no
strict locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = yes
public = yes
printable = yes
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = yes
guest ok = yes
public = yes
printable = yes
locking = no
strict locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =


```

---

### Post by sahabcse on 2010-03-22
what error you getting when ever connect from windows??

---

### Post by aviramof on 2010-03-22
simply can't connect to remote computer or something like this and to be hones i really don't understand why networking is so hard here i tried normal samba and samba4 and i can barely get xp to recognize ubuntu in netwrok places while xp and seven works perfectly and the problem is not the xp it's the ubuntu as i see it.

---

### Post by Gregorybekkers on 2010-03-23
Do u use VNC or RDP?

---

### Post by aviramof on 2010-03-23
rdp.

---

### Post by Zimmer on 2010-03-23
Have you created a SAMBA user on the Ubuntu machine? ... I do not use SAMBA anymore, but when I did I always created a SAMBA user with the same name (and password, belt and braces) as my username on the XP box. That seemed to clear up any access issues...

---

### Post by ortayus on 2010-03-23
How about using no machine instead?

---

### Post by aviramof on 2010-03-23
what do you mean no machine?in any case i still can't connect to my ubuntu computer not even from my second computer in the home network for no apperent reason.

---

### Post by 2hot6ft2 on 2010-03-23
Not to be rude, and I hope it doesn't come across that way, but you should be asking in this forum
[Lucid Lynx Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=377")
Since you're running a Beta of Lucid and that's where the testers are.
There may be issues with it in Lucid and that's where you'll find answers about it.

And this looks all messed up
> **aviramof said:**
> 
connection denied from **::ffff:192.168.137.2** which is my second computer.

It's part IPV6 and part IPV4. **"::ffff:"** is in the IPV6 format while **"192.168.137.2"** is in IPV4 format. The 2 shouldn't be together.

---

