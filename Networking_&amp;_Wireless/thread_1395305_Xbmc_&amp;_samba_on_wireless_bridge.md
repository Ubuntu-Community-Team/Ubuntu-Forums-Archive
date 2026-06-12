---
title: "Xbmc &amp; samba on wireless bridge"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by cbaughman on 2010-01-31
I made the switch to Ubuntu for my media sever this weekend and so far almost everything is working. I have a second XBMC in the bedroom connected via a wireless bridge. However so far it can't see the media sever. I'm wondering if it's a setting in the /etc/samba/smb.conf that needs to be changed. 

Thanks for any help you can give.

Here is a copy of that file. Media sever is ip 192.168.1.2, gateway for sever is 192.168.1.1, gatway for bridge 192.168.0.1 and the bedroom xbmc is 192.168.0.9
```

[global]
; General server settings
netbios name = cbud1 
server string = (leavethisblank)
workgroup = cbwg
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

;interfaces = 127.0.0.1, 192.168.2.1/24
interfaces = lo, eth1 (put you ethX here ,eth0 or 1 etc.)
bind interfaces only = true

hosts allow = 192.168.1.6 192.168.1.4 192.168.0.9 192.168.0.1
hosts deny = 0.0.0.0/0

passdb backend = tdbsam
security = user
encrypt passwords = true
username map = /etc/samba/smbusers
obey pam restrictions = yes
invalid users = root

name resolve order = hosts wins bcast

wins support = no

; printing = CUPS
; printcap name = CUPS

syslog = 1
syslog only = yes

# Do something sensible when Samba crashes: mail the admin a backtrace
panic action = /usr/share/samba/panic-action %d

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0700
;browseable = no
;read only = yes
;veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = yes

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
;path = /var/lib/samba/profiles
;valid users = %U
;create mode = 0600
;directory mode = 0700
;writeable = no
;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
;[print$]
;path = /var/lib/samba/printers
;browseable = no
;guest ok = no
;read only = yes
;write list = root
;create mask = 0644
;directory mask = 0755

;[printers]
;path = /tmp
;printable = no
;guest ok = no
;browseable = no

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
;path = /media/cdrom
;browseable = no
;read only = yes
;guest ok = no

[MyFiles]
path = /mnt/MediaV1/
browseable = yes 
read only = yes
guest ok = no
create mask = 0600
directory mask = 0700
force user = xbox 
force group = xbox

```

---

### Post by lakerssuperman on 2010-02-03
I have a HTPC that can connect wirelessly to my main Video server.  I have the box running Ubuntu 9.10 and have it set to auto start XBMC.  The problem is that the wireless connection is setup after XBMC is already loaded.  I think that XBMC is not aware of the connection as a result and my Samba browsing fails.  However if I restart XBMC and try to browse it works perfectly.  I am currently searching for a way to make sure the wireless connection is up and running before XBMC starts to make sure that I don't have to constantly restart XBMC every time I turn on the HTPC.

---

