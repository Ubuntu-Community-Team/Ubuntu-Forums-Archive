---
title: "Ubuntu 10.10 Desktop &amp; Samba issues :("
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by The Guv. on 2011-03-28
I'm building a very simple NAS box, my plan was originally to use Freenas 8 but there was issues with it and I couldn't get it to run nicely on my hardware (D525MW). After faffing around with that, I went back to do what I wanted to do in the first place which was install Ubuntu and Samba to do the job as Ubuntu has been very stable for me in the past using it on my HTPC.

However, after installing 10.10 and Samba I've found issues with windows (XP, Vista & 7) connecting to the shares. The NAS doesn't appear in the WORKGROUP but if I address it by it's IP address from the run command I get a list of shares... Problem is when I try to open one of the shares it asks for a User/Pass (as it's meant to) and when I enter the details it then proceeds to tell me that windows couldn't access the share!

I've also got a 'Shared' share which doesn't require a Username/Password, and even that I can't view.

Anyone have any ideas? I'm pulling my hair out here I've been working on this nas box for 3 days solid now and I'm yet to upload a single file!

Thank you! :cool:

---

### Post by fela on 2011-03-28
Do you have another Linux box on the network? If not, either use that or fire up an Ubuntu live cd on some other box.

Make sure you're connected to the network obviously, and run:

```
findsmb
```

Then post the output of that...

(oh yeah, also test whether or not it sees the server in the file browser on Linux)

---

### Post by The Guv. on 2011-03-28
```
ubuntu@ubuntu:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.75    IAIN_MORRISON  [IAIN_MORRISON] [Windows 5.1] [Windows 2000 LAN Manager]
192.168.1.85    ENTERTEE-SERVER+[WORKGROUP] [Unix] [Samba 3.5.4]
192.168.1.85    ENTERTEE-SERVER+[WORKGROUP] [Unix] [Samba 3.5.4]
ubuntu@ubuntu:~$
```Can be accessed through the file/network browser as well although I can't get access to the Shared folder (shouldn't require login but it requests, although it doesn't accept any logins including root), I can get access to two folders (James & Iain) I've been tweeking with appending usernames everywhere through the SWAT interface. Also these folders can be accessed through Windows now, although I don't know what part of my tweaking played a part in that and as it's not as clean as I feel it should be I don't really want to go around blind guessing settings if you know what I mean.

```
Samba config file created using SWAT
# from UNKNOWN (192.168.1.103)
# Date: 2011/03/28 13:23:54

[global]
server string = Entertee NAS
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
username map = /etc/samba/smbusers
unix password sync = Yes
syslog = 0
max log size = 1000

[printers]
comment = All Printers
path = /var/spool/samba
create mask = 0700
printable = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
read only = No
guest ok = Yes

[James]
path = /media/Drive A/Users/James
username = james
valid users = james
admin users = james
read list = james
write list = james
read only = No
create mask = 0775
directory mask = 0775
inherit owner = Yes

[Shared]
path = /media/Drive A/Shared
valid users = *
read only = No
guest ok = Yes

[Iain]
path = /media/Drive A/Users/Iain
username = iain
valid users = iain
admin users = iain
read list = iain
write list = iain
read only = No
create mask = 0775
directory mask = 0775
inherit owner = Yes

[Paul]
path = /media/Drive A/Users/Paul
valid users = paul
read only = No

[Reece]
path = /media/Drive A/Users/Reece
valid users = reece
read only = No

[Gill]
path = /media/Drive A/Users/Gill
valid users = gill
read only = No

[Emma]
path = /media/Drive A/Users/Emma
valid users = emma
read only = No

[Christina]
path = /media/Drive A/Users/Christina
valid users = christina
read only = No

[Sarah]
path = /media/Drive A/Users/Sarah
valid users = sarah
read only = No
```I was hoping that it would be a pretty simple task! Or maybe I'm being simple!

---

### Post by fela on 2011-03-28
Here I've made a few modifications off the top of my head...

```

Samba config file created using SWAT
# from UNKNOWN (192.168.1.103)
# Date: 2011/03/28 13:23:54

[global]
server string = Entertee NAS
workgroup = WORKGROUP
server string = Samba Server
netbios name = ENTERTEE_NAS
security = user
name resolve order = hosts wins bcast
wins support = yes
use wins = yes
map to guest = Bad User
pam password change = Yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
username map = /etc/samba/smbusers
unix password sync = Yes
syslog = 0
max log size = 1000

[printers]
comment = All Printers
path = /var/spool/samba
create mask = 0700
printable = Yes
browseable = No

[print$]
comment = Printer Drivers
path = /var/lib/samba/printers
read only = No
guest ok = Yes

[James]
path = /media/Drive A/Users/James
username = james
valid users = james
admin users = james
read list = james
write list = james
read only = No
create mask = 0775
directory mask = 0775
inherit owner = Yes

[Shared]
comment = Public Share
path = /media/Drive A/Shared
available = yes
browsable = yes
writable = yes
public = yes

[Iain]
path = /media/Drive A/Users/Iain
username = iain
valid users = iain
admin users = iain
read list = iain
write list = iain
read only = No
create mask = 0775
directory mask = 0775
inherit owner = Yes

[Paul]
path = /media/Drive A/Users/Paul
valid users = paul
read only = No

[Reece]
path = /media/Drive A/Users/Reece
valid users = reece
read only = No

[Gill]
path = /media/Drive A/Users/Gill
valid users = gill
read only = No

[Emma]
path = /media/Drive A/Users/Emma
valid users = emma
read only = No

[Christina]
path = /media/Drive A/Users/Christina
valid users = christina
read only = No

[Sarah]
path = /media/Drive A/Users/Sarah
valid users = sarah
read only = No

```

Edit; btw you're not being stupid, Samba is really hard to configure! :@

Also, edit the file by hand, don't use the SWAT interface.

EDIT 2: attached the working smb.conf file in my server.

---

