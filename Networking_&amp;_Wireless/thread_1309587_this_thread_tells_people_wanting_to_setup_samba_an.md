---
title: "this thread tells people wanting to setup samba and having probs with it how to do it"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
this is a thread to help people setup a decent samba server

[global]
    workgroup = put your workgroup or domain name here
    netbios name = put your servers name here
    server string = %h server (Samba, Ubuntu)
    update encrypted = Yes
    map to guest = Bad User
    null passwords = Yes
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    deadtime = 5
    socket options = SO_KEEPALIVE SO_REUSEADDR SO_BROADCAST TCP_NODELAY IPTOS_LOWDELAY IPTOS_THROUGHPUT
    add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
    add machine script = sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false %u
    logon script = logon.cmd
    logon drive = S:
    domain logons = Yes
    domain master = Yes
    dns proxy = No
    wins support = Yes
    time offset = 5
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    winbind trusted domains only = Yes
        name resolve order = lmhosts wins bcast host

[homes]
    comment = My Documents
    read only = no
    create mask = 0700
    directory mask = 0700
    browseable = yes
        guest ok = no

[netlogon]
    comment = Network Logon Service
    path = /srv/samba/netlogon
    guest ok = Yes
    share modes = No

delete everything in smb.conf and paste this in and modify it to your needs

you will need these packages as a minimum so open up a terminal and paste this in

sudo apt-get install samba smbclient samba-docs webmin swat

for swat (samba web administration tool goto localhost:901 in firefox and for webmin go to localhost:10000 in firefox) 

also please could you post any info if anything here is wrong

---

### Post by headvampyre@hotmail.co.uk on 2009-11-01
this is a thread to help people setup a decent samba server

[global]
    workgroup = put your workgroup or domain name here
    netbios name = put your servers name here
    server string = %h server (Samba, Ubuntu)
    update encrypted = Yes
    map to guest = Bad User
    null passwords = Yes
    obey pam restrictions = Yes
    passdb backend = tdbsam
    pam password change = Yes
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    deadtime = 5
    socket options = SO_KEEPALIVE SO_REUSEADDR SO_BROADCAST TCP_NODELAY IPTOS_LOWDELAY IPTOS_THROUGHPUT
    add user script = /usr/sbin/adduser --quiet --disabled-password --gecos "" %u
    add machine script = sudo /usr/sbin/useradd -n -g machines -c Machine -d /var/lib/samba -s /bin/false %u
    logon script = logon.cmd
    logon drive = S:
    domain logons = Yes
    domain master = Yes
    dns proxy = No
    wins support = Yes
    time offset = 5
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    winbind trusted domains only = Yes
        name resolve order = lmhosts wins bcast host

[homes]
    comment = My Documents
    read only = no
    create mask = 0700
    directory mask = 0700
    browseable = yes
        guest ok = no

[netlogon]
    comment = Network Logon Service
    path = /srv/samba/netlogon
    guest ok = Yes
    share modes = No

delete everything in smb.conf and paste this in and modify it to your needs

you will need these packages as a minimum so open up a terminal and paste this in

sudo apt-get install samba smbclient samba-docs webmin swat

for swat (samba web administration tool goto localhost:901 in firefox and for webmin go to localhost:10000 in firefox) 

also please could you post any info if anything here is wrong

---

### Post by cariboo on 2009-11-01
Please don't double post, I have merged your two threads.

---

