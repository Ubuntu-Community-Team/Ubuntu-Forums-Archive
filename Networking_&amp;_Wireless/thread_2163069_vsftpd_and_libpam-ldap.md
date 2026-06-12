---
title: "vsftpd and libpam-ldap"
date: 2013-07-16
forum: Networking &amp; Wireless
---

### Post by 243750496 on 2013-07-16
[B]We know if you want to combine vsftpd with mysql you should install libpam-ldap first,if not you will get lack some librarys.
but after i install the libpam-ldap i found the native user cc cant login
so i do this
open a terminal and type[/B]
tail -f /var/log/auth.log
**and got this:**
Jul 13 19:44:45 thinkpad pkexec[4765]: cc:  Executing command [USER=root] [TTY=unknown] [CWD=/home/cc]  [COMMAND=/usr/lib/update-notifier/package-system-locked]
Jul 13 19:45:38 thinkpad sudo:       cc : TTY=pts/1 ; PWD=/home/cc ; USER=root ; COMMAND=/usr/sbin/service vsftpd restart
Jul 13 19:45:38 thinkpad sudo: pam_unix(sudo:session): session opened for user root by cc(uid=0)
Jul 13 19:45:38 thinkpad sudo: pam_unix(sudo:session): session closed for user root
Jul  13 19:46:17 thinkpad vsftpd: PAM unable to dlopen(pam_ck_connector.so):  /lib/security/pam_ck_connector.so: cannot open shared object file: No  such file or directory
Jul 13 19:46:17 thinkpad vsftpd: PAM adding faulty module: pam_ck_connector.so
Jul  13 19:46:17 thinkpad vsftpd: PAM unable to dlopen(pam_shells.so):  /lib/security/pam_shells.so: cannot open shared object file: No such  file or directory
Jul 13 19:46:17 thinkpad vsftpd: PAM adding faulty module: pam_shells.so
Jul  13 19:46:17 thinkpad vsftpd: PAM unable to  dlopen(pam_gnome_keyring.so): /lib/security/pam_gnome_keyring.so: cannot  open shared object file: No such file or directory
Jul 13 19:46:17 thinkpad vsftpd: PAM adding faulty module: pam_gnome_keyring.so
**so i use cp to copy the lost files,and do it again**
**then i got this**
Jul 13 19:57:56 thinkpad vsftpd: PAM adding faulty module: pam_cap.so
Jul  13 19:57:56 thinkpad vsftpd: PAM unable to dlopen(pam_shells.so):  /lib/security/pam_shells.so: failed to map segment from shared object:  Cannot allocate memory
Jul 13 19:57:56 thinkpad vsftpd: PAM adding faulty module: pam_shells.so
Jul  13 19:57:56 thinkpad vsftpd: PAM unable to  dlopen(pam_gnome_keyring.so): /lib/security/pam_gnome_keyring.so: failed  to map segment from shared object: Cannot allocate memory
Jul 13 19:57:56 thinkpad vsftpd: PAM adding faulty module: pam_gnome_keyring.so
Jul 13 19:57:56 thinkpad vsftpd: pam_unix(vsftpd:auth): check pass; user unknown
Jul  13 19:57:56 thinkpad vsftpd: pam_unix(vsftpd:auth): authentication  failure; logname= uid=0 euid=0 tty=ftp ruser=cc rhost=192.168.1.106 
Jul 13 19:58:42 thinkpad pkexec: pam_unix(polkit-1:session): session opened for user root by (uid=1000)
Jul 13 19:58:42 thinkpad pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Jul  13 19:58:42 thinkpad pkexec[2461]: cc: Executing command [USER=root]  [TTY=unknown] [CWD=/home/cc]  [COMMAND=/usr/lib/update-notifier/package-system-locked]
Jul 13 20:17:01 thinkpad CRON[2774]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 13 20:17:01 thinkpad CRON[2774]: pam_unix(cron:session): session closed for user root
Jul 13 20:27:49 thinkpad gnome-screensaver-dialog: gkr-pam: unlocked login keyring
[B]by the way the native user cc still cant log in

befor i install libpam-ldap i have typed this code
and get this
[/B]Jul 12 21:30:12 thinkpad usermod[3374]: change user 'ftp' password
Jul 12 21:30:12 thinkpad chage[3379]: changed password expiry for ftp
Jul 12 21:30:12 thinkpad chfn[3382]: changed user 'ftp' information
Jul  12 21:33:04 thinkpad sudo:       cc : TTY=pts/1 ; PWD=/home/cc ;  USER=root ; COMMAND=/bin/cp /etc/vsftpd.conf /etc/vsftpd.conf.bk
Jul 12 21:33:04 thinkpad sudo: pam_unix(sudo:session): session opened for user root by cc(uid=0)
Jul 12 21:33:04 thinkpad sudo: pam_unix(sudo:session): session closed for user root
Jul 12 21:33:17 thinkpad sudo:       cc : TTY=pts/1 ; PWD=/home/cc ; USER=root ; COMMAND=/usr/bin/gedit /etc/vsftpd.conf
Jul 12 21:33:17 thinkpad sudo: pam_unix(sudo:session): session opened for user root by cc(uid=0)
Jul 12 21:33:31 thinkpad sudo: pam_unix(sudo:session): session closed for user root
Jul  12 21:34:19 thinkpad polkitd(authority=local): Operator of  unix-session:/org/freedesktop/ConsoleKit/Session1 successfully  authenticated as unix-user:cc to gain TEMPORARY authorization for action  org.debian.apt.install-or-remove-packages for system-bus-name::1.68  [/usr/bin/python /usr/bin/software-center] (owned by unix-user:cc)
[B]

question&#65306;
1&#12289;why if i install the software i got to have problem ? 2&#12289;does it change some libraries?and when i copy the files another problem came out how can i solve it???[/B]
[U][I][B]

thanks a lot[/B][/I][/U]
in Ubuntu 13.04

---

### Post by 243750496 on 2013-07-18
Nobody???

---

