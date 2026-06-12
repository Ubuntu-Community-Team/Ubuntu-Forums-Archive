---
title: "Problems joining Active Directory (DNS update failed)"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by World_emp on 2013-04-30
Server: Windows 2008 R2
Client: Ubuntu 12.04

I'm trying to add my Ubuntu client to an Active Directory domain controller, but I always get one of two errors:

Error #1
```
sudo net ads join -U Administrator
Enter Administrator's password:
kinit succeeded but ads_sasl_spnego_krb5_bind failed: SASL bind in progress
Failed to join domain: failed to connect to AD: SASL bind in progress
```

Error #2
```
sudo net ads join -U Administrator
Enter Administrator's password:
Using short domain name -- TESTSUPSI
Joined 'VMDC1' to realm 'testsupsi.ch'
DNS Update for vmdc1.dti.supsi.ch failed: ERROR_DNS_GSS_ERROR
DNS update failed!
```

Here's a copy of my configuration files:

/etc/krb5.conf
```
    [appdefault]
    pam = {
       realm = TESTSUPSI.CH
       ticket_lifetime = 1d
       renew_lifetime = 1d
       forwardable = true
       proxiable = false
            retain_after_close = false
            minimum_uid = 2
            try_first_pass = true
            ignore_root = true
    }

    [libdefaults]
       default_realm = TESTSUPSI.CH
            default_keytab_name = FILE:/etc/krb5.keytab

    [realms]
       TESTSUPSI.CH = {
          auth_to_local = DEFAULT
       }

    [domain_realm]
       .testsupsi.ch = TESTSUPSI.CH
       testsupsi.ch = TESTSUPSI.CH

    [login]
       krb4_convert = true
       krb4_get_tickets = false


```

/etc/samba/smb.conf
```
[global]
  netbios name = VMDC1
  realm = TESTSUPSI.CH
  workgroup = TESTSUPSI
  security = ADSsudo net ads join -U Administrator
Enter Administrator's password:
Using short domain name -- TESTSUPSI
Joined 'VMDC1' to realm 'testsupsi.ch'
DNS Update for vmdc1.dti.supsi.ch failed: ERROR_DNS_GSS_ERROR
DNS update failed!
  kerberos method = system keytab
  client ldap sasl wrapping = sign
```

Any ideas how to solve them?

Thanks in advance!

---

