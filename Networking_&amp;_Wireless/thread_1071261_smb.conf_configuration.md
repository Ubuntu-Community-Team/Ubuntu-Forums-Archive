---
title: "smb.conf configuration?"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by erictherev on 2009-02-15
I recently upgraded my file server running Kubuntu 8.1.0 to a larger hard drive, which entailed reinstalling Kubuntu. Now I can't seem to get my Win shares back up and running. 

Originally, every time I attempted to add new shares (right-click, then go to properties, share, configure file sharing, add new share) I would get a Kde Krash handler message. I entered the shares into my /etc/samba/smb.conf file manually, but the shares still don't show up on my WinXP systems, although my Kubuntu system does show up as a workgroup computer.

Any ideas would be greatly appreciated.

---

### Post by dmizer on 2009-02-16
Moved this to it's own thread, as your problem was not related.

Take a look at the first link in my sig for how to crrectly configure smb.conf

Take special care to insure that the Ubuntu computer and Windows computers are all on the same workgroup.

---

### Post by erictherev on 2009-02-16
I posted the following as a reply to StormBringer's tutorial:

> **erictherev said:**
> In other distros I have used in the past, I was able to configure samba for sharing, then have my file share box just show up on the Win network without making any modifications to the Win machines on the network. I have transferred the same smb.conf from distro to distro and have always had good luck with this.

I recently upgraded my system from a 160Gb hdd to a 320Gb hdd, and when doing so, I managed to lose my smb.conf. Now, I'm having a hard time reconfiguring my system to share files over the Win network. In most other distro, I did this via the kcontrol panel, but in Kubuntu 8.1.0, this feature is gone.

I need help setting up my system so that it will just share to everyone, without passwords and without having to modify settings on the Win boxes.

Here's my smb.conf, if it helps at all.

```
[global]
    ; General server settings
    netbios name = HONOGHR
    server string =
    workgroup = GALACTIC_EMPIRE
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

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

[Comics]
path = /home/shared/Comics/
browseable = yes
read only = no
guest ok = yes

[Gaming]
path = /home/shared/Gaming/
browseable = yes
read only = no
guest ok = yes

[ISOs]
path = /home/shared/ISOs/
browseable = yes
read only = no
guest ok = yes

[LEGO]
path = /home/shared/LEGO/
browseable = yes
read only = no
guest ok = yes

[Music]
path = /home/shared/music/
browseable = yes
read only = no
guest ok = yes

[Setup]
path = /home/shared/Setup/
browseable = yes
read only = no
guest ok = yes

[Torrents]
path = /home/shared/torrents/
browseable = yes
read only = no
guest ok = yes
```

---

