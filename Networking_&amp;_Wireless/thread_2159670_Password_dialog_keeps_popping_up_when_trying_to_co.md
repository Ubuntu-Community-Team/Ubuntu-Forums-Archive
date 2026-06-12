---
title: "Password dialog keeps popping up when trying to connect to shared PC"
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by Huzudra on 2013-07-04
I've read several threads, applied the fixes outlined here: [http://ubuntuforums.org/showthread.php?t=1655434](http://ubuntuforums.org/showthread.php?t=1655434)
I've rebooted both systems.
I'm still getting the never ending password box and unable to access the windows machine shares. I have NO Windows Live software installed.
Suggestions? Help?

It wasn't working on 12.1 suddenly (it used to work fine) so I updated to 13.04, still not working. I'll boot up 12.04 on the other partition and see if that works but I'd like it to work on 13.04 and into the future as well.

---

### Post by varunendra on 2013-07-04
Try suggestions in this thread : [Howto : Fix Windows share browsing issues - by dmizer]("http://ubuntuforums.org/showthread.php?t=1169149")

---

### Post by Huzudra on 2013-07-04
I saw that and we're all in WORKGROUP, I can see the computer under 'Network' in Thunar so most of those steps don't seem to apply to my situation, right?
Anyway, I did go through step 1 just to make sure, I did step 2 as well just to make sure (so far everything jives, remember this used to work just fine a few weeks ago), I also went through 3. Step 4 is also right on, exactly as he shows it should be with no firewall. I checked out step 5, but I didn't try anything with it since I can't see any drives on the computer I'm trying to access since I can't get past the password prompt.

Here's my samba.conf

```
[global]
client use spnego = no
netbios name = Samba24
server string = Samba file and print server
workgroup = Workgroup
name resolve order = bcast host
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
name resolve order = wins lmhosts bcast host
wins support = no
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
allow trusted domains = no
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
passdb backend = tdbsam
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script=/usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
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
client use spnego = no

[homes]
comment = Home Directories
path = /home
valid users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[profiles]
comment = User Profiles
path = /var/lib/samba/profiles
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no

[pdf-documents]
path = /var/lib/samba/pdf-documents
comment = Converted PDF Documents
admin users = %U
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

### Post by Huzudra on 2013-07-04
It's working flawlessly fromm my 12.04.2 LTS install on the same laptop, good thing I keep 12.04 around 'just in case'. I'd love to get it working in 13.04 though. Should I compare my samab.conf between installs or should I figure out which samba version I have and try to downgrade? (how would I even do that?)

---

### Post by varunendra on 2013-07-04
> **Huzudra said:**
> It's working flawlessly fromm my 12.04.2 LTS install on the same laptop, good thing I keep 12.04 around 'just in case'. I'd love to get it working in 13.04 though.

Do you know that 13.04 is only supported for 9 months and will reach its End Of Life in January next year? Any good enough reason to go with it instead of sticking with the LTS?

Downgrading samba should be as easy as removing and re-installing both samba and winbind with "sudo apt-get install samba=<preferred version> winbind=<preferred version>", but I don't think it is going to help.

I have almost zero experience with samba, so can't really help with that. But you may be able to get plenty of support on the thread I linked to, since it is full of people who had such issues and have good experience with samba and related stuff.

Good Luck, and sorry for not being able to help with this.

**PS:**
In my very limited personal experience with Windows browsing, the password prompt issue always happened to be a problem on Windows side, a firewall issue. However, I always had admin access to those machines, so I just used to use (and remember until reboot) the administrator (or an admin user) ID/Password in the password dialogue. It allowed me access and I never bothered with troubleshooting it.

---

