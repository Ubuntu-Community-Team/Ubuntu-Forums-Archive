---
title: "can not start bind9 - apparmor ?"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by linubu on 2012-01-02
Hi.
I can not restart bind9 server.

dns@server:/etc/bind$ sudo /etc/init.d/bind9 stop 
 * Stopping domain name service... bind9   
    rndc: connect failed:  127.0.0.1#953: connection refused [OK] 

dns@server:/etc/bind$ sudo /etc/init.d/bind9 start 
 * Starting domain name service... 
bind9                               [fail] 

When i look into messages log file i found this description: 
apparmor="DENIED" operation="open" parent=12917  profile="/usr/sbin/named" name="/etc/ssl/openssl.cnf" pid=12918  comm="named" requested_mask="r" denied_mask="r" fsuid=118 ouid=0 

I shut down the apparmor and make the bind restart. 
The situation is the same. 

It's interesting that this error comes all the time. 
From first installation till now. 

my usr.bin.named 

/usr/sbin/named { 
  #include <abstractions/base> 
  #include <abstractions/nameservice> 
  #include <abstractions/nis> 

  capability net_bind_service, 
  capability setgid, 
  capability setuid, 
  capability sys_chroot, 

  /usr/sbin/named mr, 
  /var/lib/named/dev/random r, 
  /var/lib/named/etc/127.0.0 r, 
  /var/lib/named/etc/bind/named.conf r, 
  /var/lib/named/etc/bind/rndc.key r, 
  /var/lib/named/etc/localhost r, 
  /var/lib/named/etc/localtime r, 
  /var/lib/named/etc/named.run a, 
  /var/lib/named/etc/root.hints r, 
  /var/lib/named/etc/sites/domingo.dk/forward.zone r, 
  /var/lib/named/etc/sites/domingo.dk/reverse.zone r, 
  /var/lib/named/var/run/named.pid w, 
}

What could be the problem and how to fix it ?

---

### Post by Dangertux on 2012-01-02
> **linubu said:**
> Hi.
I can not restart bind9 server.

dns@server:/etc/bind$ sudo /etc/init.d/bind9 stop 
 * Stopping domain name service... bind9   
    rndc: connect failed:  127.0.0.1#953: connection refused [OK] 

dns@server:/etc/bind$ sudo /etc/init.d/bind9 start 
 * Starting domain name service... 
bind9                               [fail] 

When i look into messages log file i found this description: 
apparmor="DENIED" operation="open" parent=12917  profile="/usr/sbin/named" name="/etc/ssl/openssl.cnf" pid=12918  comm="named" requested_mask="r" denied_mask="r" fsuid=118 ouid=0 

I shut down the apparmor and make the bind restart. 
The situation is the same. 

It's interesting that this error comes all the time. 
From first installation till now. 

my usr.bin.named 

/usr/sbin/named { 
  #include <abstractions/base> 
  #include <abstractions/nameservice> 
  #include <abstractions/nis> 

  capability net_bind_service, 
  capability setgid, 
  capability setuid, 
  capability sys_chroot, 

  /usr/sbin/named mr, 
  /var/lib/named/dev/random r, 
  /var/lib/named/etc/127.0.0 r, 
  /var/lib/named/etc/bind/named.conf r, 
  /var/lib/named/etc/bind/rndc.key r, 
  /var/lib/named/etc/localhost r, 
  /var/lib/named/etc/localtime r, 
  /var/lib/named/etc/named.run a, 
  /var/lib/named/etc/root.hints r, 
  /var/lib/named/etc/sites/domingo.dk/forward.zone r, 
  /var/lib/named/etc/sites/domingo.dk/reverse.zone r, 
  /var/lib/named/var/run/named.pid w, 
}

What could be the problem and how to fix it ?


Perhaps add the followign to your apparmor profile

```

/etc/ssl/openssl.cnf r,

```

Reload the profile and that issue should be resolved.

Hope this helps.

---

