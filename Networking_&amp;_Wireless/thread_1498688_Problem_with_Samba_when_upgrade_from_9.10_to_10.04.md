---
title: "Problem with Samba when upgrade from 9.10 to 10.04"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by wahyabiantara on 2010-06-01
Hello,

I have a problem with sharing /var/www folder using samba when i upgrade the ubuntu server 9.10 to 10.04. Before the sharing system was working fine and then when the update is finish, suddenly the sharing system is not work properly.

I try to access the server using Windows Vista. I have try to modify some configuration in smb.conf file and i still have no luck.

I follow [this instruction]("http://ubuntuforums.org/showthread.php?t=202605") to reconfigure the Samba and this is my smb.conf file when i write testparm using terminal, and i still have no luck.

[global]
        workgroup = BITS
        netbios name = WEBSERVER
        server string =
        null passwords = Yes
        username map = /etc/samba/smbusers
        syslog only = Yes
        announce version = 5.0
        name resolve order = hosts wins bcast
        socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192                           SO_SNDBUF=8192
        printcap name = CUPS
        wins support = Yes

[print$]
        path = /var/lib/samba/printers
        write list = root
        create mask = 0664
        directory mask = 0775
        guest ok = Yes

[printers]
        path = /tmp
        guest ok = Yes
        printable = Yes
        browseable = No
        browsable = No

[www]
        path = /var/www/
        force user = userftp
        force group = www-data
        read only = No
        create mask = 0644

Could somebody please help me how to fix the problem. I am a new Linux User and have to learn much thing.

Thanks

---

### Post by wahyabiantara on 2010-06-01
any suggestion please

---

### Post by wahyabiantara on 2010-06-02
It solved now. the batch shell to restart Samba is changed. Before it used

```
/etc/init.d/samba restart
```

and then i try to restart it using this

```
/etc/init.d/smbd restart
```

And the samba work fine

---

