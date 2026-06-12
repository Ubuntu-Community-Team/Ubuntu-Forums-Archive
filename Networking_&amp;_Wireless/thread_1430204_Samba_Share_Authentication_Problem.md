---
title: "Samba Share Authentication Problem"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by cr.santini on 2010-03-15
Hi guys

I have the follow environment


PDC SAMBA + OPEN LDAP (ubuntu 9.04)
Linux (File Servers) + Windows machines
all working well

I'm trying to set up a share drive on my new server using ubuntu 9.10 with samba (v 3.4) and ldapclient and the shares are not working when I defined Valid Users for share folders, that keep me ask me about my user and password, on the logs I have:

 [2010/03/15 10:24:10,  1] smbd/service.c:676(make_connection_snum)
  create_connection_server_info failed: NT_STATUS_ACCESS_DENIED


This is my smb.conf

[global]
        workgroup = FLOWCONNECT
        server string = OSLO SAMBA FILE SERVER
        netbios name = OSLO

        #log options
        log level = 1
        #log level = acls:10
        log file = /var/log/samba/%m.log

        #log specific user
        #include = /etc/samba/smb.conf.%m


        max log size = 500
        syslog = 0
        ldap admin dn           = cn=admin,dc=flowconnect,dc=com
      
       wins server = 172.16.0.200
       socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

        #misc from TOKIO (PDC)
        security = domain
        dns proxy = no

[H_DRIVE]
        comment = User area
        path = /usr/local/samba/H_DRIVE
        read only = no
        browseable = no
        guest ok = no
        valid users = +"Domain Users"
        create mask = 0660
        directory mask = 0770

the machine are on the domain already
libnss-ldap installed
getent passwd and group is working fine
/usr/local/samba/H_DRIVE with permission for Domain Users Group



I have the same set up on my File Server (Ubuntu 9.04) which use samba 3.3 is working  fine. Someone know if has some different setting between samba 3.3 (ubuntu 9.04) and samba 3.4 (ubuntu 9.10) that could cause this problem ? 


Tks in advance

---

### Post by cr.santini on 2010-03-18
someone ?

---

