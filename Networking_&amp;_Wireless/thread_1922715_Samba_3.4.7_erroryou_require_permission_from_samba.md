---
title: "Samba 3.4.7 error:you require permission from sambaserver to make changes"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by Ginkel on 2012-02-09
Dear all,

I have run into a problem I cannot seem to solve. My company uses Ubuntu 10.04 virtual servers with samba (3.4.7) and active domain authentication through kerberos. Only 1 share per user is shared - which is mounted either on Windows XP or Windows 7, we have a mix of both and the problem occurs at both - but when they try to modify something in their share windows displays the following error message:

You need permission to perform this action
You require permission from <sambaserver>\<username> to make changes to this file

The username is the same windows username used to connect to the share in the first place. The samba configuration looks sane, and Linux directory permissions are also OK. Does anyone happen to know where I might be slipping up? I have masked the few parts in the configuration for security reasons, just hostnames and such.

**smb.conf**
```

# Samba config file created using SWAT
# from 127.0.0.1 (127.0.0.1)
# Date: 2010/07/01 11:47:42

[global]
        workgroup = OUR
        realm = OUR.DOMAIN.COM
        server string = %h
        security = ADS
        password server = activedomainserver
        idmap backend = tdb
        idmap uid = 9000-9999
        idmap gid = 9000-9999
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        unix extensions = No
        load printers = No
        disable spoolss = Yes
        show add printer wizard = No
        local master = No
        dns proxy = No
        ldap ssl = no
        panic action = /usr/share/samba/panic-action %d
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes
        winbind refresh tickets = Yes
        invalid users = root

[homes]
        comment = Local home accessed by %U
        path = /localhome/%S
        read only = No
        map archive = No
        force create mode = 0100
        browseable = No

[rootdir]
        path = /

```

/etc/krb5.conf
```


[libdefaults]
        default_realm = OUR.DOMAIN.COM
        clockskew = 300
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

[realms]
        our.domain.com = {
                kdc = activedomainserver
                default_domain = OUR.DOMAIN.COM
                admin_server = activedomainserver
        }

[domain_realm]
        .OUR.DOMAIN.COM = OUR.DOMAIN.COM

[appdefaults]
    pam = {
debug = true
            ticket_lifetime = 10h
            renew_lifetime = 9h
            forwardable = true
            proxiable = false
            retain_after_close = false
            minimum_uid = 0
            try_first_pass = true
    }

[logging]
    default = FILE:/var/log/krb5.log

[login]
        krb4_convert = true
        krb4_get_tickets = false

```

pam.d
```

/etc/pam.d/samba

@include common-auth
@include common-account
@include common-session


/etc/pam.d/common-auth

auth    sufficient      pam_krb5.so ccache=/tmp/krb5cc_%u
auth    sufficient      pam_unix.so likeauth nullok use_first_pass
auth    required        pam_deny.so


/etc/pam.d/common-account

account required        pam_unix.so
account [default=bad success=ok user_unknown=ignore service_err=ignore system_err=ignore] pam_krb5.so


/etc/pam.d/common-session

session required        pam_unix.so
session required        pam_mkhomedir.so skel=/etc/skel/ umask=0077


```

When I run testparm -s, it doesn't show any error:
```


testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[rootdir]"
Loaded services file OK.
Server role: ROLE_DOMAIN_MEMBER
[global]
        workgroup = OUR
        realm = OUR.DOMAIN.COM
        server string = %h
        security = ADS
        password server = activedomainserver
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        unix extensions = No
        load printers = No
        disable spoolss = Yes
        show add printer wizard = No
        local master = No
        dns proxy = No
        ldap ssl = no
        panic action = /usr/share/samba/panic-action %d
        idmap uid = 9000-9999
        idmap gid = 9000-9999
        winbind enum users = Yes
        winbind enum groups = Yes
        winbind use default domain = Yes
        winbind refresh tickets = Yes
        invalid users = root

[homes]
        comment = Local home accessed by %U
        path = /localhome/%S
        read only = No
        force create mode = 0100
        map archive = No
        browseable = No
        browsable = No

[rootdir]
        path = /

```

---

### Post by Ginkel on 2012-02-13
Does anyone happen to know how to fix this problem?

---

### Post by IraBa on 2012-04-19
I had a similar error and a simple line fixed it for me, either in global or the share config:

```
writable = yes
```Seems readonly = no is not enough sometimes.

---

