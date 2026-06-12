---
title: "Samba works from LAN cable but not from WIFI"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by chadk on 2009-01-27
I'm running ubuntu 8.10 on a laptop and I can see my windows shares when I have eth0 (LAN cable) plugged in but when I unplug it and the laptop switches to WIFI I can no longer see the windows shares...
When I trye smbclient //COMPUTERNAME/SHARE I get: "Connection to COMPUTER failed (Error NT_STATUS_ACCESS_DENIED)"  ?  

All other network stuff functions... internet, ping, etc.,  just no samba...

```

[global]
    ; General server settings
    netbios name = ROAMER
    server string =
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = bcast hosts wins

    wins support = no

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

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
    path = /media/samba/
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
    force user = chad
    force group = chad

```

---

### Post by chadk on 2009-01-27
Strange, I went into the WLAN connection and changed nothing.. I saved it and it started seeing the Samba shares.
I went to each tab and opened the routes and confirmed it was empty.  Then I closed and saved it and poof. Samba shares.

---

### Post by kraymore on 2009-04-26
I am wondering, you mention going into routes and making sure its empty.  where is this ?  what do you mean by routes ? 

I have the same issue on Jaunty.  Samba only works when connected by cable, not wifi, and would like to fix it.

thank you

---

