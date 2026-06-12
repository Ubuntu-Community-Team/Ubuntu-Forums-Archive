---
title: "can see ubuntu 9 cant acess samba share from xp or 7"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by chrismitt2002 on 2009-11-16
here is a copy of my samba setup 

[global]
; General server settings
netbios name = intel-quad
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



;[homes]
;valid users = %S
;create mode = 0600
;directory mode = 0755
;browseable = no
;read only = no
;veto files = /*.{*}/.*/mail/bin/



;[netlogon]
;path = /var/lib/samba/netlogon
;admin users = Administrator
;valid users = %U
;read only = no


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


[D-931gb]
path = /home/owner/D-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[E-931gb]
path = /home/owner/E-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[F-931gb]
path = /home/owner/F-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[G-931gb]
path = /home/owner/G-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[H-931gb]
path = /home/owner/H-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[I-931gb]
path = /home/owner/I-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

[J-931gb]
path = /home/owner/J-931gb/
browseable = yes
ready only = no
guest ok = no
create mask = 0644
directory mask = 0755
force user = owner

i can mount and acess windows shares from ubuntu 910 to xp but not from xp to ubuntu in virutual box i can see the ubuntu shares but i get path not found i was getting this error but it suddenly went away Multiple connections to a server or shared resource by the same user, using more than one user name, are not allowed. Disconnect all previous connections to the server or shared resource and try again.oh b4 i 4get how to i have my mapped drives reconnect in fstab after a reboot ????

---

