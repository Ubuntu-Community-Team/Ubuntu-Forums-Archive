---
title: "Vsftp Error"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by mtbiker on 2006-06-12
Hello,
I'm new to this so bear with me. I've running Ubuntu 6.0.6. I just installed vsftpd and edited my vsftpd.conf file to read the following




```
# Standalone mode 
listen=YES 
max_clients=200 
max_per_ip=4 
# Access rights 
anonymous_enable=YES 
local_enable=NO 
write_enable=YES 
anon_upload_enable=YES 
anon_mkdir_write_enable=NO 
anon_other_write_enable=NO 
anon_umask=077 
# Security 
anon_world_readable_only=YES 
connect_from_port_20=YES 
hide_ids=YES 
pasv_min_port=50000 
pasv_max_port=60000 
# Features 
xferlog_enable=YES 
ls_recurse_enable=NO 
ascii_download_enable=NO 
async_abor_enable=YES 
# Performance 
one_process_model=YES 
idle_session_timeout=120 
data_connection_timeout=300 
accept_timeout=60 
connect_timeout=60 
anon_max_rate=50000
```



All I'm trying to do is get anonymous access working so I can upload and download. When ever I try to upload I get



```
ftp> put book-toc.html local: book-toc.html remote: book-toc.html 
200 PORT command successful. 
Consider using PASV. 
553 Could not create file.
```


Could not create file? Any idea's what I'm doing wrong?

Thanks a million!!!

---

