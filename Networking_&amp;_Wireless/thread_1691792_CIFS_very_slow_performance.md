---
title: "CIFS very slow performance"
date: 2011-02-20
forum: Networking &amp; Wireless
---

### Post by soulreaver1 on 2011-02-20
Hi,
I have a problem with slow CIFS performance. Network share is shared from my windows 7 and the client is Ububntu 10.04 x64. Transfer speed is about 500kb/s - 1MB/s on wifi (ubuntu client) and 5 MB/s (windows client).

Share is mounted like this:
```
//192.168.1.10/Music    /media/Music        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
```

extract from samba.log:

```
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/server.c:285:binary_smbd_main()]
samba version 4.0.0alpha9-GIT-9733816 started.
Copyright Andrew Tridgell and the Samba Team 1992-2009
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/server.c:366:binary_smbd_main()]
samba: using 'standard' process model
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [kdc: no KDC required in standalone configuration]
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [NT_STATUS_CANT_ACCESS_DOMAIN_INFO]
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [kccsrv: no KCC required in standalone configuration]
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [ldap_server: no LDAP server required in standalone configuration]
[Tue Feb 15 19:16:17 2011 CET, 0 lib/socket/interface.c:230:load_interfaces()]
WARNING: no network interfaces found
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [nbtd: no network interfaces configured]
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/service_stream.c:332:stream_setup_socket()]
Failed to listen on 0.0.0.0:445 - NT_STATUS_ADDRESS_ALREADY_ASSOCIATED
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [Failed to startup smb server task]
[Tue Feb 15 19:16:17 2011 CET, 0 lib/socket/interface.c:230:load_interfaces()]
WARNING: no network interfaces found
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [cldapd: no network interfaces configured]
[Tue Feb 15 19:16:17 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [dreplsrv: no DSDB replication required in standalone configuration]
[Tue Feb 15 20:14:54 2011 CET, 0 smbd/server.c:117:sig_term()]
Exiting pid 1118 on SIGTERM
[Tue Feb 15 20:14:54 2011 CET, 0 smbd/server.c:112:sig_term()]
[Tue Feb 15 20:14:54 2011 CET, 0 smbd/server.c:117:sig_term()]
SIGTERM: killing children
Exiting pid 1112 on SIGTERM
[Tue Feb 15 20:14:54 2011 CET, 0 smbd/server.c:117:sig_term()]
Exiting pid 1101 on SIGTERM
[Tue Feb 15 20:14:54 2011 CET, 0 smbd/server.c:117:sig_term()]
Exiting pid 1110 on SIGTERM
[Tue Feb 15 20:14:56 2011 CET, 0 smbd/server.c:285:binary_smbd_main()]
samba version 4.0.0alpha9-GIT-9733816 started.
Copyright Andrew Tridgell and the Samba Team 1992-2009
[Tue Feb 15 20:14:57 2011 CET, 0 smbd/server.c:366:binary_smbd_main()]
samba: using 'standard' process model
[Tue Feb 15 20:14:57 2011 CET, 0 smbd/service_stream.c:332:stream_setup_socket()]
Failed to listen on 0.0.0.0:445 - NT_STATUS_ADDRESS_ALREADY_ASSOCIATED
[Tue Feb 15 20:14:57 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [Failed to startup smb server task]
[Tue Feb 15 20:14:57 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [kdc: no KDC required in standalone configuration]
[Tue Feb 15 20:14:57 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [ldap_server: no LDAP server required in standalone configuration]
[Tue Feb 15 20:14:57 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [kccsrv: no KCC required in standalone configuration]
[Tue Feb 15 20:14:57 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [NT_STATUS_CANT_ACCESS_DOMAIN_INFO]
[Tue Feb 15 20:14:57 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [dreplsrv: no DSDB replication required in standalone configuration]
[Tue Feb 15 20:14:57 2011 CET, 0 smbd/service_task.c:36:task_server_terminate()]
task_server_terminate: [cldap_server: no CLDAP server required in standalone configuration]
[Tue Feb 15 20:36:07 2011 CET, 0 smbd/server.c:117:sig_term()]
[Tue Feb 15 20:36:07 2011 CET, 0 smbd/server.c:117:sig_term()]
Exiting pid 2682 on SIGTERM
Exiting pid 2690 on SIGTERM
[Tue Feb 15 20:36:07 2011 CET, 0 smbd/server.c:117:sig_term()]
Exiting pid 2684 on SIGTERM
[Tue Feb 15 20:36:07 2011 CET, 0 smbd/server.c:117:sig_term()]
Exiting pid 2683 on SIGTERM
[Tue Feb 15 20:36:07 2011 CET, 0 smbd/server.c:112:sig_term()]
SIGTERM: killing children
[Tue Feb 15 20:36:07 2011 CET, 0 smbd/server.c:117:sig_term()]
Exiting pid 2679 on SIGTERM
```

sudo dpkg -l | grep "samba":
```
ii  python-samba                              4.0.0~alpha8+git20090912-1                            Python bindings for Samba
ii  samba                                     2:3.4.7~dfsg-1ubuntu3.3                               SMB/CIFS file, print, and login server for U
ii  samba-common                              2:3.4.7~dfsg-1ubuntu3.3                               common files used by both the Samba server a
ii  samba-common-bin                          2:3.4.7~dfsg-1ubuntu3.2                               common files used by both the Samba server a
ii  samba-ldb-tools                           4.0.0~alpha8+git20090912-1                            LDAP-like embedded database - tools
ii  samba4                                    4.0.0~alpha8+git20090912-1                            LanManager-like file server for Unix (versio
ii  samba4-common-bin                         4.0.0~alpha8+git20090912-1                            Samba 4 common files used by both the server
```

Is there any way to fix it?

---

