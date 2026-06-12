---
title: "Connecting Vista to Ubuntu via Samba"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by Aweyer2 on 2009-08-11
While trying to connect my Vista machine to ubuntu I get this error message on vista 192.168.1.107 is not set up to establish a connection on port "file and printer sharing (SMB)' with this computer. 192.168.1.107 is my Ubuntu ip address. I have a dynamic ip address and am attempting to connect to my ubuntu machine via network drive mapping. Here is how Samba is configured 

[global]
    ; General server settings
    netbios name = ajweyer
    server string =
    workgroup = WEYER
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
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = ajweyer
    force group = ajweyer

any help would be greatly appreciated. The ubuntu firewall is set to allow incoming traffic.
Please be basic, I do not know many linux commands so if possible, list any commands I may need to open up the necessary ports. I can ping my ubuntu machine from windows and vice versa.

---

### Post by swerdna on 2009-08-12
I suggest these changes in the [global] stanza:
edit this line: name resolve order = hosts wins bcast
to this: name resolve order = bcast host lmhosts wins
note that it's host not hosts

add these lines into [global]:
map to guest = bad user
local master = yes
preferred master = yes
os level = 32

After the changes, reboot to restart Samba and get a browse master election going.

If problems persist, turn of UFW firewall with this command: ```
sudo ufw disable
```just for a time, to see whether your samba config for UFW was correct.

If you're trying to connect to the share [myfiles] from windows by mapping a network share as a mapped drive, remember you've imposed authentication in Linux by the line "guest ok = no", so if problems persist, change that line pro tem to "guest ok = yes" just to test if you have an authentication problem.

Reference: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

PS: This assumes you haven't set vista to look for a wins server, that you've left vista correctly configured for normal mode communications (broadcast name resolution).

---

### Post by Iowan on 2009-08-12
In case it helps:
[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

---

