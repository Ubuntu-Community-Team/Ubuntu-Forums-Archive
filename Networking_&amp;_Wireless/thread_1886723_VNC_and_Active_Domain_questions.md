---
title: "VNC and Active Domain questions"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by QuinRiva on 2011-11-25
I've been having weird problems recently, with things that used to work not working.

My server is part of a Windows Active Directory Domain, and it was previously connected, but I can no longer login as Domain users and it appears as if I'm not connected despite Likewise reporting otherwise.

So I type in:
```
kinit quinriva
Password for quinriva@SIN.X:

```

I enter the password, press enter and nothing happens.  So I should be connect right?

```
carl@Vanity:/$ klist
klist: No credentials cache found (ticket cache FILE:/tmp/krb5cc_1000)
```

Weird.

The contents of /etc/krb5.conf:
```
[logging]
    default = FILE10000:/var/log/krb5lib.log

libdefaults]
    ticket_lifetime = 24000
    default_realm = SIN.X

[realms]
    SIN.X = {
    kdc = Pride
    admin_server = Pride
    default_domain = SIN.X
    }

[domain_realm]
    .sin.x = SIN.X
    sin.x = SIN.X

```

Similarly VNC doesn't work either:
I followed [these]("http://mlepicki.com/?p=10") instructions for setting up VNC, but connecting from my Windows machine with both UltraVNC and TightVNC results in *Failed to connect to server*.

Any ideas?

---

