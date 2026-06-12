---
title: "samba access problem"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by pdc124 on 2010-03-23
heres my smb.conf. i can mount the relevant stuff using smbmount from a linux client



hepworth@desktop:~$ less /etc/samba/smb.conf


[global]
        netbios name = HEPWORTH
        server string = hepworth server %L (Samba, Ubuntu)
        map to guest = Bad User
#       obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
log level =2
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
security = user


[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers

[printers]
        comment = All Printers
        path = /var/spool/samba
        create mask = 0700
        printable = Yes
        browseable = No
#[homes]
#       valid users = %S
#       read only = No
#       browseable = yes
#writeable = yes

[Anne's stuff]
path=/home/adc65
browseable = yes
writeable =yes

[shared documents]
        comment = shared documents
        valid users = adc65,amb43
        writeable = yes
        path = /home/sharedDocs
browseable = yes
writeable = yes

[public]
path = /home/public
browseable =yes
public = yes

and from a winXP client I can see the shares - Annes stuff , shared Documents, public 

I can access the public folder , but not the other 2 

the log file ( log level 3) 
[2010/03/23 22:24:49,  2] smbd/service.c:create_connection_server_info(652)
  guest user (from session setup) not permitted to access this share (shared documents)
[2010/03/23 22:24:49,  0] smbd/service.c:make_connection_snum(744)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2010/03/23 22:24:49,  2] smbd/service.c:create_connection_server_info(652)
  guest user (from session setup) not permitted to access this share (shared documents)
[2010/03/23 22:24:49,  0] smbd/service.c:make_connection_snum(744)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2010/03/23 22:24:52,  2] smbd/service.c:create_connection_server_info(652)

etc etc

smbmount works , ive added the user/password with smbpasswd. so ive no tidea where its gone wrong and why the guest user crops up

if i change the security = share, the login says hepworth/guest and asks me for a password

I dont know where its getting the guest user from

---

### Post by capscrew on 2010-03-23
> **pdc124 said:**
> heres my smb.conf. i can mount the relevant stuff using smbmount from a linux client



hepworth@desktop:~$ less /etc/samba/smb.conf


[global]
        netbios name = HEPWORTH
        server string = hepworth server %L (Samba, Ubuntu)
        map to guest = Bad User
#       obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
log level =2
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes [COLOR="Red"]**<-- Here is the guest**[/COLOR]
        panic action = /usr/share/samba/panic-action %d
security = user
...

See the notation in red> 
...

        browseable = No
#[homes]
#       valid users = %S
#       read only = No
#       browseable = yes
#writeable = yes

[Anne's stuff]
path=/home/adc65
browseable = yes
writeable =yes

[shared documents]
        comment = shared documents
        valid users = adc65,amb43
        writeable = yes
        path = /home/sharedDocs
browseable = yes
writeable = yes

[public]
path = /home/public
browseable =yes
public = yes

and from a winXP client I can see the shares - Annes stuff , shared Documents, public 

I can access the public folder , but not the other 2 

the log file ( log level 3) 
[2010/03/23 22:24:49,  2] smbd/service.c:create_connection_server_info(652)
  [COLOR="Red"]guest user (from session setup)[/COLOR] not permitted to access this share (shared documents)
[2010/03/23 22:24:49,  0] smbd/service.c:make_connection_snum(744)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2010/03/23 22:24:49,  2] smbd/service.c:create_connection_server_info(652)
  guest user (from session setup) not permitted to access this share (shared documents)
[2010/03/23 22:24:49,  0] smbd/service.c:make_connection_snum(744)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED
[2010/03/23 22:24:52,  2] smbd/service.c:create_connection_server_info(652)

etc etc

smbmount works , ive added the user/password with smbpasswd. so ive no tidea where its gone wrong and why the guest user crops up

if i change the security = share, the login says hepworth/guest and asks me for a password

I dont know where its getting the guest user from

There are now 2 ways to configure Samba.  Through the GUI (via *usershares*) and the classic CLI method.  The smbmount knows nothing of Nautilus.  That's why it works as you expected.  In addition, the usershare in your smb.conf file is in the global section and therefore becomes the default for all shares.

---

### Post by pdc124 on 2010-03-24
this was done using webmin and a bit of CLI . Which GUI should I be using?
the problem is that its not working as expected !

---

### Post by Iowan on 2010-03-24
Nautilus would be the GUI (unless I'm mistaken... again) and it configures shares in */var/lib/samba/usershare*. The classic CLI method uses */etc/samba/smb.conf* (as mentioned).

---

### Post by capscrew on 2010-03-24
> **pdc124 said:**
> this was done using webmin and a bit of CLI . Which GUI should I be using?
the problem is that its not working as expected !

Webmin is a GUI for configuring Samba.  It uses scripts for the configuration.  Nautilus is what I was referring to.  It uses lower level calls to achieve the same *usershare *configuration.

I'm not a fan of Webmin and have never used it.  All of my Samba installs have been configured via CLI.

This does not mean that you can successfully configure Samba by Nautilus.  Many have done it.  If you use Nautilus then the config files are where Iowan as said (/var/lib/samba) and the mount point is in your home directory at .gvfs.

---

### Post by skidaddy on 2010-03-24
you might like to use a program smb4k i use it works not sure what it uses

---

