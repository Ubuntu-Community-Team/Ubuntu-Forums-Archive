---
title: "ddclient, no-ip errors"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by mcc28x on 2012-08-15
Hi,

ddclient has recently started to report errors when trying to update my ip with no-ip service. The errors from syslog are:

```
WARNING:  cannot send to dynupdate.no-ip.com:443 (Bad file descriptor).
Aug 15 18:07:09 myhostname ddclient[1352]: FAILED:   updating myhostname.hopto.org: Could not connect to dynupdate.no-ip.com.
```

If I issue ```
 sudo ddclient -force

```

I get the following:

```

file /var/cache/ddclient/ddclient.cache, line 4: Invalid Value for keyword 'ip' = ''
here...my@emailaddress.com --> mypassword
syswrite() on closed filehandle GEN0 at /usr/sbin/ddclient line 1816.
Use of uninitialized value $result in numeric ne (!=) at /usr/sbin/ddclient line 1817.
WARNING:  cannot send to dynupdate.no-ip.com:443 (Bad file descriptor).
FAILED:   updating myhostname.hopto.org: Could not connect to dynupdate.no-ip.com.
```

I've note changed anything, this problem just appeared the other day. Can anyone help me troubleshoot/resolve?

thanks

---

### Post by tonyldo on 2012-08-15
happened whit me too:

```

sudo ddclient -force
Missing argument in sprintf at /usr/sbin/ddclient line 1543.
FAILED:   updating tonyldo.no-ip.org: 911: unexpected status ()

```

I don't know what changed since the last upgrade.

---

### Post by mcc28x on 2012-08-16
Hi,

What are you going to do then? Switch to the No-ip client?

cheers

---

### Post by mcc28x on 2012-08-16
I resolved this by creating an account with dns-omatic and updating from there to no-ip.

---

