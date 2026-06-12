---
title: "I can't configure virtual users in VSFTPd"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by simonbcn on 2011-03-27
Ubuntu 10.04 32 bits
vsftpd 2.3.4 installed from sources

```
    # cat vsftpd.conf 
    listen=YES
    anonymous_enable=NO
    local_enable=YES
    write_enable=YES
    anon_upload_enable=NO
    anon_mkdir_write_enable=NO
    connect_from_port_20=YES
    nopriv_user=ftp
    chroot_local_user=YES
    secure_chroot_dir=/usr/share/empty
    ls_recurse_enable=YES
    listen_port=1031
    log_ftp_protocol=YES
    syslog_enable=NO
    vsftpd_log_file=/var/log/vsftpd.log
    delete_failed_uploads=YES
    user_config_dir=/etc/vsftpd/user_conf
    anon_world_readable_only=NO
    anon_other_write_enable=NO
    no_anon_password=YES
    force_dot_files=NO
    guest_enable=YES
    pam_service_name=vsftpd.virtual
    virtual_use_local_privs=YES
``````
    # cat /etc/pam.d/vsftpd.virtual 
    auth       required     /lib/security/pam_userdb.so db=/etc/vsftpd/virtual_users.db
    account    required     /lib/secutiry/pam_userdb.so db=/etc/vsftpd/virtual_users.db
```I use db_load to create a simple hashed db with the following command:

    ```
db4.8_load -T -t hash -f logins /etc/vsftpd/virtual_users.db
```Well, I can login with my system user and it enters in FTP folder.
But when I try to enter with virtual user it always shows: *530 Login incorrect.*

I've tried with other tutorial ([[http://www.ubuntututorials.net/installing-vsftpd-using-text-file-for-virtual-users/]](http://www.ubuntututorials.net/installing-vsftpd-using-text-file-for-virtual-users/])) that uses *htpasswd* and *libpam-pwdfile* but it also doesn't work.

I've tried see the log files but neither shows anything. I've done several searches with "*grep -i vsftpd /var/log/**" and "*grep -i pam /var/log/**" but I don't find any clue.

---

### Post by simonbcn on 2011-03-27
Hi,
The problem was several:

   1. I hadn't installed libpam0g-dev before I compiled vsftpd.
   2. In the pam file doesn't put the db file extension.

Now it's solved.

---

