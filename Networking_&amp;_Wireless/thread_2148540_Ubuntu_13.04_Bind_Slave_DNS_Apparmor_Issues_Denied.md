---
title: "Ubuntu 13.04 Bind Slave DNS Apparmor Issues Denied Transfer and Modification Date"
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by own3mall on 2013-05-25
Hi All,

I'm having problems getting my DNS records to replicate from my domain over to other servers using slave DNS on Ubuntu 13.04.  On the master and slave servers, I have set the following settings in /etc/apparmor.d/usr.sbin.named:

```

# vim:syntax=apparmor
# Last Modified: Fri Jun  1 16:43:22 2007
#include <tunables/global>

/usr/sbin/named {
  #include <abstractions/base>
  #include <abstractions/nameservice>

  capability net_bind_service,
  capability setgid,
  capability setuid,
  capability sys_chroot,
  capability sys_resource,

  # /etc/bind should be read-only for bind
  # /var/lib/bind is for dynamically updated zone (and journal) files.
  # /var/cache/bind is for slave/stub data, since we're not the origin of it.
  # See /usr/share/doc/bind9/README.Debian.gz
  /etc/bind/** rw,
  /var/lib/bind/** rw,
  /var/lib/bind/ rw,
  /var/cache/bind/** lrw,
  /var/cache/bind/ rw,

  # gssapi
  /etc/krb5.keytab kr,
  /etc/bind/krb5.keytab kr,

  # ssl
  /etc/ssl/openssl.cnf r,

  # dnscvsutil package
  /var/lib/dnscvsutil/compiled/** rw,

  /proc/net/if_inet6 r,
  /proc/*/net/if_inet6 r,
  /usr/sbin/named mr,
  /{,var/}run/named/named.pid w,
  /{,var/}run/named/session.key w,
  # support for resolvconf
  /{,var/}run/named/named.options r,

  # some people like to put logs in /var/log/named/ instead of having
  # syslog do the heavy lifting.
  /var/log/named/** rw,
  /var/log/named/ rw,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.sbin.named>
}

```

/etc/bind/named.conf has the following:
```

zone "mydomain.com" {
        type slave;
        file "/etc/bind/mydomain.com";
        masters { 173.213.124.98; };
};

```

When I restart the bind daemon, I get the following:

```

May 25 13:33:56 earnolmartin-VirtualBox named[10354]: zone 255.in-addr.arpa/IN: loaded serial 1
May 25 13:33:56 earnolmartin-VirtualBox kernel: [ 8715.712977] type=1702 audit(1369510436.230:91): op=linkat action=denied pid=10356 comm="named" path="/etc/bind/mydomain.com" dev="sda1" ino=583771
May 25 13:33:56 earnolmartin-VirtualBox named[10354]: all zones loaded
May 25 13:33:56 earnolmartin-VirtualBox named[10354]: running
May 25 13:33:56 earnolmartin-VirtualBox named[10354]: zone mydomain.com/IN: Transfer started.
May 25 13:33:56 earnolmartin-VirtualBox named[10354]: transfer of 'mydomain.com/IN' from 173.213.124.98#53: connected using 10.0.2.15#37690
May 25 13:33:56 earnolmartin-VirtualBox named[10354]: zone mydomain.com/IN: transferred serial 171
May 25 13:33:56 earnolmartin-VirtualBox named[10354]: zone mydomain.com/IN: transfer: could not set file modification time of '/etc/bind/mydomain.com': permission denied
May 25 13:33:56 earnolmartin-VirtualBox named[10354]: transfer of 'mydomain.com/IN' from 173.213.124.98#53: Transfer completed: 1 messages, 84 records, 1652 bytes, 0.110 secs (15018 bytes/sec)

```

It would appear that if I chown the mydomain.com file to bind:bind, the modification time error will go away; however, apparmor is still blocking it.  

```

May 25 13:44:22 earnolmartin-VirtualBox kernel: [ 9342.115092] type=1400 audit(1369511062.631:93): apparmor="DENIED" operation="link" parent=10449 profile="/usr/sbin/named" name="/etc/bind/db-XVHpRRYR" pid=10452 comm="named" requested_mask="l" denied_mask="l" fsuid=118 ouid=118 target="/etc/bind/mydomain.com"

```

Why should a slave dns entry have to be owned by bind when the rest are owned by root?

Anyone have any idea how to fix these problems?

---

### Post by own3mall on 2013-05-25
Turns out the only change you need to make is this if you are receiving any of the error messages above:

```

sudo chmod -R 774 /etc/bind

```

Your DNS transfers should work now.  (note, they might be in raw binary format)

---

