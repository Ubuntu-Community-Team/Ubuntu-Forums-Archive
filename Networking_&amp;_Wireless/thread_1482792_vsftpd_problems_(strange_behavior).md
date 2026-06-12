---
title: "vsftpd problems (strange behavior)"
date: 2010-05-13
forum: Networking &amp; Wireless
---

### Post by clblanchard on 2010-05-13
Hello all.  I have been having some problems setting up vsftpd.  My config files is as follows:

#```
 Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
listen_port=5000
pasv_address=an.example.com
pasv_addr_resolve=YES
accept_timeout=1800
anonymous_enable=NO
pasv_min_port=5001
pasv_max_port=5002
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
chown_uploads=YES
chown_username=chris
ftpd_banner=Welcome to Chris's FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp

```

I can connect from a Windows 7 vm with filezilla.  I can connect from my wife's laptop using filezilla (also running Windows 7).  I can connect from my school's network from my laptop using PuTTY as a proxy with filezilla.  But my brother can't connect from his house in another state.  I have even tried ssh tunneling through PuTTY with him but it just won't work. He can connect to the ssh session (ie. he sees the terminal and can issue commands) but it won't work as a proxy. He is behind a wireless router and I was wondering if, because of the ports I have chosen, does he need to forward anything?  I am at my wits end with this.  I have been searching the forums and I think I googled the entire internet... twice.  :confused:

---

### Post by clblanchard on 2010-05-16
bump

---

