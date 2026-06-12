---
title: "New Linux User Trying to Use Samba with MS Office 2007"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by rkjack1 on 2010-09-27
I have just recently installed Ubuntu 10.  I have setup Samba and my Windows Vista laptop is able to access the share successfully.  The path I shared happens to be a USB external NTFS drive.  Whenever the share is accessed from the Windows Vista box all files can be created, deleted and accessed, but for some reason, any MS Excel 2007 files on the share that are opened cannot be saved.  The error is "There is not enough disk space.  Free enough space and try again".  I have verified the permissions on the file are 777 and the directory is 777.  I am using Samba 3.4.7.  My smb.conf file is below.  Any help would be greatly appreciated.  I didn't see much related to this in the manual.  I also searched the forums and the internet, but didn't see much regarding an error when trying to save an office file.  I can save standard text.


[global]
    ; General server settings
    netbios name = primary-pc
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    follow symlinks = yes
    unix extensions = no

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1

    syslog only = yes
    log file = /var/log/samba/log.%m

    oplocks = false
    level2 oplocks = false

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;    valid users = %S
;    create mode = 0600
;    directory mode = 0755
;    browseable = yes
;    writeable = yes
;    read only = no
;    veto files = /*.{*}/.*/mail/bin/

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
    path = /media/sdf1
    browseable = yes
    writable = yes
    read only = no
    guest ok = yes
    create mask = 0777
    directory mask = 0777
    follow symlinks = yes
    valid users = winuser
    public = yes

---

