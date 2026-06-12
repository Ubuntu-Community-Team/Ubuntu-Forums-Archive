---
title: "Need help setting up samba on PC with dynamic IP address"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by KIAaze on 2010-03-03
I can't get filesharing to work.
I don't even see my samba shares locally in dolphin! (smb:/)

Here's my current /etc/samba/smb.conf:
```

[global]
    ; General server settings
        netbios name = my-desktop
        server string =
        workgroup = msheimnetz
        announce version = 5.0
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

        passdb backend = tdbsam
        security = share
        null passwords = true
        name resolve order = bcast host lmhosts wins

        wins support = no

;       printing = cups
        printcap name = CUPS

;       syslog = 1
        syslog only = yes
;       encrypt passwords = yes
;       guest ok = no
;       guest account = nobody
        username map = /etc/samba/smbusers

        client lanman auth = Yes
        lanman auth = Yes

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
;       browseable = yes
        guest ok = yes
;       read only = yes
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

[Shared]
        path = /home/shared
        browseable = yes
        read only = yes
        writeable = no
        guest ok = yes
        create mask = 0644
;       directory mask = 0755
        force user = kiaaze
        force group = kiaaze

```

```
$ smbclient -L my-desktop
Domain=[MSHEIMNETZ] OS=[Unix] Server=[Samba 3.4.0]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk
        Shared          Disk
        IPC$            IPC       IPC Service ()
        Photo_Printer_720 Printer   Photo_Printer_720
Domain=[MSHEIMNETZ] OS=[Unix] Server=[Samba 3.4.0]

        Server               Comment
        ---------            -------
        MY-DESKTOP

        Workgroup            Master
        ---------            -------
        MSHEIMNETZ           MY-DESKTOP

```

```
 $ sudo pdbedit -Lw
nobody:65534:*****
kiaaze:1000:*****

```
(edited to be safe)

```
$ hostname
my-desktop
$ uname -a
Linux my-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 02:39:34 UTC 2010 x86_64 GNU/Linux

```

I want to share the files on my Kubuntu PC with Windows machines without having to use a password if possible, and in read-only.

How can I do that?

The server has no static IP address, but I don't mind having to enter an IP address on the clients if necessary.

---

### Post by KIAaze on 2010-03-03
It works. I really need to set up a static IP address.
Having problems everytime I want to use it again.

Current /etc/samba/smb.conf:
```
[global]
    ; General server settings
;       netbios name = my-desktop
        server string =
        workgroup = msheimnetz
        announce version = 5.0
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

        passdb backend = tdbsam
        security = share
        null passwords = true
        name resolve order = bcast host lmhosts wins

;       wins support = no

;       printing = cups
        printcap name = CUPS

;       syslog = 1
        syslog only = yes
;       encrypt passwords = yes
;       guest ok = no
;       guest account = nobody
        username map = /etc/samba/smbusers

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
;       browseable = yes
        guest ok = yes
;       read only = yes
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

[SharedMusic]
        path = /home/kiaaze/Music
        browseable = yes
        read only = yes
        writeable = no
        guest ok = yes
        create mask = 0644
;       directory mask = 0755
        force user = kiaaze
        force group = kiaaze

[SharedVideos]
        path = /home/kiaaze/Videos/SharedVideos
        browseable = yes
        read only = yes
        writeable = no
        guest ok = yes
        create mask = 0644
;       directory mask = 0755
        force user = kiaaze
        force group = kiaaze

```

---

### Post by Iowan on 2010-03-04
If capable, your DHCP server (router?) might be able to issue a "static lease" to your server (based on MAC address). That'd simplify the server setup (you wouldn't need to change anything).

---

