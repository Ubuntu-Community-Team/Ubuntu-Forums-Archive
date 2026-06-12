---
title: "iPhone and xl2tpd"
date: 2011-01-31
forum: Networking &amp; Wireless
---

### Post by Gaku on 2011-01-31
Hello!

On my Ubuntu installed xl2tpd.
Connected from Win7 without any problems. But I cannot connect from iPhone. 
Where I can get pre-shared key? Is it differ from password?

---

### Post by Gaku on 2011-02-01
Doing as [http://ubuntuforums.org/showthread.php?t=1645473](http://ubuntuforums.org/showthread.php?t=1645473)

A.B.C.D - my Elastic IP

/etc/ipsec.conf:
> version 2.0
 
config setup
  nat_traversal=yes
  virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/8,%v4:172.16.0.0/12
  oe=off
  protostack=netkey
include /etc/ipsec.d/l2tp-psk.conf


/etc/ipsec.d/l2tp-psk.conf:
> conn L2TP-PSK-NAT
  rightsubnet=vhost:%priv
  also=L2TP-PSK-noNAT
 
conn L2TP-PSK-noNAT
  authby=secret
  pfs=no
  auto=add
  keyingtries=3
  rekey=no
  type=transport
  left=A.B.C.D
  leftnexthop=A.B.C.D
  leftprotoport=17/1701
  right=%any
  rightprotoport=17/%any


/etc/ppp/chap-secrets:
> test123 * test123 *


/etc/ipsec.secrets:
> 
A.B.C.D %any: PSK "secret"


/etc/ppp/options.xl2tpd:
> 
mtu 1410
mru 1410
ms-dns 8.8.8.8
ms-dns 8.8.4.4
lcp-echo-interval 3
lcp-echo-failure 8
nodeflate
noproxyarp
netmask 255.255.255.0
lock


/var/log/auth.log
> 
Jan 31 21:13:48 domU-12-31-39-10-60-9D pluto7741: packet from 93.80.44.86:500: initial Main Mode message received on 10.198.99.107:500 but no connection has been authorized with policy=PSK


But I've write authby=secret. What may be wrong?

---

### Post by Gaku on 2011-02-01
Arrgh, finally solved half of problem. Elastic IP must be replaced with IP-address of local interface 10.x.x.x.

But now problems with xl2tpd:
Connection 8 closed to 213.87.91.49, port 54679 (No Authorization)

:-(

---

### Post by Gaku on 2011-02-01
Found bug in that howto: "lac" param in xl2tpd.conf wasn't specified.

Next error :-(
> xl2tpd[757]: control_finish: Peer requested tunnel 23 twice, ignoring second one.
xl2tpd[757]: control_finish: Peer requested tunnel 23 twice, ignoring second one.
xl2tpd[757]: Maximum retries exceeded for tunnel 56568.  Closing.
xl2tpd[757]: control_finish: Peer requested tunnel 23 twice, ignoring second one.
xl2tpd[757]: Connection 23 closed to 213.87.89.28, port 53428 (Timeout)
xl2tpd[757]: control_finish: Peer requested tunnel 23 twice, ignoring second one.
xl2tpd[757]: Unable to deliver closing message for tunnel 56568. Destroying anyway.

---

### Post by Gaku on 2011-02-01
ifconfig:
eth0      Link encap:Ethernet  HWaddr 12:31:39:10:60:9d
lo        Link encap:Local Loopback

no ipsec0. :-(

Still not working :(((

---

### Post by ndoggac on 2011-02-01
I'm at the same spot, with the same syslog errors.

Still working on it.  I'm annoyed that the Openswan update killed this for me.  It worked fine before.

---

### Post by ndoggac on 2011-02-01
Reading around it seems there is a bug in Openswan 2.6.x that breaks xl2tp.  Couldn't find any info about a fix other than rolling back to 2.4.x version.  This explains why my guide worked before, but not now. :-(

---

### Post by Jnex26 on 2011-03-24
The problem your experiencing is to do with ubuntu's maintained version. 

sudo -i 
apt-get build-deps openswan 
apt-get remove openswan 
apt-get autoremove


cd ~ 
wget [http://www.openswan.org/download/openswan-2.6.33.tar.gz](http://www.openswan.org/download/openswan-2.6.33.tar.gz)
tar -xvf openswan-2.6.33.tar.gz

cd openswan-2.6.33
make programs install

---

### Post by ndoggac on 2011-06-08
Got this working again, check my guide here...

[http://ubuntuforums.org/showthread.php?t=1645473&highlight=openswan+iphone](http://ubuntuforums.org/showthread.php?t=1645473&highlight=openswan+iphone)

---

