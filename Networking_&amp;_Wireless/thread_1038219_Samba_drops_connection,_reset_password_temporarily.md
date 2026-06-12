---
title: "Samba drops connection, reset password temporarily fixes"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by v1nsai on 2009-01-12
I'm using samba to access my ubuntu host from my windows xp guest on virtualbox.  I set everything and windows is able to access my shared folders, but my connection seems intermittent, it drops in the middle of transfers to my zune and tells me my username and password don't match when I try to access the file again.  I have to reset and re-enable my samba account and password in ubuntu ('sudo smbpasswd -L -a v1nsai', then 'sudo smbpasswd -L -a v1nsai) then it works for a few more minutes.  I'm posting my smb.conf file too.  I've noticed that it makes a reference to /etc/samba/smbusers but I am not able to find that file anywhere, maybe this has something to do with it.

Can anyone a) help me solve my intermittent connection problem or b) help me set samba to public and do away with the problem altogether?  Much thanks.

```
[global]
    ; General server settings
    netbios name = v1nsai_linux
    server string =
    workgroup =TEH_RIFFELZ
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

[MyFiles]
    path = /home/v1nsai/Music
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = v1nsai
    force group = TEH_RIFFELZ
```

---

### Post by v1nsai on 2009-01-14
I've been trying to fix this for days, any help please?

---

### Post by v1nsai on 2009-01-15
pretty please?

---

### Post by superprash2003 on 2009-01-16
yea.. if you dont see the smbusers file , then just create one.. [http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html](http://www.prash-babu.com/2008/05/how-to-setup-samba-in-linux.html) .. look at step 5

---

### Post by cgeroux on 2009-03-11
I am having the same problem with ubuntu server 8.10. I have set up a share with the following:

```
[global]
  unix password sync = no
  workgroup = Avalon
  netbios name  = guenevere
  server string = Samba on %L
  security      = user

[homes]
  browseable=yes
  read only = no

[common]
  valid users=cgeroux, jparker
  browseable=yes
  read only = no
  write list=cgeroux, jparker
  path=/home/common
  force group=common

```
and I am able to connect to the drives, and map them. Then after a few days, and a reboot or two of the client machines the password and or username are no longer valid and the client fails to connect. I can fix this temporarily by doing

```
sudo smbpasswd -a cgeroux
```
and entering a new password but it still disconnects eventually. 

Some additional info: one of the users jparker has the same password as her account on the server, while cgeroux doesn't have the same password. I haven't, as of yet, noticed jparker's mapped drives disconnecting. However my impression was that ```
unix password sync = no
``` did not require these passwords to be the same.

I have read on other posts that the linux and samba passwords should be the same. Is this true? Could this fix my problem? I will try it out.

---

