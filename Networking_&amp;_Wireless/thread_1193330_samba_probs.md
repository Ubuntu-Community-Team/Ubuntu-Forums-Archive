---
title: "samba probs"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by johnh10000 on 2009-06-21
Hi gang

Under ubuntu 8.10 samba worked fine.  several changes later:

ubuntu 9.04
virgin media (cable) arrived
netgear wgr614 wireless router arrived (with above)

now I get "failed to retrive shares list from server"

Oh I opened ports 137,139,445 tcp on both guarddog and the netgear

I am new to this bit .... H E L P .... 
please

---

### Post by dmizer on 2009-06-21
Please see the 6th link in my sig :)

Edit:
Not sure about guarddog (don't even know what that is), but on your router, close those ports but quick. That's opening the ports to the web, not to the lan. Routers don't filter LAN traffic, so you shouldn't have to adjust anything on it to allow for Samba browsing.

Edit2:
Just figured out what guarddog is. If you have a router, the router firewall is sufficient. There's no need to filter your traffic twice. The only reason you should consider using a local firewall is if there is not a firewall at the gateway (router), or you're frequently connected to unprotected networks.

---

### Post by swerdna on 2009-06-22
> 137,139,445 tcpAs dmizer noted -- don't open them on the router or there'll be tears.

Those aren't correct. The ports you need for a Samba workgroup are:
TCP139 TCP445 UDP137 UDP138

---

### Post by dmizer on 2009-06-22
> **swerdna said:**
> Those aren't correct. The ports you need for a Samba workgroup are:
TCP139 TCP445 UDP137 UDP138

Actually, even those are not correct. Here is the complete list:
Port 135/TCP - used by smbd
Port 137/UDP - used by nmbd
Port 138/UDP - used by nmbd
Port 139/TCP - used by smbd
Port 445/TCP - used by smbd


Either way though, the root cause of the problem is the unnecessary Guarddog. If uninstalled the problem will likely be fixed.

---

### Post by johnh10000 on 2009-06-22
> **dmizer said:**
> Please see the 6th link in my sig :)

Edit:
Not sure about guarddog (don't even know what that is), but on your router, close those ports but quick. That's opening the ports to the web, not to the lan. Routers don't filter LAN traffic, so you shouldn't have to adjust anything on it to allow for Samba browsing.

Edit2:
Just figured out what guarddog is. If you have a router, the router firewall is sufficient. There's no need to filter your traffic twice. The only reason you should consider using a local firewall is if there is not a firewall at the gateway (router), or you're frequently connected to unprotected networks.

Thanks for that, however , I decided to remove samba compleately and then folow your tut no.1.  Bad news.  It still don't work :(

I took your advice and shut the ports on the router.

Now is there another way of this sharing bit?  ftp I have working. I will need to share a printer though.

---

### Post by swerdna on 2009-06-22
> **dmizer said:**
> Actually, even those are not correct. Here is the complete list:
Port 135/TCP - used by smbd
Port 137/UDP - used by nmbd
Port 138/UDP - used by nmbd
Port 139/TCP - used by smbd
Port 445/TCP - used by smbd


Either way though, the root cause of the problem is the unnecessary Guarddog. If uninstalled the problem will likely be fixed.
I agree with your diagnosis re firewall. But I respectfully point out that I listed ports "for a Samba workgroup" and not for an interaction with a windows server (where you would need TCP135), but yes the complete series includes 135 for all situations.

---

### Post by dmizer on 2009-06-22
> **johnh10000 said:**
> Thanks for that, however , I decided to remove samba compleately and then folow your tut no.1.  Bad news.  It still don't work :(

I took your advice and shut the ports on the router.

Now is there another way of this sharing bit?  ftp I have working. I will need to share a printer though.

Do you want to share files to Windows, or are you trying to access Windows shares from Ubuntu? Have you tried disabling/removing guarddog?

Please post your current /etc/samba/smb.conf

---

### Post by johnh10000 on 2009-06-22
> **dmizer said:**
> Do you want to share files to Windows, or are you trying to access Windows shares from Ubuntu? Have you tried disabling/removing guarddog?

Well it'd be nice to have windows shares and ubuntu shares and the ubuntu dvd, and printer.  This worked out of the box be4 router and 9.04 arrived.

Please post your current /etc/samba/smb.conf
As requested smb.conf:

[global]
    ; General server settings
    netbios name = TUX
    server string =
    workgroup = MSHOME
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
[homes]
    valid users = %S
    create mode = 0600
    directory mode = 0755
    browseable = no
    read only = no
    veto files = /*.{*}/.*/mail/bin/

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
[DVD-ROM Drive]
    path = /media/cdrom
    browseable = yes
    read only = yes
    guest ok = yes

[MyFiles]
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = johnh10000
    force group = johnh10000

---

### Post by johnh10000 on 2009-06-22
> **dmizer said:**
> Do you want to share files to Windows, or are you trying to access Windows shares from Ubuntu? Have you tried disabling/removing guarddog?

Please post your current /etc/samba/smb.conf

I hadn't until last of course. Then it sorta worked.

Then found hidden away, smb turn that on in guarddog an away we go.

Cheers for everyones help.

Oh the web site's getting there too!

tux.isa-geek.org

---

