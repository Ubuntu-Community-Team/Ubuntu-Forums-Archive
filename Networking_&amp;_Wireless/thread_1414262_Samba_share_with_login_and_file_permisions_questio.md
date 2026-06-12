---
title: "Samba share with login and file permisions question"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by mad_max0204 on 2010-02-23
Hi,

I have a folder on my linux server and I want to be able to share files to windows users in this manner :
1. Require login with username and password when accessing file share.
2. Files created by logged in users become owned by them (I can create local accounts for this matter to all the users).
3. Depending on permissions files created by other users can be read only by logged in user.

I thought of going in samba way for this but I'm not familiar with samba enough to make something like this. If any other sharing method is required I can go for it since I'm doing this from a scratch but that only if its not possible with samba.

Thanks

---

### Post by mad_max0204 on 2010-02-24
bump

---

### Post by Morbius1 on 2010-02-24
Let's say you have a share at /lanshare

You could create a share definition in smb.conf that looks like this:

[lanshare]
  path = /lanshare
  guest ok = no
  read only = no

This will take care of item (1) and (2). Only authenticated users will have access to the share and when they save a file to that share they will be the owner.

Item (3) is a little trickier. There may be a Samba way to do this but I'm thinking perhaps linux file permissions may be the way to do this:

Change the permissions on the /lanshare directory:

**sudo chmod 1777 /lanshare**

What should happen with the "1" "sticky" bit is to prevent users other than the owner from deleting files or directories inside the share. The owner has full rights to files and directories created by him, but others will have read-only rights to files and directories they don't own.

It's worth a shot

---

### Post by mad_max0204 on 2010-03-02
I cannot make this work. I always get the message:
You do not have permission to access \\10.10.0.10. Contact your network administrator to request access.

This is from Windows 7 computer. I just simply have no more ideas.
Any, and I mean any, help is very much appreciated.

---

### Post by Morbius1 on 2010-03-02
Did you create a samba user on the server corresponding to the windows client user?

For example:
> Let's say you have a remote user named john:

Open **Terminal**
Type **sudo useradd -s /bin/true john**
[COLOR=Blue]*This will create the user john on the server that has no local server logon capability and no server home directory.*[/COLOR]
Type[B] sudo smbpasswd -a john
[/B][COLOR=Blue][I]This will add AND activate the samba user john on the server.
[/I][/COLOR]

Or if you want to use your server username to access the share from the remote machine:
Type** sudo smbpasswd -a your_local_server_user_name**

---

### Post by Gaurav_Ag on 2010-05-17
Hi,
I'm working on samba.I need following things to happen

1. Whenever a new user logins he/she should get a new folder with all the permissions individually.
2. When we login from root we should have complete permissions.
3. Need not create separate user each time with their permissions.

My smb.config file is as : 

```

[global]
    ; General server settings
    netbios name = gaurav
    server string =
    workgroup = MQ
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
    ;valid users = %S
    ;create mode = 0600
    ;directory mode = 0755
    ;browseable = no
    ;read only = no
    ;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes
    browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[MyFiles]
    path = /home/samba/
    browseable = no
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = gaurav
    force group = gaurav

[Florian]
path = /home/samba/Florian
browseable = yes
read only = no
guest ok = no
create mask = 0644
directory mask = 0770
force user = florian
force group = florian

```Here each time adding the user and have to create the folder Ex- florain.
So i want this to be done just dynamic not manually all the time.

---

