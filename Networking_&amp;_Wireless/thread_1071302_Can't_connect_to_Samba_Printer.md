---
title: "Can't connect to Samba Printer"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by RealG187 on 2009-02-16
I cannot connect to a Samba printer. I get 
 

CUPS Server Error
There was an error during the CUPS operation: 'client-error-not-possible'.

---

### Post by crazyness003 on 2009-02-16
Try reinstalling CUPS. That worked for me once. Or maybe your samba setup is bad. You need to give a little bit more info on how and what things are hooked up.

---

### Post by RealG187 on 2009-02-16
Here is my /etc/samba/smb.conf

> [global]
    ; General server settings
    netbios name = MIKED6
    server string =
    workgroup = WORKGROUP
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

I can connect to my Ubuntu (I can see the pritners but never tried. My printer is on my wired network and my laptop is on my wireless network. I can print when I plug my laptop into my wired network, but not from my wireless network. Using my IBM computer (bridge) that is connected to both Networks I shared my printer and am trying to print this way.

[http://img205.imageshack.us/img205/3482/icsmu9.png](http://img205.imageshack.us/img205/3482/icsmu9.png)
In that image my printer is on the Same network there that has my Xbox, Compaq, and Seanix machines. My laptop is connected to the "First Router" the one at the top where my internet comes in. I can actually get internet on my Xbox, Compaq, and Seanix by having them connected to the IBM machine which in turn connects to my wireless network where my internet comes in. I use Windows XP Internet Connection Sharing for that (don't know how to do that in Ubuntu). But now I am trying to reverse the process and instead of accessing resources (internet) on my wireless network from my wired one, I am trying to access resources (printer) on my wired network from my Wireless one.

I bought [this wireless bridge]("http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ssPageName=STRK:MEWNX:IT&item=180327444773"), if I plug that into my wired network and connect it to my Wifi would that be a better way?

---

### Post by RealG187 on 2009-02-18
I think I can print if I am wired into the same network, so I am not sure if its CUPS error...

---

### Post by mskapinski on 2009-02-18
I had problems also connecting to my printer connected to a samba share.  
1- make sure you have the correct drive. You can get this from the manufacturers site.
2- go to the system menu, administration and printing (this will start the printer configuration tool)
3- click on the new printer 
4- select WINDOWS PRINTER VIA SAMBA
5- use browse and locate the printer you want to connect to.  
6- there should be an option to use a PPD file, select it.

Heres the tricky part.  I haven't figured it out yet but each time i log in i have to manually connect to my WORKGROUP.  Once connected i can print no problems, but this was a pain. I was able to get arround this by going back and editing the printer  just created and replacing the print server name with its IP address.  That worked for me and now i dont have to manually connect to workgroup to be able to print.

---

