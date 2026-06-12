---
title: "Apache could not determine fully qualified domain name"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by Horatio on 2011-10-02
Hello,
   I'm re-configuring apache2 for a virtual host environment. After restarting apache2 I have the following errors in /var/log/apache2/error.log

```
[Sat Oct 01 02:26:03 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Oct 01 02:35:44 2011] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 192.168.1.100 for ServerName
[Sat Oct 01 02:35:44 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Oct 01 02:42:40 2011] [notice] caught SIGTERM, shutting down
[Sat Oct 01 02:42:41 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Oct 01 03:17:28 2011] [notice] caught SIGTERM, shutting down
[Sat Oct 01 16:38:01 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.2 with Suhosin-Patch configured -- resuming normal operations
```

In addition, my target goal is to use local email addresses, using a working( mail bob@earth works) postfix install, in an drupal installation, and during the installation drupal was rejecting my local email addresses. I believe this is related to the above error.

I also don't understand why nslookup `hostname` is failing? 

```

$ nslookup 192.168.1.100
Server:         192.168.1.1
Address:        192.168.1.1#53

** server can't find 100.1.168.192.in-addr.arpa.: NXDOMAIN

```

Further information:
```

$ cat /etc/hosts
# The loop-back
127.0.0.1       localhost

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

# The local Notwork
192.168.1.100 earth
192.168.1.102 mercury
192.168.1.104 venus

192.168.1.100 snippets.earth

```

```

$ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:a0:cc:79:bc:ea  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:ccff:fe79:bcea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69854 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52757 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:51330792 (51.3 MB)  TX bytes:8069708 (8.0 MB)
          Interrupt:21 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:22:15:ba:d3:d1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1558 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:585203 (585.2 KB)  TX bytes:585203 (585.2 KB)


```

```

$ hostname
earth

```

```

$ domainname
(none)

```


ARG.... NOTE THIS. I believe this should return, "earth"?
```

$ nslookup 192.168.1.100
Server:         192.168.1.1
Address:        192.168.1.1#53

** server can't find 100.1.168.192.in-addr.arpa.: NXDOMAIN

```

```

$ nslookup earth
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   earth
Address: 63.251.179.13
Name:   earth
Address: 8.15.7.117

```

```

$ nslookup 192.168.1.1
Server:         192.168.1.1
Address:        192.168.1.1#53

1.1.168.192.in-addr.arpa        name = Wireless_Broadband_Router.home.

```

```

cat /etc/apache2/httpd.conf


```

```

 cat /etc/apache2/sites-enabled/snippets.earth
<VirtualHost *:80>
   ServerAdmin webmaster@earth

   DocumentRoot /var/www-sites/snippets/wroot
   ServerName snippets.earth
   ServerAlias snippets.earth
   ErrorLog /var/log/apache2/sites/snippets.earth_error-log
   CustomLog /var/log/apache2/sites/snippets.earth_access-log "combined"

   # Rewrite the www
   RewriteEngine on

   RewriteCond %{HTTP_Host} ^www\.snippets\.earth/?$ [NC]
   RewriteRule ^(.*)$ http://snippets.earth$1 [L,R=301]

   # Possible values include: debug, info, notice, warn, error, crit,
   # alert, emerg.
   LogLevel debug




```


As for my apache2 installation, I used:
```
sudo tasksel install lamp-server
```

Thanks for any comments, advice, or solutions. If I forgot to give needed information, please let me know.

---

### Post by Horatio on 2011-10-02
Okay I seem to have apache2 happy now. I forgot to set a global directive. I put it in the file /etc/apache2/conf.d/fqdn:
```
$ cat /etc/apache2/conf.d/fqdn
ServerName earth
```

Although, my problem stands. I want verifiable local email address. Maybe my postfix config could be helpful.

```

$ cat /etc/postfix/main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = earth
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
local_recipient_maps = proxy:unix:passwd.byname $alias_maps
mydestination = earth, localhost.localdomain, , localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128 192.168.1.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mail_spool_directory = /var/mail/
recipient_delimiter = +
inet_interfaces = all 
default_transport = error
relay_transport = error
inet_protocols = all

```

Does anyone know how to trouble shoot this? I don't know how drupal is doing email verification, but I imagine that drupal tries to verify the host part of the email address? So, this is where I think is still is related to my nslookup problem:

```

$ nslookup 192.168.1.100
Server:         192.168.1.1
Address:        192.168.1.1#53

** server can't find 100.1.168.192.in-addr.arpa.: NXDOMAIN

```

```

$ nslookup earth
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
Name:   earth
Address: 63.251.179.13
Name:   earth
Address: 8.15.7.117

```

I'm starting to wonder if I need to install bind to have the email address verifiable? Any advice?

---

### Post by Horatio on 2011-10-02
Okay I found a quick fix.

I was typing example@earth in the drupal 7 email field, and it was rejected.

I just was able to change the email in the field from a gmail email to a local email address in the form, [email]example@earth.local[/email] .

---

