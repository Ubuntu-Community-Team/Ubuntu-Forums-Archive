---
title: "Trying to network with an iMac"
date: 2006-02-04
forum: Networking &amp; Wireless
---

### Post by mmcmonster on 2006-02-04
Hi.
  I'm trying to network my Ubuntu PC with an iMac running the latest version of OSX.

I'm basically trying to create a workgroup called "RAMONA", with this computer being called "Avalon".  With this setup, the iMac sees the workgroup Ramona and the computer Avalon in that workgroup.  There is a button to connect to Avalon.  When I click the button, the iMac hangs!!!

Can someone please tell me what I am getting wrong?  My /etc/samba/smb.conf is the following:

I'm a networking novice, so any help is appreciated!

```

[global]
   workgroup = RAMONA
   server string = %h server (Samba, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
security = share
username map = /etc/samba/smbusers
   encrypt passwords = true
   passdb backend = tdbsam guest
   obey pam restrictions = yes
   invalid users = root
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   socket options = TCP_NODELAY
wins support = no
[homes]
   comment = Home Directories
   browseable = no

   writable = yes

   create mask = 0700

   directory mask = 0700

[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700

[print$]
   comment = Printer Drivers
   path = /var/lib/samba/printers
   browseable = yes
   read only = yes
   guest ok = no
[AvalonHome]
path = /home
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes


```

---

### Post by rapidwiz on 2008-03-01
I had a lot of problems connecting my iMac to my Ubuntu shares which works fine for my linux/windows shares but not for my iMac.

I had to take 3 steps

1. Create smbuser (useradd smbuser)
2. Enable Guest account in global section (guest account = smbuser)
3. Enable Public = Yes in share section


 more /etc/samba/smb.conf 
[global]
   workgroup = MYGROUP
   server string = VMS Server
   hosts allow =  192.168.2.
;   printcap name = /etc/printcap
   load printers = yes
   printing = lprng
   guest account = smbuser
   log file = /var/log/samba/%m.log
   ;max log size = 0
   security = share
   encrypt passwords = true
   smb passwd file = /etc/samba/smbpasswd
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
   dns proxy = no 
   log level = 2
   debug level = 2

[fs2]
   path = /fs2/movies
   only guest = no
   writable = yes
   valid users = smbuser
   browseable = no
    public = yes

---

