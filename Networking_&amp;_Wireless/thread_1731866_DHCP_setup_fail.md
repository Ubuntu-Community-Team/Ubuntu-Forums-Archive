---
title: "DHCP setup fail"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by iconoclast hero on 2011-04-17
[B]Could someone see if they can quickly spot why the line
```
lease-file-name "/var/lib/dhcpd/dhcpd.leases";
```
in my /etc/dhcp3/dhcpd.conf giving me this error:
[/B]```
****Apr 17 15:03:04 ubuntu-lucky kernel: [757513.827270] type=1400  audit(1303066984.694:28): apparmor="DENIED" operation="open"  parent=18262 profile="/usr/sbin/dhcpd3"  name="/var/lib/dhcpd/dhcpd.leases" pid=18275 comm="dhcpd3"  requested_mask="r" denied_mask="r" fsuid=120 ouid=0

```[B]for this file:
[/B]****```
-rw-rw-rw- 1 root root 0 2011-04-17 15:06 /var/lib/dhcpd/dhcpd.leases
```[B]
[/B]The error looks like it is not getting a permission it needs...when I comment out the line at the top there, it starts fine.

I saw this [http://ubuntuforums.org/showthread.php?t=977830](http://ubuntuforums.org/showthread.php?t=977830) but don't really know what I'm doing or what symlinking is or if it is still even relevant on server 10.10.

thanks

---

### Post by iconoclast hero on 2011-04-17
> **iconoclast hero said:**
> [B]Could someone see if they can quickly spot why the line
```
lease-file-name "/var/lib/dhcpd/dhcpd.leases";
```in my /etc/dhcp3/dhcpd.conf giving me this error:
[/B]```
Apr 17 15:03:04 ubuntu-lucky kernel: [757513.827270] type=1400  audit(1303066984.694:28): apparmor="DENIED" operation="open"  parent=18262 profile="/usr/sbin/dhcpd3"  name="/var/lib/dhcpd/dhcpd.leases" pid=18275 comm="dhcpd3"  requested_mask="r" denied_mask="r" fsuid=120 ouid=0

```[B]for this file:
[/B]```
-rw-rw-rw- 1 root root 0 2011-04-17 15:06 /var/lib/dhcpd/dhcpd.leases
```The error looks like it is not getting a permission it needs...when I comment out the line at the top there, it starts fine.

I saw this [http://ubuntuforums.org/showthread.php?t=977830](http://ubuntuforums.org/showthread.php?t=977830) but don't really know what I'm doing or what symlinking is or if it is still even relevant on server 10.10.

thanks

The output of dhclient wlan0 is
```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
Open a socket for LPF: Operation not permitted

```

predictably /var/lin/dhcp3/dhclient.leases is empty but I am using the new DHCP server just fine on this machine...  Assigned the proper number when I turned off the router DHCP and all...

---

### Post by velle frak on 2011-04-17
Under which user is your dhcpd started?

---

### Post by iconoclast hero on 2011-04-17
I've been fighting with ps, but it doesn't want to tell me how to do that.

---

### Post by iconoclast hero on 2011-04-17
> **iconoclast hero said:**
> I've been fighting with ps, but it doesn't want to tell me how to do that.



```
UID        PID  PPID  C STIME TTY          TIME CMD
dhcpd    19019     1  0 15:46 ?        00:00:00 /usr/sbin/dhcpd3 -q -pf /var/run/dhcp3-server/dhcpd.pid -cf /etc/dhcp3/dhcpd.

```It appears the answer is dhcpd.

I also found 4 instances of Apache2 running and I don't have a webpage up, just an Icecast and an mpd server running...  is that normal?
```
14457 ?        S      0:00 /usr/sbin/apache2 -k start
14458 ?        S      0:00 /usr/sbin/apache2 -k start
14459 ?        S      0:00 /usr/sbin/apache2 -k start
14460 ?        S      0:00 /usr/sbin/apache2 -k start
14461 ?        S      0:00 /usr/sbin/apache2 -k start
```

---

### Post by velle frak on 2011-04-18
If you do not host a website on that machine, I would not run the apache service (disable it through /etc/rc?).

---

### Post by iconoclast hero on 2011-04-18
> **velle frak said:**
> If you do not host a website on that machine, I would not run the apache service (disable it through /etc/rc?).

Ok, but what about the DHCP server not working right because it doesn't have proper permissions?

---

