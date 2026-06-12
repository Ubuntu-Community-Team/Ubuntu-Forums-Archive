---
title: "Remove Samba Password"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-03-11
I followed [this guide]("http://ubuntuforums.org/showthread.php?t=202605") and got Samba setup sucessfully, but to connect I have to type in my username and password, I don't want this.

I perhaps want a different password or no password to be used.

Can I have one share that has no password, another that has a password, and another that has a different password?

---

### Post by Iowan on 2009-03-11
Security is generally set in the "general" section... I don't know if individual shares can be set for "user" or "share"...

---

### Post by RealG187 on 2009-03-11
General section where?

---

### Post by Iowan on 2009-03-11
```
[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    server string =
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    [COLOR="Red"]security = user[/COLOR]
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast
```

Sorry... I meant *global* section

---

### Post by RealG187 on 2009-03-11
that's in the smb.conf file?

So what should I put?

---

### Post by RealG187 on 2009-03-20
> [global]
    ; General server settings
    netbios name = MIKED6
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
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

There is my smb.conf file, how do I remove the login prompt period once and for all?

---

