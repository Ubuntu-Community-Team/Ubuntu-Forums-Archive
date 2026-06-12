---
title: "vsftpd help!"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by crash893 on 2009-05-11
Hi all

I have a 8.04ltr release of unbuntu

I have installed vsftpd and I can start and stop it but i don't seem to be able to get to it from outside the building


1) i have a biz class broadband connection from comcast
2) i have a linksys wrv200 router that has port 21 forwarded to 192.x.x.40 ( the ip of the box)

3) This is a copy of my conf file


listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=ftpuser
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp

4) the permissions on the /home/ftp server are

drwxrwxrwx  3 rbarbrow      ftpuser       4096 2009-05-11 11:08 ftp




When i get try to log on useing cute ftp or fillizilla It won't let me log on ( ill cut and paste error logs in a second)


Does anyone have any idea?



edit add

sv_min_port=31000
pasv_max_port=32000

---

### Post by crash893 on 2009-05-13
anyone?

---

### Post by superprash2003 on 2009-05-13
not sure about vsftpd , but you could try using gproftpd , which has a GUI , it would easier to setup an ftp server

---

### Post by crash893 on 2009-05-13
I'll give that a try

Is it a package i can just get or do i have to find it and download it?

---

### Post by LiQuidAiR on 2009-05-13
help for vsftpd seems to be lost or never written.  Even the how to's from the author don't work.  After trial and error I was able to fix mine and make it work outside the network.  If you're still interested I'll try and help you.

---

### Post by crash893 on 2009-05-14
I am very intrested. I only have access to the branch office in person once or twice a week. I do most everything else thorugh putty so i have decided to stick with vsftpd.

Im starting to wonder if there is a internal firewall ( on the unbuntu box) 

how can i tell and if its enabled how can i open the ports i need?

---

### Post by LiQuidAiR on 2009-05-14
First, what type of messages are you getting from FileZilla?

---

### Post by crash893 on 2009-05-14
the problem seemed to be that i did not have the passive ports set


i needed to add something to the portforwarding on the router and then add

to the config file
pasv_min_port=31000
pasv_max_port=32000


listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=ftpuser
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/0-samba/ftp
pasv_min_port=31000
pasv_max_port=32000
ftpd_banner=MARKON FTP SERVER! AUTHORIZED PERSONNEL ONLY


and thanks to Mr.LiQuidAiR for all of his help

---

### Post by LiQuidAiR on 2009-05-14
Boy, whoever helped you on that must have been a really smart person :)

---

