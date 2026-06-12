---
title: "Network problems"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by aramshiro on 2009-08-01
Helo  there Guys. If u dont mind i just want to tell some of my problem i apriciate a lot if u can helped me right.  By d way I will tell you my situation. In our office we are using windows operating system (Windows 98 & Windows Xp) We have a good network connection for both 98 and Xp. Now we try to Install ubuntu in 1 pc. Because we want to try it to be our server pc because as i heared from others for now there are no viruses developed yet in ubuntu so we want to try it for our safety. Now the problem is that when i using our windows base computer we have access in all network group also we can access file from the ubuntu pc, but when i using ubuntu pc to access files from other network group, there i encounter some problem. Its like this when i open my windows network i see all the workgroup but if i double click one of my workgroup to see other pc who are connected in dat work group i cant see anything,  the only workgroup that i can access pc's is where my ubuntu pc was joined. So dats what i want to solve. Im sry because im just a bigginer in this OS. I really apriciate your help. thx alot.

  BY D WAY THIS IS MY CONFIGURATION. PLS TELL ME IF THERE'S SOMETHING I MUST TO CHANGE OR TO PUT ANOTHER CONFIG. 

[global]
    ; General server settings
    netbios name = Dbaseserveru
    server string =  %h (Ubuntu)
    workgroup = MIS Department
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
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
  comment = read and write
  path = /home/samba
  available = yes
  browsable = yes
  public = yes
  writable = yes
  create mask = 0700
  directory mask = 0755
  force user = nobody
  force group = nogroup

    ;path = /home/samba/
   ; browseable = yes
   ; read only = no
   ; guest ok = no
   ; create mask = 0644
   ; directory mask = 0755
   ; force user = nobody
   ; force group = nogroup

[D]
  comment = read and write
  path = /home/samba
  available = yes
  browsable = yes
  public = yes
  writable = yes
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

[documents]
  comment = read and write
  path = /home/samba
  available = yes
  browsable = yes
  public = yes
  writable = yes
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

---

### Post by tsali on 2009-08-01
> **aramshiro said:**
> Helo  there Guys. If u dont mind i just want to tell some of my problem i apriciate a lot if u can helped me right.  By d way I will tell you my situation. In our office we are using windows operating system (Windows 98 & Windows Xp) We have a good network connection for both 98 and Xp. Now we try to Install ubuntu in 1 pc. Because we want to try it to be our server pc because as i heared from others for now there are no viruses developed yet in ubuntu so we want to try it for our safety. Now the problem is that when i using our windows base computer we have access in all network group also we can access file from the ubuntu pc, but when i using ubuntu pc to access files from other network group, there i encounter some problem. Its like this when i open my windows network i see all the workgroup but if i double click one of my workgroup to see other pc who are connected in dat work group i cant see anything,  the only workgroup that i can access pc's is where my ubuntu pc was joined. So dats what i want to solve. Im sry because im just a bigginer in this OS. I really apriciate your help. thx alot.

  BY D WAY THIS IS MY CONFIGURATION. PLS TELL ME IF THERE'S SOMETHING I MUST TO CHANGE OR TO PUT ANOTHER CONFIG. 

[global]
    ; General server settings
    netbios name = Dbaseserveru
    server string =  %h (Ubuntu)
    workgroup = MIS Department
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
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
  comment = read and write
  path = /home/samba
  available = yes
  browsable = yes
  public = yes
  writable = yes
  create mask = 0700
  directory mask = 0755
  force user = nobody
  force group = nogroup

    ;path = /home/samba/
   ; browseable = yes
   ; read only = no
   ; guest ok = no
   ; create mask = 0644
   ; directory mask = 0755
   ; force user = nobody
   ; force group = nogroup

[D]
  comment = read and write
  path = /home/samba
  available = yes
  browsable = yes
  public = yes
  writable = yes
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

[documents]
  comment = read and write
  path = /home/samba
  available = yes
  browsable = yes
  public = yes
  writable = yes
  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup

I appears you have created shares in the /home directory.

Samba treats the /home directory differently.

Try creating another directory in root called /shares, then create your individual shares in that folder.

Also, I'm not sure I would use the "force user" option. Simply set access to "guest = ok"

---

### Post by cariboo on 2009-08-01
Moved to Networking & wireless

---

