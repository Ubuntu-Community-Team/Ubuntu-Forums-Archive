---
title: "vsFTPd local users issues"
date: 2013-05-01
forum: Networking &amp; Wireless
---

### Post by DoubleD33D on 2013-05-01
I'm trying to share a secondary hard drive from my Ubuntu Desktop 13.04 AMD64 machine to a Windows 7 AMD64 machine. They are both on the network properly and are able to network with other services(such as synergy). Anyway, I have been googling the internet now for hours trying to figure out how to fix this. vsFTPd is installed and here is my config file
```
listen=YES#listen_ipv6=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=022
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
ftpd_banner=Very private FTP network
#deny_email_enable=YES
#banned_email_file=/etc/vsftpd.banned_emails
chroot_local_user=YES
#chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
pasv_min_port=12000
pasv_max_port=12100
```

I've check /etc/pam.d/, there is a file called vsftpd. I've tried pam_service_name=ftp. I've added my local user to the ftp group. I've tried different combinations of configs. My user is not listed in /etc/ftpusers. I have run /etc/init.d/vsftpd restart after each config change. I've tried running commands to open ports 20, 21, and the passive ports. I don't care about port forwarding because I don't want this server accessed from outside the house. I'm about to connect with Anonymous, but when I try my(or any) user the login failed. Tried using FileZilla client, and tried connecting to it in the browser. Finally I tried connecting to it with localhost and it still fails to login. Help anyone?

---

### Post by gorkypah on 2013-05-01
I have this same problem after I upgraded from Ubuntu Server 12.10 to Ubuntu Server 13.04 with vsftpd.  I have since moved from vsftpd to proftpd.

---

### Post by DoubleD33D on 2013-05-02
I found the issue. It's nothing wrong with configs or anything it's a bug in vsFTPd. This seems to work.

[https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1160372/+attachment/3661388/+files/vsftpd_3.0.2-1ubuntu1_amd64_patched.deb]("http://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1160372/+attachment/3661388/+files/vsftpd_3.0.2-1ubuntu1_amd64_patched.deb")


[https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1160372/+attachment/3661389/+files/vsftpd_3.0.2-1ubuntu1_i386_patched.deb](https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1160372/+attachment/3661389/+files/vsftpd_3.0.2-1ubuntu1_i386_patched.deb)

---

