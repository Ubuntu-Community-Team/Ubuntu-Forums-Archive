---
title: "server 8.04(.2) samba auto-changes passwords?"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by the kaz on 2009-02-10
Hello all, 
I have a strange probleme with two 8.04 server installations running samba as sole domain controller for a few Windows machines. 

Some of the users have different passwords for their unix accounts on the same machine as the samba accounts. But since we upgraded to 8.04 (from 7.04), their samba passwords keep changing back to their unix passwords, i.e. after a day or so, they cannot login anymore unsing the new password, they have to enter the unix one. If they change it back via smbpasswd, it works for the day or so, but the next day they have to use the old password again.

Does anybody have any idea samba behaves this bezarrely? The global section of the smb.conf file (which hasn't changed since way before the update to 8.04) looks like this:

> 
[global]
workgroup = <MY_LOCAL_DOMAIN>
netbios name = <MY_NETBIOS_NAME>
debug level = 1 passdb:1 auth:1
encrypt passwords = true
preserve case = yes
os level = 65
log file = /var/log/samba/%m.log
passdb backend = smbpasswd:/etc/samba/smbpasswd
security = user
printing = cups
load printers = yes
printcap name = cups
domain master = yes
unix charset = utf-8
display charset = utf-8
domain logons = yes
preferred master = yes
max log size = 100000
kernel oplocks = no
wins support = yes
dns proxy = yes
time server = yes
hosts allow = <MY_LOCAL_NETWORKS>
remote announce = <MY_LOCAL_NETWORKS>
logon home = \\double\home\.config\%m
logon path = \\double\home\.config\%m
auto services = netlogon
logon script = %U.bat
socket options = TCP_NODELAY IPTOS_THROUGHPUT SO_RCVBUF=4096 SO_SNDBUF=4096
interfaces = <MY_LOCAL_INTERFACES>
server string = <MY_SERVER_NAME>


All our Windows machines store profiles locally and are configured not to use server-stores profiles. Additionally, we don't have any logon scripts anymore; these are remants of an earlier configuration which could be removed. I just included them for accuracy, perhaps they are the culprits for the odd behaviour. 

Any help is appreciated.

Greetings, the kaz.

---

### Post by Iowan on 2009-02-10
I don't have my favorite Samba book with me today, but I seem to remember an option to synchronize passwords - just don't remember the wording.

---

### Post by the kaz on 2009-02-12
Hello again,
yes, you can synchronize passwords using "unix password sync" - but a) that option is not in my smb.conf and the default value is "no", and b) this would only change Unix passwords whenever the samba one is changed. 

In my case, it's vice versa: the samba password changes back to the unix one - and, as far as I can tell, without any user action whatsoever. The user changes his samba password via smbpassword, this seems to work, but a day later the samba password's back to the old value (which happens to be the unix password, but whether that's just a coincidence I don't know). 

As I wrote before, this behaviour started when I upgraded the server from 7.04 to 8.04(.2) - which didn't change as much as one bit of the smb.conf. I'm at a loss as to what could be the problem here. 

Greetings, the kaz.

---

### Post by Joe Beam on 2009-02-13
Kaz, I am having the exact same behavior. I setup an 8.10 ubuntu-server and smbpasswd works for like a day and then it goes back to the unix password. It's hard to say when it reverts, because it's not on a reboot of the machine or restart of the samba server. My samba server is super simple and here is my smb.conf

```
[global]
   workgroup = MSHOME
printcap name = /dev/null
hosts allow = 127.0.0.1 <other hosts>
hosts deny = 0.0.0.0/0
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   interfaces = 127.0.0.0/8 eth0
   bind interfaces only = yes
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   security = user
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   invalid users = root
   unix password sync = no
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = no
[motion]
comment = motion snapshots and video
path = /home/motion
valid users = <user>
read only = yes
guest ok = no

```

It's driving me crazy! I wish I knew more about pam. Since it's hard to reproduce, I've been switching config options each day and then checking back the next day to see if my smbpasswd will hold. I thought it was winbind but I removed that and I still get the problem. I'm running out of ideas...

---

### Post by Joe Beam on 2009-02-17
[solved]
I have removed libpam-smbpass and my samba password does not revert to the unix password anymore. This was the first time I installed samba through the CD server install option. It must use this module by default??...

---

### Post by Packdude on 2009-12-09
Joe, thank you for posting this solution.  I have been using Samba for years on various Linux distros, and never before saw this crazy problem until the latest Ubuntu release.  I was also trying all kinds of things like turning off pam options in the smb.conf, etc. but nothing seemed to be working.

I guess most people like their shell account password and Samba password to be the same, but not me!

Thanks again.

---

### Post by frankvw on 2010-03-10
> **Joe Beam said:**
> [solved]
I have removed libpam-smbpass and my samba password does not revert to the unix password anymore.

Thank you!!!!!

One question, though: must you unistall the libpam package entirely, or is it sufficient to disable all use of PAM in smb.conf?

// FvW

---

