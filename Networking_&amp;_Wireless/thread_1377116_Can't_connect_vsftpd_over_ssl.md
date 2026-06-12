---
title: "Can't connect vsftpd over ssl"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by Geort on 2010-01-09
I'm trying to enable ssl in vsftpd but seems to be imposible. My .conf file: 

anon_world_readable_only=NO
anonymous_enable=NO
chroot_local_user=YES
guest_enable=YES
guest_username=ftp
hide_ids=YES
listen=YES
local_enable=YES
max_clients=100
max_per_ip=3
nopriv_user=ftp
pasv_enable=YES
pasv_addr_resolve=YES
pasv_min_port=40000
pasv_max_port=40100
session_support=YES
use_localtime=YES
user_config_dir=/etc/vsftpd/users
local_root=/home/ftp
userlist_enable=YES
userlist_file=/etc/vsftpd/denied_users
xferlog_enable=YES
log_ftp_protocol=YES
pam_service_name=vsftpd
anon_umask=0027
async_abor_enable=YES
connect_from_port_20=YES
dirlist_enable=YES
download_enable=YES
virtual_use_local_privs=YES
write_enable=YES
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES
force_anon_logins_ssl=NO
ssl_tlsv1=YES
ssl_sslv2=YES
ssl_sslv3=YES
rsa_cert_file=/etc/vsftpd/server.pem

If I disable ssl, all work well. But when enable it, I am able to login but not to use regular commands. For example, when I use "ls", I get this response: 

ftp> ls
500 Illegal PORT command.
ftp: bind: Address already in use

Any idea how to solve this problem?
Thanks a lot!

---

