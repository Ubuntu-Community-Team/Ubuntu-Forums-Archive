---
title: "Windows Server 2008 and samba/kerberos/winbind"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by phantome on 2009-08-06
Hi 

I have been struggeling with Samba, kerberos and winbind for a while.

I have a Windows server 2008 as domain controller. I want to connect Ubuntu 9.04 with samba(3.3.2) as a file server. This works great with my old domain controller ( windows 2000 server )
But when i connect to my new DC it does not work.

1. net ads join domain -U administrator = ok
2. wbinfo -u = ok
3. wbinfo -g = ok
4. wbinfo -t = hangs for a couple of minutes and fails ( checking the trust secret via RPC calls failed - could not check secret ) There is no error code.
As long as wbinfo -t hangs the winbind log gets a lot of:

> -----
2009/08/06 11:00:01,  1] libsmb/clikrb5.c:ads_krb5_mk_req(686)
  ads_krb5_mk_req: krb5_get_credentials failed for SERVER$@DOMAIN (Cannot resolve network address for KDC in requested realm)
[2009/08/06 11:00:01,  1] libsmb/cliconnect.c:cli_session_setup_kerberos(624)
  cli_session_setup_kerberos: spnego_gen_negTokenTarg failed: Cannot resolve network address for KDC in requested realm
----- 

Kinit is successfull, result of klist:

> -----
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: user@REALM

Valid starting     Expires            Service principal
08/06/09 14:43:21  08/07/09 00:43:24  krbtgt/REALM@REALM
        renew until 08/07/09 14:43:21


Kerberos 4 ticket cache: /tmp/tkt0
-----


Anyone got any clue what is wrong ?

I'm using the following cofiguration

smb.conf

> -----
[global]
        workgroup = DOMAIN
        realm = REALM
        server string = Server 
        security = ADS
        obey pam restrictions = Yes
        pam password change = Yes
        username map = /etc/samba/user.map
        log file = /var/log/samba/samba.log
        socket options = TCP_noDELAY SO_RCVBUF=8192 SO_SNDBUF=8192
        printcap name = /etc/printcap
        local master = No
        domain master = No
        dns proxy = No
        preload = global homes printers
        default service = homes
        idmap uid = 10000-60000
        idmap gid = 10000-60000
        template homedir = /home/%U
        template shell = /bin/bash
        winbind separator = /
        winbind cache time = 15
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes
        valid users = "@DOMAIN/Domain Users", @DOMAIN/Personal
        admin users = DOMAIN/Administrator
        hosts allow = 192.168.168.0/255.255.255.0, 192.168.170.0/255.255.255.0, 127.
        hosts deny = 0.0.0.0/0.0.0.0

[homes]
        comment = Home Directory
        valid users = "@DOMAIN/Domain Users"
        read only = No
        browseable = No

[users]
        comment = All Home Directories
        path = /home
        valid users = "@DOMAIN/Domain Users"
        read list = "@DOMAIN/Domain Users"
        write list = "@DOMAIN/Domain Users"
        read only = No
        browseable = No
-----


Krb5.conf ( some is made after testing likewise-open ) 

> -----
[logging]
        default = FILE:/var/log/krb5.log
[libdefaults]
        krb4_config = /etc/krb.conf
        krb4_realms = /etc/krb.realms
        kdc_timesync = 1
        ccache_type = 4
        forwardable = true
        proxiable = true
        v4_instance_resolve = false
        v4_name_convert = {
                host = {
                        rcmd = host
                        ftp = ftp
                }
                plain = {
                        something = something-else
                }
        }
        fcc-mit-ticketflags = true
        default_tgs_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        default_tkt_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        preferred_enctypes = RC4-HMAC DES-CBC-MD5 DES-CBC-CRC
        dns_lookup_kdc = true

[realms]
        REALM = {
                kdc = server.realm
                admin_server = server.realm:749
                default_domain = realm
        }

[domain_realm]
        .realm = REALM
        realm = REALM

[login]
        krb4_convert = true
        krb4_get_tickets = false

[appdefaults]
        pam = {
                debug = true
                ticket_lifetime = 36000
                renew_lifetime = 36000
                forwardable = true
                }
-----

nsswitch.conf

> -----
passwd:         compat winbind
group:          compat winbind
shadow:         compat

hosts:          files dns mdns4_minimal [NOTFOUND=return] mdns4
+++
-----

pam ( standard pam files with the following added )

> -----
Name: Winbind authentication
Default: yes
Priority: 255
Auth-Type: Primary
Auth:
        [success=end default=ignore]    pam_winbind.so krb5_auth krb5_ccache_type=FILE try_first_pass
Auth-Initial:
        [success=end default=ignore]    pam_winbind.so krb5_auth krb5_ccache_type=FILE
Account-Type: Primary
Account:
        [success=end new_authtok_reqd=done default=ignore]      pam_winbind.so
Account-Initial:
        [success=end new_authtok_reqd=done default=ignore]      pam_winbind.so
Session-Type: Additional
Session:
        required pam_mkhomedir.so umask=0022 skel=/etc/skel
Session-Initial:
        required pam_mkhomedir.so umask=0022 skel=/etc/skel
-----

---

### Post by phantome on 2009-08-19
No respons, so i tried downgrading to Ubuntu 8.04 with samba 3.0.28a and now it works.

---

