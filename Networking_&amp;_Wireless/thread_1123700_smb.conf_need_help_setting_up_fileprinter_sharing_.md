---
title: "smb.conf: need help setting up file/printer sharing over LAN"
date: 2009-04-12
forum: Networking &amp; Wireless
---

### Post by MaxIBoy on 2009-04-12
Been mucking with /etc/samba/smb.conf for a while now (over a month, on and off.) I still can't get it right.

I need to be able to remotely browse my home folder from the house's XP box, but I don't want it to be free for all (that is, proper password authentication needs to be required.) I also need remote printing to work.

Right now, the XP box can see that my server (hostname "server") exists, but that's it. It cannot recognize that any printers are attached to it, nor can it see any network shares.

In the screenshot, "JEMAMA" is the XP box, and "SERVER" is my server. "SERVER" shows no connected devices.

[IMG]http://img13.imageshack.us/img13/2765/noprinters.jpg[/IMG]

Right now, getting the printers working is priority one.



Here is my /etc/samba/smb.conf:
```
[global]
   workgroup = JEMAMAGROUP
   netbios name = server
   server string = %h server (Samba, Ubuntu)

   
   passdb backend = tdbsam
   security = user
   username map = /etc/samba/smbusers
   name resolve order = wins bcast hosts
   domain logons = yes
   preferred master = yes
   wins support = yes
   
   # Set CUPS for printing
   printcap name = CUPS
   printing = CUPS
   
   # Default logon
   logon drive = H:
   logon script = scripts/logon.bat
   logon path = \\server1\profile\%U


   # Useradd scripts
   add user script = /usr/sbin/useradd -m %u
   delete user script = /usr/sbin/userdel -r %u
   add group script = /usr/sbin/groupadd %g
   delete group script = /usr/sbin/groupdel %g
   add user to group script = /usr/sbin/usermod -G %g %u
   add machine script = /usr/sbin/useradd -s /bin/false/ -d /var/lib/nobody %u
   idmap uid = 15000-20000
   idmap gid = 15000-20000


   # sync smb passwords woth linux passwords
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\sUNIX\spassword:* %n\n *Retype\snew\sUNIX\spassword:* %n\n .
   passwd chat debug = yes
   unix password sync = yes
   
   # set the loglevel
   log level = 3

[allusers]
  comment = All Users
  path = /home/shares/allusers
  browsable = yes
  guest ok = yes
  writable = yes


[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   admin users = Administrator
   read only = no
   guest ok = yes

#[homes]
#   comment = Home
#   read only = yes
#   browsable = yes
#   guest ok = yes

[max]
   comment = Max home
   path = /home/max
   guest ok = No
   read only = No
   browseable = yes
   admin users = Administrator
   valid users = max


[printers]
   comment = All Printers
   path = /var/spool/samba
   printable = yes
   guest ok = yes
   browsable = yes


[profile]
   comment = User profiles
   path = /home/samba/profiles
   valid users = %U
   create mode = 0600
   directory mode = 0700
   writable = yes
   browsable = yes


```I'll provide any other configuration files on request

---

