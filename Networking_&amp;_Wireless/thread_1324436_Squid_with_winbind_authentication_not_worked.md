---
title: "Squid with winbind authentication not worked"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by ricardobarbosa on 2009-11-12
Hi, Team, 

I triyng deployment the enviroment with server proxy squid, samba, winbind and kerberos. for integration with Active Directory windows 2003. its winbind is purchased users from Active Directory. The commands wbinfo -t -u -g worked follow bellow.

```
root@srv-f2:~# wbinfo -t
checking the trust secret via RPC calls succeeded
root@srv-f2:~# wbinfo -u
luciano
roberto
....
srv-winbind
tiago
linux
root@srv-f2:~# wbinfo -g
gg_trafego
gg_almoxarifado
.....
gg_departamentopessoal
gg_notificadas
g_bloqueio
root@srv-f2:~# wbinfo -a linux%123456
plaintext password authentication succeeded
challenge/response password authentication succeeded
root@srv-f2:~#
```And authentication via ntlm_auth worked as some entries 

```
root@srv-f2:~# /usr/bin/ntlm_auth VCS/SRVMAIL --helper-protocol=squid-2.5-basic
VCS\linux 123456
ERR
VCS+linux 123456
OK
linux 123456
OK

root@srv-f2:~#

root@srv-f2:~# /usr/bin/ntlm_auth VCS/SRVMAIL --debug-level=10 --helper-protocol=squid-2.5-ntlmssp
VCS\linux 123456
[2009/11/12 17:47:45, 1] utils/ntlm_auth.c:manage_squid_ntlmssp_request(750)
BH
VCS+linux 123456
BH
linux 123456
BH

```

means that the BH code anyone know?

IP address of Active Directory the server is 192.168.0.6
The IP address of the proxy is 192.168.0.5
Domain is VCS.COM.BR

kerberos worked follow bellow

```

root@srv-f2:~# kinit administrator
Password for administrator@VCS.COM.BR:
root@srv-f2:~#
root@srv-f2:~# klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: administrator@VCS.COM.BR

Valid starting     Expires            Service principal
11/12/09 17:54:46  11/13/09 03:54:50  krbtgt/VCS.COM.BR@VCS.COM.BR
     renew until 11/13/09 17:54:46


Kerberos 4 ticket cache: /tmp/tkt0
klist: You have no tickets cached
root@srv-f2:~#


```following settings samba, winbind and squid

```

root@srv-f2:~# cat /etc/samba/smb.conf
[global]
        workgroup = VCS
        netbios name = %h
        server string = %h
        load printers = no
        log file = /var/log/samba/log.%m
        max log size = 500
        realm = VCS.COM.BR
        security = ADS
        auth methods = winbind
        password server = 192.168.0.6
        winbind separator = /
        encrypt passwords = yes
        winbind cache time = 15
        winbind enum users = yes
        winbind enum groups = yes
        winbind use default domain = yes
        idmap uid = 10000-20000
        idmap gid = 10000-20000
        local master = no
        os level = 233
        domain master = no
        preferred master = no
        domain logons = no
        wins server = 192.168.0.6
        dns proxy = no
        ldap ssl = no
        ntlm auth = Yes
        client NTLMv2 auth = Yes
root@srv-f2:~#
root@srv-f2:~# ls -l /var/run/samba/winbindd_privileged/f
/var/run/samba/winbindd_privileged:
total 0
srwxrwxrwx 1 root proxy 0 2009-11-12 15:58 pipe
root@srv-f2:~#
root@srv-f2:~# cat /etc/squid3/squid.conf
http_port 3128

icp_port 3130
hierarchy_stoplist cgi-bin ?

cache_access_log /var/log/squid3/access.log

cache_effective_user proxy
cache_effective_group proxy

acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320

#acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl SSL_ports port 443
acl Safe_ports port 80          # http
acl Safe_ports port 21          # ftp
acl Safe_ports port 443         # https
acl Safe_ports port 70          # gopher
acl Safe_ports port 210         # wais
acl Safe_ports port 1025-65535  # unregistered ports
acl Safe_ports port 280         # http-mgmt
acl Safe_ports port 488         # gss-http
acl Safe_ports port 591         # filemaker
acl Safe_ports port 777         # multiling http
acl CONNECT method CONNECT

auth_param ntlm program /usr/bin/ntlm_auth VCS/SRVMAIL --debug-level=10 --helper-protocol=squid-2.5-ntlmssp
auth_param ntlm children 10

auth_param basic program /usr/bin/ntlm_auth VCS/SRVMAIL --helper-protocol=squid-2.5-basic
auth_param basic children 5
auth_param basic realm Digite o LOGIN/SENHA
auth_param basic credentialsttl 2 hours
auth_param basic casesensitive off

acl autenticacao proxy_auth REQUIRED
http_access allow autenticacao

http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost

#http_access deny all
http_access allow all

http_reply_access allow all
icp_access allow all
coredump_dir /var/spool/squid3


root@srv-f2:~#


```The only error messages that appear are
```

==> /var/log/samba/log.wb-VCS <==
[2009/11/12 18:02:32, 0] nsswitch/winbindd_pam.c:winbindd_dual_pam_auth_crap(1763)
  winbindd_pam_auth_crap: invalid password length 24/260

     ==> /var/log/samba/log.wb-VCS <==
[2009/11/12 18:03:12, 0] nsswitch/winbindd_pam.c:winbindd_dual_pam_auth_crap(1763)
  winbindd_pam_auth_crap: invalid password length 24/260
[2009/11/12 18:03:12, 0] nsswitch/winbindd_pam.c:winbindd_dual_pam_auth_crap(1763)
  winbindd_pam_auth_crap: invalid password length 24/260


```I'm synchronizing the clock via ntpdate. anyone know where I'm wrong? thanks

Regards

---

### Post by ricardobarbosa on 2009-11-12
Hi,

I discovered the cause of the error I synchronize the time via ntpdate but the time zone was used the incorrect time zone Weast and it worked. The server samba+winbind have to be synchronized with respect to time.

regards

---

