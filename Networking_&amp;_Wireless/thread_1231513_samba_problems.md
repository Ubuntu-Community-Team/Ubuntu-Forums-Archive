---
title: "samba problems"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by dagobert39 on 2009-08-04
I installed Ubuntu 9 on VMWare Fusion residing on an Intel iMac. In Ubuntu I installed Samba as required. The networks of the Mac and the Ubuntu guest are bridged.

When clicking the network icon in the file browser in Ubuntu, I see both the Mac and the Ubuntu servers. However, doubleclicking on either icon, it says shares cannot be mounted. Can somebody give me a hint about what might be wrong. Please note I am a beginner in the Unix business. I enclose my smb.conf file:

QUOTE

[global]
    ; General server settings
    netbios name = Ubuntu
    server string =
    workgroup = arnold
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 	SO_SNDBUF=8192
    interfaces = lo,eth0
    bind interfaces only = true	
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
    path = /home/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = helmut
    force group = arnold

UNQUOTE

Thanks in advance for any help

---

### Post by latev on 2009-08-04
Just some quick ideas:
1) Check that all the samba stuff is installed 

2) check your firewall

3) check your permissions

---

### Post by dagobert39 on 2009-08-05
I checked your points 1 and 2, seem to be in order. After inserting correct IP numbers in the host lists I managed to see the shares in the Ubuntu server, however, opening the shares wasn't possible. I gave what I thought was the correct Samba password, but no luck. When doubleclicking on the icon of the Mac server nothing came although I marked directories on the Mac for file sharing.

What I noticed was that my PW file is in the /etc/directory. Should it be in the /etc/samba/directory?

Thanks in advance.

---

### Post by latev on 2009-08-05
what password file are you talking about? the passwd file in Linux lives in etc

Also when debugging issues like the one you're having I always try to simplify things as much as possible. 

So I would suggest you remove all your password protected shares, actually just implement a single share for the whole world to see and make sure you can access it. and go from there

also flush your logs try restarting smbd and nmbd, check the logs again

---

### Post by dagobert39 on 2009-08-07
Hi Latev,

thanks for the reply, but I still seem to have a password problem. Here is what happens:

when I open the network browser, all machines appear on the list, namely the samba server called ubuntu, the mac plus a windows machine which is attached to the mac by wired network. Doubleclicking on either mac or pc opens up the correct shares on those machines. Doubleclicking on Ubuntu (the samba server) shows all the shares correctly. However, in trying to open one of the shares, the password dialogue appears. I fill in the correct password, and the password dialogue keeps coming back again. When I click cancel, it says shares cannot be mounted, end of story. Also, I cannot connect from the mac nor from the pc to the samba server.

I think we can narrow the problem down to a pw problem with the server?

Thanks in advance for your help.

---

### Post by latev on 2009-08-07
Well, it does make sense yes

Again - I'd suggest you examine the log files and see why it is rejecting the valid password. Also you may try starting the Samba in debug mode and monitor what it is doing in real time. Can you login to the system using the same samba account?

Actually just to be 100% sure that it's a pass issue - create a nonpass share and make sure it works perfectly, then you'll know for sure!

---

### Post by dmizer on 2009-08-07
Take a look at the 6th link in my sig.

---

