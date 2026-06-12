---
title: "Kerberos krb5-rsh issue"
date: 2010-09-04
forum: Networking &amp; Wireless
---

### Post by hobbyhack on 2010-09-04
I have a debian server running as a master kerberos and key distribution server.  From a separate debian client I am able to 'krb5-rsh -PN -x debtest1.hobbyhack.net' (referred to as rsh from now on) into the server.  From my Ubuntu 10.04 client I am unable to rsh in although i don't see any errors.

[LIST]
[*]both clients and server are fresh installs in virtualbox
[*]/etc/krb5.conf is identical on both clients
[*]both clients seem to be receiving the appropriate keys
[*]dns is working and all the digs i can do between any of the machines returns the fqdn or the right ip
[/LIST]

I am able to get a key initially:
```

shane@xhanux1:~$ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: shane@HOBBYHACK.NET

Valid starting     Expires            Service principal
09/04/10 00:06:53  09/04/10 10:06:53  krbtgt/HOBBYHACK.NET@HOBBYHACK.NET
	renew until 09/05/10 00:06:50

```

When I try rsh in I don't see any errors sent to screen or in any of the client error logs:
```

shane@xhanux1:~$ krb5-rsh -PN -x debtest1.hobbyhack.net
shane@xhanux1:~$  

```

The server does log the following when i try and login:
```
==> syslog <==
Sep  3 23:59:40 debtest1 klogind[3337]: connect from 192.168.1.71 (192.168.1.71)

==> daemon.log <==
Sep  3 23:59:40 debtest1 klogind[3337]: connect from 192.168.1.71 (192.168.1.71)

==> auth.log <==
Sep  3 23:59:40 debtest1 klogind[3337]: Error reading message

```

After login you can see I get the host key:
```

shane@xhanux1:~$ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: shane@HOBBYHACK.NET

Valid starting     Expires            Service principal
09/03/10 23:44:04  09/04/10 09:44:04  krbtgt/HOBBYHACK.NET@HOBBYHACK.NET
	renew until 09/04/10 23:44:00
09/03/10 23:44:08  09/04/10 09:44:04  host/debtest1.hobbyhack.net@HOBBYHACK.NET
	renew until 09/04/10 23:44:00

``` 

On the debian client I get logged in:
```

shane@debtest2:/etc$ krb5-rsh -PN -x debtest1.hobbyhack.net
This rlogin session is encrypting all data transmissions.
Last login: Fri Sep  3 23:25:02 from debtest2
Linux debtest1.hobbyhack.net 2.6.32-5-686 #1 SMP Thu Aug 12 13:38:27 UTC 2010 i686

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
You have mail.
shane@debtest1:~$ 

```


I see this in the server logs when the debian client logs in:
```

==> syslog <==
Sep  4 00:02:46 debtest1 klogind[3341]: connect from 192.168.1.13 (192.168.1.13)

==> daemon.log <==
Sep  4 00:02:46 debtest1 klogind[3341]: connect from 192.168.1.13 (192.168.1.13)

```

And I end up with similar looking keys:
```

shane@debtest2:/etc$ klist
Ticket cache: FILE:/tmp/krb5cc_1000
Default principal: shane@HOBBYHACK.NET

Valid starting     Expires            Service principal
09/03/10 23:21:52  09/04/10 09:21:52  krbtgt/HOBBYHACK.NET@HOBBYHACK.NET
	renew until 09/04/10 23:21:50
09/03/10 23:22:37  09/04/10 09:21:52  host/debtest1.hobbyhack.net@HOBBYHACK.NET
	renew until 09/04/10 23:21:50

```

Any ideas?

---

### Post by hobbyhack on 2010-09-04
The version of packages is a bit different.  On the working client I have:
```

shane@debtest2:/etc$ sudo apt-show-versions | grep krb5
krb5-clients/squeeze uptodate 1:1.0.1-1
krb5-config/squeeze uptodate 2.2
krb5-user/squeeze uptodate 1.8.3+dfsg~beta1-1
libgssapi-krb5-2/squeeze uptodate 1.8.3+dfsg~beta1-1
libkrb5-3/squeeze uptodate 1.8.3+dfsg~beta1-1
libkrb5support0/squeeze uptodate 1.8.3+dfsg~beta1-1

```

On the one that isn't working I have:
```

shane@xhanux1:~$ sudo apt-show-versions | grep krb5
krb5-clients/lucid uptodate 1:1.0~alpha1-1
krb5-config/lucid uptodate 2.2
krb5-user/lucid-security uptodate 1.8.1+dfsg-2ubuntu0.2
libgssapi-krb5-2/lucid-security uptodate 1.8.1+dfsg-2ubuntu0.2
libkrb5-3/lucid-security uptodate 1.8.1+dfsg-2ubuntu0.2
libkrb5support0/lucid-security uptodate 1.8.1+dfsg-2ubuntu0.2

```

---

