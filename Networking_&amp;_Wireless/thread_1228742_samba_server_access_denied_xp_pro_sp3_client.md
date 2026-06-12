---
title: "samba server access denied xp pro sp3 client"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by ceders on 2009-08-01
I've been trying for days to create a home network with a samba server, using ubuntu 8.10 intrepid ibex with client XP Pro SP3. 

I can see the netbios name but denied access. I've added users with smbpasswd, and enabled them, and chmod the share directory.

Tried connecting with share name and ip address.

done the RequireSignOrSeal registry hack  HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\netlogon\parameters   
 "RequireSignOrSeal"=dword:00000000  

allowed File and Printer Sharing in Windows Firewall, and disabled it. Shutdown other firewall programs

made sure the XP's network ID and workgroup is correct ( Start> 'right click My Computer' > Properties > Computer Name > Change )

upgraded to samba4, then couldn't see the share, then installed samba again.

I'm about to throw the computer out my window...

```
 [global]
    ; General server settings
    netbios name = ubuntu
    server string =
    workgroup = WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    ;interfaces = lo, eth0
    ;bind interfaces only = true

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
    path = /home/chris/share
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = chris
    force group = chris
 

```any help is appreciated.

---

