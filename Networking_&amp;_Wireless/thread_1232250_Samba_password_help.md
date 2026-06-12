---
title: "Samba password help"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by mitsios on 2009-08-05
Hi, i need some help. I have googled this problem but nothing seems to work.

I have a network which consists of an Ubuntu 9.10, a Win XP and Vista.

I have recently set up Samba with one user. But because I -obviously- had more than one username on windows, I decided to add another samba user. I created an unprivileged user on Ubuntu and used that for the second Samba user. I had also given it it's own password. 
Everything seemed to work fine, but now all Samba users have the same password, which is the one I use for the machine's root account. I tried changing them but they revert back.

I tried disabling unix password sync, as well as removing libpam-smbpass with no luck.

Any help would be appreciated.

---

### Post by superprash2003 on 2009-08-05
post output of /etc/samba/smbusers .. have you configured the smb.conf file to authenticate a certain shared folder with certain VALID users

---

### Post by mitsios on 2009-08-06
The output is:

stavros = stavros
omiros2 = Omiros

---

### Post by superprash2003 on 2009-08-06
are these the correct 2 users?? post contents of smb.conf file

---

### Post by mitsios on 2009-08-06
smb.conf contents:

[global]
    ; General server settings
;    netbios name = stavros-ubuntu
    server string = 
    workgroup = stavros1
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    null passwords = true
    name resolve order = hosts wins bcast

    wins support = yes

;    unix password sync = no
;    pam password change = no

;    printing = cups
    printcap name = CUPS

;    syslog = 1
    syslog only = yes
;    encrypt passwords = yes
;    guest ok = no
;    guest account = nobody

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
;    browseable = yes
    guest ok = yes
;    read only = yes
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
    path = /media/Files/
;    browseable = yes
    writeable = yes
    create mask = 0644
;    directory mask = 0755
    force user = stavros
    force group = stavros
    guest ok = yes

[Downloads]
    path = /home/stavros/Downloads
;    writeable = No
;    browseable = yes
    guest ok = yes

---

### Post by superprash2003 on 2009-08-07
do uncomment the line browseable = yes .. and remove the line force user and force group

---

### Post by mitsios on 2009-08-07
No luck, the password still gets reverted. But I noticed one thing. Samba automatically comments the line "unix password sync" and "pam password change". Could this be the problem?

---

### Post by mitsios on 2009-08-13
bump

---

### Post by mitsios on 2009-08-16
bump

---

### Post by Iowan on 2009-08-16
It's been awhile since I configured Samba - and longer since I used security=share.  Prior posts have discussed changing passwords - sounds like you've changed both the Ubuntu password and the Samba password (if not, try it). One loose end that I'm not sure about is the PAM module.  I dunno if that comes into play except on an LDAP system, but if something else is managing passwords, I suppose it might be possible for that "something" to be changing things back.

---

