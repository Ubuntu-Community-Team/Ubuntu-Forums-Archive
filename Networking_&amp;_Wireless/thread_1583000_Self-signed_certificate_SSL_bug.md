---
title: "Self-signed certificate SSL bug ?"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by ericv on 2010-09-27
Hi,

I'm using Ubuntu 10.04 LTS and I encounter the following problem / bug :

I can't access any website with https using a self-signed certificate.

I've tried with chromium/seamonkey/firefox/wget --no-check-certificate and each time it gets stuck forever (not even getting a timeout !!).

For instance, here's what I get with wget :
```
eric@orwell:/tmp$ wget --no-check-certificate xxx.xxx.xxx
--2010-09-27 14:45:35--  http://xxx.xxx.xxx/
Resolving xxx.xxx.xxx... yyy.yyy.yyy.yyy
Connecting to xxx.xxx.xxx|yyy.yyy.yyy.yyy|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://xxx.xxx.xxx/ [following]
--2010-09-27 14:45:41--  https://xxx.xxx.xxx/
Connecting to xxx.xxx.xxx|yyy.yyy.yyy.yyy|:443... connected.
WARNING: cannot verify xxx.xxx.xxx's certificate, issued by `/C=US/ST=CA/O=Sun M
icrosystems, Inc./CN=yyy.yyy.yyy.yyy':
  Self-signed certificate encountered.
WARNING: certificate common name `yyy.yyy.yyy.yyy' doesn't match requested host 
name `xxx.xxx.xxx'.
HTTP request sent, awaiting response...
[stuck forever]

```

Any idea what I may be missing ?
Thanks,
Eric.

---

