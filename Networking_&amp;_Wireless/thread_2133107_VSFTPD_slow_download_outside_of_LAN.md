---
title: "VSFTPD slow download outside of LAN"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by mantas1 on 2013-04-07
[COLOR=#000000]Hello all. I have VSFTP up and ruining on ubuntu 10.04. It works great inside LAN, however when it comes to using it outside i have some problems. If i try to connect from filezila i get the listing and if i try to download it shows it will take forever to receive a file which is larger then 1mb, if one is less its ok. When i try to download from explorer i get time out error. I use passive mode, here is my vsftpd.conf:[/COLOR]
[COLOR=#000000][FONT=arial]listen=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]anonymous_enable=no[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]local_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]write_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]local_umask=022[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]dirmessage_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]xferlog_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]log_ftp_protocol=yes[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]pasv_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]virtual_use_local_privs=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]pasv_min_port=2000[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]pasv_max_port=2010[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]connect_from_port_20=NO[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]chroot_local_user=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]secure_chroot_dir=/var/run/[/FONT][/COLOR][COLOR=#000000][FONT=arial]vsf[/FONT][/COLOR][COLOR=#000000][FONT=arial]tpd[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]pam_service_name=vsftpd-[/FONT][/COLOR][COLOR=#000000][FONT=arial]virtua[/FONT][/COLOR][COLOR=#000000][FONT=arial]l[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]rsa_cert_file=/etc/ssl/certs/[/FONT][/COLOR][COLOR=#000000][FONT=arial]s[/FONT][/COLOR][COLOR=#000000][FONT=arial]sl-cert-snakeoil.pem[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]rsa_private_key_file=/etc/ssl/[/FONT][/COLOR][COLOR=#000000][FONT=arial]private/ssl-cert-snakeoil.key[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]hide_ids=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]user_config_dir=/etc/vsftp/[/FONT][/COLOR][COLOR=#000000][FONT=arial]vsf[/FONT][/COLOR][COLOR=#000000][FONT=arial]tpd_user_conf[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]dual_log_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]guest_enable=YES[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]guest_username=ftp[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]local_root=/var/vsftp[/FONT][/COLOR]
[COLOR=#000000]If i switch to active mode it does work with filzilla, but then i cant login wia explorer. Maybe somebody has any ideas?[/COLOR]

---

### Post by conradin on 2013-04-07
I think IE and browsers in general default to Active mode transfers. 
Users can modify firefox, not sure about IE to accept pasv mode connections.
some clients cant handle pasv mode, beware of it.
[http://compnetworking.about.com/cs/novellgroupwise/ht/setpassiveftpie.htm](http://compnetworking.about.com/cs/novellgroupwise/ht/setpassiveftpie.htm)

you might want to have a look at your firewall settings too.

---

### Post by mantas1 on 2013-04-07
One more thing that i noticed was if i set passiv_address to my external IP no help, but if i set it to any random ip adress 192.168.... i receive 227 entering passive mode. Server sent passive reply with with unroutable address. Using server address instead in filezilla and the download and upload works, but on explorer it still does not. I did try to disable UFW to check if it might be firewall problem but still the same result.

---

