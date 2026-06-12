---
title: "Samba not authenticating against AD"
date: 2013-06-14
forum: Networking &amp; Wireless
---

### Post by sambaChallenged on 2013-06-14
Hi,

My goal is to have samba authenticate against AD.  I got it to the point where it works if I try accessing my shares while I'm on the server where I provisioned samba but fails on any other host.  
 
Some output:

ON THE SERVER WHERE I PROVISIONED SAMBA
```
kfrank@serverName002:~$ smbclient \\\\serverName002\\base
Enter kfrank's password: 
Domain=[domainName] OS=[Unix] Server=[Samba 3.6.3]
smb: \> 
```

ON MY MACHINE
```
kfrank@MYMACHINE:~$ smbclient \\\\serverName002\\base
Enter kfrank's password: 
session setup failed: NT_STATUS_LOGON_FAILURE

```
TRY WITH THE IP INSTEAD
```
kfrank@MYMACHINE:~$ smbclient \\\\xxx.xxx.xxx.xxx\\base
Enter kfrank's password: 
session setup failed: NT_STATUS_LOGON_FAILURE
```

SANITY CHECK
```
kfrank@MYMACHINE:~$ smbclient \\\\somerandoname\\base
Enter kfrank's password: 
Connection to somerandoname failed (Error NT_STATUS_BAD_NETWORK_NAME)

```




MY smb.conf (stuff in [] is different in my actual smb.conf)

```
[global]
        server string = Samba %v on %L
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        socket options = TCP_NODELAY
        host msdfs = No
        dns proxy = No
        panic action = /usr/share/samba/panic-action %d
        load printers = No


        security = DOMAIN
        workgroup = [myWorkgroup] 
        realm = [MyRealm]
        netbios name = [serverName002]


#       idmap uid = 10000-600000                                                                                                                                                                             
#       idmap gid = 10000-600000                                                                                                                                                                             
        wins server = [xxx.xxx.xxx.xxx]


        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes
        idmap config * : range = 10000-600000
        idmap config * : backend = tdb


#       security = User                                                                                                                                                                                      
        encrypt passwords = Yes
#       passdb backend = smbpasswd                                                                                                                                                                           
        obey pam restrictions = Yes


        guest ok = No
        restrict anonymous = 2
        map to guest = Bad User
        usershare allow guests = No


        create mask = 0664
        directory mask = 0775


        logon path = \\%i\profiles\%u
        logon drive = Z:
        logon home = \\%i\%u
        valid users = [myRealm\username, etc.]
        admin users = [myRealm\username, etc.]


[base]
        comment = Base Image Directories
        path = /export/base-images
        browseable = yes
        read only = no
[installer]
        comment = Installer Image Directories
        path = /export/installer-images
        browseable = yes
        read only = no






```





 
My nsswitch.conf

```
passwd:         files winbindgroup:          files winbind
shadow:         compat


hosts:          files dns winbind
networks:       files


protocols:      db files
services:       db files
ethers:         db files
rpc:            db files


netgroup:       nis



```

One other thing to note is that I joined AD to my server using

```
**net rpc join -U kfrank**
```

Any suggestions why AD won't auth on any other host?

Thanks

---

### Post by SeijiSensei on 2013-06-14
What do you see in the logs on the AD server?

You probably need to specify the domain as well as the username.  What happens if you include "-W domainname" in the smbclient command, where "domainname" is the name of your AD domain?

---

### Post by sambaChallenged on 2013-06-20
Sorry for the late response but here's an update.

smbclient -W did the same thing - won't authenticate properly

Tried getting a debug output on the server where I can connect vs on a machine where I can't connect and got some interesting results

$smbclient -d10 \\\\serverName002\\base

It appears as if samba is trying to use the local smb.conf file on whatever machine I happen to be on instead of the one on serverName002.  I still believe that a there is a connection to serverName002 when trying to use smbclient on a different host since a log file for that host appears on serverName002.

There's a flag for specifying an smb.conf file but I'm not sure how to use it.

Tried:

$  smbclient --configfile=serverName002:/etc/samba/smb.conf \\\\serverName002\\base

But alas it did not work.  Still trying to work on this will post results

---

### Post by SeijiSensei on 2013-06-20
Does it work if you use the server's IP address instead of its hostname?  What are you using to resolve names?

---

### Post by sambaChallenged on 2013-06-20
No dice with the IP.

When I copy over the smb.conf file on a different machine with the one I got on serverName002 it works!!!! That solution is pretty crappy tho so I copied over the smb.conf file from serverName002 to my current directory then ran

$ smbclient \\\\serverName002\\base -s smb.conf
(-s specifies the smb.conf file)

which also works.  Any way to set it up so it looks for the smb.conf file on serverName002 by default?

---

### Post by sambaChallenged on 2013-06-24
Figured it out finally. Turns out you need to specify a workgroup:

$  smbclient \\\\serverName002\\base -U kfrank -W myWorkGroup

thanks for the help seiji

---

