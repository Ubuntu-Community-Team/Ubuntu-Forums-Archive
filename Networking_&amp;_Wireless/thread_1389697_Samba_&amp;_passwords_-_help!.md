---
title: "Samba &amp; passwords - help!"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by doctorbighands on 2010-01-24
Ok, here's the scenario.

I have a server set up in my home. It has two internal hard drives. The second "slave" drive is a data-only drive. I want to share this drive on the network in my home. I want to limit access to this drive to only certain people in my home (preferably by requiring a username/password).

That's all I want. I'm having a REALLY HARD TIME making it happen.

I installed Samba on the server, and now I can access the slave drive from any machine in the house. This is good, but it's really important for me to be able to restrict access to this slave drive. How can I tell Samba to require a username and password before displaying the contents of the slave drive on the server?

I have attempted to edit my smb.conf, but to no avail. I installed gadmin-samba, but it looks way too complex for me (I tried to use it, but ran into all kinds of problems, and I gave up).

Please help me. I feel like I'm close to getting it set up how I want, but I just can't get all the way.

Thank you to anyone who helps!

Here are the contents of the smb.conf file on the server, in case that helps. I'm pretty sure I don't need most of the junk in this file, so if someone wanted to help me clean it up a bit, that would be most welcome.
```

[global]
netbios name = Samba24
server string = Samba file and print server
workgroup = Workgroup
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
smb passwd file = /etc/samba/smbpasswd
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

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
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
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

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

### Post by doctorbighands on 2010-01-26
...bamp

I could really use some help on this, if anyone is able...

---

### Post by inobe on 2010-01-26
sure thing, here are all the steps for a successful setup, ignore what is already done.

1) we need to install samba if it's not already installed, open terminal.

```
sudo apt-get install samba
```

2) we need to create a samba user name and password in order for outsiders to access your shares with a password prompt, restrictions is a must.

replace "username" with your actual user name.

```
sudo smbpasswd -a username
```

3) we need to make a shared folder that outsiders will have access to,again don't forget your username.

```
mkdir /home/username/shares
```

4) we need to backup your current smb.conf.

```
sudo cp /etc/samba/smb.conf ~
```

5) now lets edit your smb.conf.

```
sudo gedit /etc/samba/smb.conf
```

when gedit opens' scroll down to the end and add this replacing username with your actual user name.

example:
```
[shares]
path = /home/username/shares
available = yes
valid users = username
read only = no
browsable = yes
public = yes
writable = yes
```

6) now lets restart samba.

```
sudo /etc/init.d/samba restart
```

7) lets test for errors.

```
testparm
```

if all is well' your done.


in your case you just need to setup the restrictions, that's a single command, use your actual user name when running that command and a different password other than the one on your box.

---

### Post by doctorbighands on 2010-01-28
> **inobe said:**
> 
in your case you just need to setup the restrictions, that's a single command, use your actual user name when running that command and a different password other than the one on your box.

I don't understand what this means.

I re-installed Samba on the server in order to replace my convoluted smb.conf with the "package maintainer's version."

I don't want to create special folders on the server for Samba shares (e.g., /home/user/share). I want to have access to the second internal hard drive, which is mounted on /slave, but I don't want others to have access to it. I still don't know how to make that happen.

---

### Post by Morbius1 on 2010-01-28
If you have a clean smb.conf and you haven't created a share yet you can do the following:

I don't know how you've mounted /slave so this will depend on whether or not You own the mount point:

Open Nautilus > Right click /slave > Select "sharing options" > Then check off the desired type of permissions you want. To restrict who has access do not select "guest access"

For every remote person who you want to give access, an account must be created on the server machine itself followed by a separate samba password. To accomplish this let's take an example of remote user "pete":

Open **Terminal**
Type **sudo useradd -s /bin/true pete**
[COLOR=Blue]*This will create a linux user "pete" on the server that has no server logon capability and no server home directory.*[/COLOR]
Type **sudo smbpasswd -a pete**
[COLOR=Blue]*This will create the password that "pete" will use to access the server share*[/COLOR]

You may have linux file permissions problems as well. If you do post the output of the following command:

[B]ls -dl /slave

[/B]This will tell us who owns the directory and what the permissions are on that directory.

---

### Post by doctorbighands on 2010-01-28
THANK YOU, Morbius1! This looks like exactly what I need!

I modified the share options on /slave (I originally checked the "allow guests" box - how stupid of me!). I created a user named "test" to see how the whole thing would work, and gave "test" a password.

Here are the permissions on /slave:
```
drwxrwxrwx 10 nick nick 4096 2010-01-25 21:37 /slave
```

("nick" is my name)

For some reason, I'm still not prompted for a password when I try to access /slave over the network, even after restarting Samba daemons. Do I need to reboot my client machine in order to see the results?

Thank you SO much for your help!

EDIT: I figured, since you brought it up, I'd post the relevant portion of my /etc/fstab to show you how /slave is mounted, in case it helps somehow:
```
# /dev/sdb1
UUID=74250bb8-acc7-41f6-ac7e-f952a29ed720 /slave ext3 defaults 0 0
```

---

### Post by Morbius1 on 2010-01-28
If you're not prompted for a password something is not configured correctly somewhere. Post the output of the following commands please:

Open **Terminal**
Type **net usershare info**
Type [B]testparm -s
[/B]

---

### Post by doctorbighands on 2010-01-28
Results of "net usershare info"
```
[slave]
path=/slave
comment=
usershare_acl=Everyone:F,
guest_ok=n
```

Results of "testparm -s"
```
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
```

---

### Post by Morbius1 on 2010-01-28
Everything looks correct to me. Let me ponder this a bit - it must be something obvious that we're missing here.

There is one thing: Is the client machine you're using to access the server a Windows machine? SMB on Windows has a design flaw ( my opinion ) where if it ever successfully connects to a remote machine with the correct password it remembers it. Try to reboot the windows client machine to clear the cache. 

If that doesn't work there is a way to force windows to clear it but I'll have to look through my notes for that. If the client machine is another linux machine then the problem is something else as linux does not have this flaw.

---

### Post by doctorbighands on 2010-01-28
The client machine is my laptop, which dual boots Windows and Linux, and is indeed currently booted into Windows. I suspected there might be some stinking issue like that, which is why I asked. I don't know why I even bother booting into Windows at all, but I digress...

I'll reboot and see what happens.

---

### Post by doctorbighands on 2010-01-28
I rebooted my client laptop into Ubuntu, was prompted for a password, and logged in successfully.

THANK YOU THANK YOU THANK YOU for all of your help!!

I will mark this thread solved.

---

### Post by doctorbighands on 2010-03-03
Okay, so, not quite solved after all...

I just reinstalled Vista on my laptop. I went to access the samba share on my server, and it accessed it immediately - I was not prompted for a password.

This is of great concern, because I live in a roommate situation. All my roommates are using Windows, and they absolutely cannot have access to this samba share of mine!

I'd hate to have to go the FTP route, but I'm not sure what else to do right now.

If anyone has any ideas, please help.

---

### Post by Morbius1 on 2010-03-04
When I first read your description I thought - "that's impossible".

Unless.........

There is another design flaw in Windows. When Windows attempts to access an SMB / Samba share it will actually transmit it's current Windows login user name and password. If that matches a Linux user name and samba password then you will automatically have access without being prompted.

Is this the case?

---

### Post by doctorbighands on 2010-03-04
Unbelievable.

You've nailed it again. My login credentials on my laptop exactly match those on my server, including my samba u&p. I tested the theory on a roomie's machine, and they were (thankfully) prompted for a u&p. What a stupid design by MS! On the other hand, perhaps it's a message to me to use different credentials on different machines, eh?

Thank you, once again, for your help, Morbius1. If we meet someday, I owe you a beer.

Marking this thread "solved" one more time...

---

