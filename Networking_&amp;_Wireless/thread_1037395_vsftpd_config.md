---
title: "vsftpd config"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by terry f on 2009-01-11
I am using an old laptop as an server.  I have setup vsftpd and it works grate.  I am using it as a media server, and it is just me and my family on it so security is not really a concern.  But what I would like to do is make it if you sign it as an user that is puts you in your own folder.  Right now it puts you in your home folder, but I want to have it be a external hard drive.  Does any one have any ideas on how best to do this?

below is my config file:
```
# Put in /etc/vsftpd.conf
# Don't forget to change samurai into your local username
listen=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES

anon_other_write_enable=YES

dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chown_uploads=YES
chown_username=terry
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
anon_root=/home/ftp
chroot_local_user=YES

```

---

### Post by albinootje on 2009-01-11
> **terry f said:**
>  Right now it puts you in your home folder, but I want to have it be a external hard drive.


Do the users need other things in their home directory or do they only use their home directory as ftp users ?

You can test changing their default home directory to the mountpoint of the external drive.
What filesystem does the drive have ?
You might need to fiddle with permissions then.

Another idea is to use the "mount --bind" option.
For example :
```

sudo mkdir /home/your_user/disk
sudo mount /media/your_external_disk /home/your_user/disk --bind

```
After that the ftp user (named your_user in the example) should see a directory called "disk" which shows the content of the external disk.

---

