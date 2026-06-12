---
title: "samba pdc logon script failure"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by jocke on 2005-12-16
deerest community! :)

I have bumped into some trouble regarding setting up a logon script. Samba shares are supposed to be automatically mapped on the Win XP computer but it doesn't...

Everything else works fine, I can log on to the domain and I can reach the share 'ourshare' by browsing the network. But I can't automatically make the share available on drive I: Does anyone know what it could be?

I've followed documentation at:
[http://us3.samba.org/samba/docs/using_samba/ch04.html](http://us3.samba.org/samba/docs/using_samba/ch04.html)

Thanx! /Jocke

This is my /home/samba/netlogon/otac/logon.bat:
```
net use I: \\sunny\ourshare
```

From the smb.conf:

```
[global]
        passwd chat = *New*UNIX*password* %n\n *Retype*new*UNIX*password* %n\n *Enter*New*UNIX*password* %n\n *Retype*New*UNI
X*password* %n\n *passwd:*all* authentication*token*update*successfully*
        socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192 IPTOS_LOWDELAY
        passdb backend = tdbsam
        printing = cups
        printcap name = cups
        null passwords = yes
        domain master = yes
        encrypt passwords = yes
        passwd program = /usr/bin/passwd %u
        available = no
        wins support = true
        allow hosts = 192.168.0.0/255.255.255.240 127.0.0.1
        netbios name = sunny
        browseable = no
        server string = Sunny
        unix password sync = yes
        local master = yes
        workgroup = Informatica
        os level = 64
        security = user
        add machine script = /usr/sbin/useradd -d /dev/null -g machines -s /sbin/nologin -M %u
        logon drive = H:
        max log size = 50
        pam password change = yes
        domain logons = yes
        logon script = %g/logon.bat
        log level = 2

[homes]
        writeable = yes
        available = yes

[netlogon]
        path = /home/samba/netlogon
        writable = no
        browsable = no
        available = yes

[ourshare]
        browseable = yes
        writable = no
        write list = @otac
        path = /home/samba/ourshare
        force user = otac
        create mode = 774
        directory mode = 775
        available = yes
```

---

