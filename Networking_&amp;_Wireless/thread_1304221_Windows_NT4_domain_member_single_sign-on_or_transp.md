---
title: "Windows NT4 domain member: single sign-on or transparent auth access windows shares"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by MarvinFS on 2009-10-29
Dear colleges, 

As far as i got it from the forums, i suppose it's working on ubuntu < 9.04?! I spent some days reading mans and forums but still no luck getting it done:

i have mintlinux7 (ubuntu 9.04)**joined to NT4 domain as a domain member.**
(i did it by net rpc join ...)
so domain users may login locally to Gnome using their domain accounts (either by domain\user or by simple user as far as i use winbind use default domain = yes)they got their homes created and all seems to work great. Also ssh local logins using domain accounts are working great.
when users open network neighborhood it shows all the servers in domain allowing to enter every server and also displays all shares on server. (i think it's anonymous smb browsing) As far as i have permissions on the servers's share i presume that on access it'll show it's contents. but it's not. nautilus only shows username\password prompt window when i wish no enter smb share (BTW it's already filled with my domain username and domain name only password is empty). When i supply correct password everything else is working just great including localized filenames and openning networked docs by openoffice.
**But SSO in not working  - please assist! **

i've tried to join AD domain (win2003 domain) with net ads join and SSO is working just great with the same settings (only settings concerting that it's AD and to use kerberos auth differs)

**system:**

mint7-test samba # uname -a
Linux mint7-test 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
UBUNTU 9.04!!!


**checks:**

mint7-test samba # wbinfo -t
checking the trust secret via RPC calls succeeded

mint7-test samba # wbinfo -D RAIL
Name              : RAIL
Alt_Name          :
SID               : S-1-5-21-433347482-382690077-1637365974
Active Directory  : No
Native            : No
Primary           : Yes

mint7-test samba # wbinfo -g
domain admins
domain guests
domain users
exchange admins

mint7-test samba # wbinfo -u
administrator
exchangesrv
guest


getent paswd
administrator:*:10706:10003::/home/RAIL/administrator:/bin/bash
exchangesrv:*:10710:10003:Exchange Server account:/home/RAIL/exchangesrv:/bin/bash
guest:*:10711:10003::/home/RAIL/guest:/bin/bash
test:*:10789:10003::/home/RAIL/test:/bin/bash
**:*:10785:10003:&#1050;&#1088;&#1072;&#1089;&#1080;&#1083;&#1100;&#1085;&#1080;&#1082;&#1086;&#1074; &#1042;&#1072;&#1083;&#1077;&#1088;&#1080;&#1081; &#1040;&#1083;&#1077;&#1082;&#1089;&#1072;&#1085;&#1076;&#1088;&#1086;&#1074;&#1080;&#1095;:/home/RAIL/**:/bin/bash

[B]
PAM modules:[/B]
```

# /etc/pam.d/common-auth - authentication settings common to all services

#added by hands
-----------
auth sufficient pam_unix.so nullok_secure
auth sufficient pam_winbind.so use_first_pass use_authtok
-----------

auth    requisite                       pam_deny.so
auth    required                        pam_permit.so
auth    optional        pam_ecryptfs.so unwrap

# /etc/pam.d/common-session - session-related modules common to all services
session [default=1]                     pam_permit.so
session requisite                       pam_deny.so
session required                        pam_permit.so
session required        pam_unix.so

#added by hands
-----------
session required  pam_mkhomedir.so umask=0022 skel=/etc/skel/
session sufficient      pam_winbind.so  use_first_pass use_authtok
------------
session optional        pam_ecryptfs.so unwrap
session optional                        pam_ck_connector.so nox11

# /etc/pam.d/common-account - authorization settings common to all services
account sufficient      pam_unix.so

#added by hands
-----------
account sufficient      pam_winbind.so user_first_pass use_authtok
-----------

account requisite                       pam_deny.so
account required                        pam_permit.so


# /etc/pam.d/common-password - password-related modules common to all services

#added by hands
-----------
password sufficient     pam_unix.so obscure sha512
password sufficient pam_winbind.so  use_first_pass use_authtok
-----------

password        requisite                       pam_deny.so
password        required                        pam_permit.so
password        optional        pam_ecryptfs.so

mint7-test samba # cat /etc/pam.d/gdm
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password


```
**mint7-test samba # cat /etc/samba/smb.conf**

```

[global]

        workgroup = RAIL
        server string = %h server (Samba, mintLinux7)
  wins support = no
  wins server = 10.0.16.200
  dns proxy = no
  name resolve order = lmhosts host wins bcast

;   bind interfaces only = yes
        log file = /var/log/samba/log.%m
        max log size = 1000
#   syslog only = no
        syslog = 0
        panic action = /usr/share/samba/panic-action %d
   security = domain
   encrypt passwords = true
   passdb backend = tdbsam
   obey pam restrictions = yes
   unix password sync = yes
#       passwd program = /usr/bin/passwd %u
#       passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    pam password change = yes
    map to guest = bad user
    domain logons = no
   socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
domain master = no
local master = no
preferred master = no
   idmap uid = 10000-20000
   idmap gid = 10000-20000
   template shell = /bin/bash
   winbind enum groups = yes
   winbind enum users = yes
template homedir = /home/%D/%U
winbind cache time = 15
winbind offline logon = yes

 # winbind separator = +

password server = *
winbind use default domain = yes
client lanman auth = yes
        usershare allow guests = yes
#        username map = /etc/samba/smbusers

[printers]
        comment = All Printers
        browseable = no
        path = /var/spool/samba
        printable = yes
;       guest ok = no
;       read only = yes
        create mask = 0700

[print$]
        comment = Printer Drivers
        path = /var/lib/samba/printers
;       browseable = yes
;       read only = yes
;       guest ok = no


[obmen]
        path = /home/user/obmen
        comment = &#1087;&#1072;&#1087;&#1082;&#1072; &#1076;&#1083;&#1103; &#1086;&#1073;&#1084;&#1077;&#1085;&#1072; &#1076;&#1086;&#1082;&#1091;&#1084;&#1077;&#1085;&#1090;&#1072;&#1084;&#1080;
;       available = yes
;       browsable = yes
        public = yes
        writable = yes

```
[B]
# /etc/nsswitch.conf[/B]

passwd:         files winbind
group:          files winbind
shadow:         files winbind

hosts:          files wins mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files dns

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by albandy on 2009-10-29
Instead of using winbind use Likewise Open, I use it and all works fine.

[http://www.likewise.com/](http://www.likewise.com/)

---

### Post by MarvinFS on 2009-10-29
Yes it's working just great but when connecting to AD based domains!!!

i need to be a **WINDOWS NT4 SERVER **based domain member with PDC on windows nt 4 server! 

as far as i know likewise dont support NT4.

---

