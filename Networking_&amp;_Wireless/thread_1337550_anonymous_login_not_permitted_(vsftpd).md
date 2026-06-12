---
title: "anonymous login not permitted (vsftpd)"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by cguy on 2009-11-25
vsftpd wants me to enter a username and a password, although I enabled anonymous access.
```

george@george-desktop:/media$ ftp MY_IP
Connected to MY_IP.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 50 allowed.
220-Local time is now 22:41. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Name (MY_IP:inginerie): anonymous
331 User anonymous OK. Password required
Password:
530 Login authentication failed
Login failed.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 
```


the config file:
```

listen=YES
anonymous_enable=YES
local_enable=YES
dirmessage_enable=YES
ls_recurse_enable=YES
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
anon_root=/media/sda4/share/muzica
no_anon_password=YES
```
I tried all sorts of combinations but to no avail.
What can I do about it?

---

