---
title: "Apache binds to ipv6 but not to ipv4"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by nathema on 2011-08-12
On my 10.04 LTS Ubuntu Server installation, apache2 doesn't bind to ipv4. It does bind to ipv6. I didn't notice this at first, because from my home connection I could visit the webpages without trouble. I noticed it running netstats -ta:
```
tcp        0      0 localhost:10024         *:*                     LISTEN
tcp        0      0 localhost:10025         *:*                     LISTEN
tcp        0      0 localhost:mysql         *:*                     LISTEN
tcp        0      0 localhost:spamd         *:*                     LISTEN
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 *:smtp                  *:*                     LISTEN
tcp6       0      0 [::]:www                [::]:*                  LISTEN
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
tcp6       0      0 [::]:smtp               [::]:*                  LISTEN

```Here's ifconfig -a:
```

eth0      Link encap:Ethernet  HWaddr 1a:62:41:fe:77:24
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 7a:e9:38:f8:d1:c6
          inet addr:197.53.163.235  Bcast:197.53.163.255  Mask:255.255.255.192
          inet6 addr: 2b10:1cd0:0:103:78e9:38ff:fef8:d1c6/64 Scope:Global
          inet6 addr: fe90::78f9:39ff:fef8:d1c6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:165787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:41041 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:64731031 (64.7 MB)  TX bytes:11827814 (11.8 MB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1571 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:701725 (701.7 KB)  TX bytes:701725 (701.7 KB)
```Apache2 ports.conf is unchanged:
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```I'm trying to avoid hardcoding the ips in 2 Listen lines.

---

### Post by lemming465 on 2011-08-12
Just because it's only showing the v6 binding doesn't necessarily mean it won't accept v4 connections using "mapped" (::FFFF:a.b.c.d style) addresses.  It depends on whether or not it was configured with --enable-v4-mapped or --disable-v4-mapped.  According to the [Apache docs]("http://httpd.apache.org/docs/2.2/bind.html"), we would expect that Linux does the former and *BSD the latter. Have you verified that v4 connections don't actually work?

---

### Post by nathema on 2011-08-13
Indeed, after telnet on port 80 i see the following line in netstat:
```
tcp        0      0 server:46737    server:www      TIME_WAIT

```

It indeed maps v4.

---

