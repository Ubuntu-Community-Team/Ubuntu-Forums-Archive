---
title: "atftpd: can't bind port"
date: 2011-05-22
forum: Networking &amp; Wireless
---

### Post by deebee19701 on 2011-05-22
can't seem to figure this one out for the life of me.. what did I miss?


/var/log/syslog:May 22 16:38:34 testbed atftpd[3444]: atftpd: can't bind port 192.168.100.2:69/udp
@testbed:~$ 

below is the configuration file

@testbed:~$ sudo cat /etc/default/atftpd 

USE_INETD=false
OPTIONS="--bind-address 192.168.100.2 --tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5 /tftpboot"

I've also editted the file  /etc/init.d/atfpd 


PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/atftpd
NAME=atftpd
DESC="Advanced TFTP server"
USE_INETD=false
OPTIONS=""

---

### Post by deebee19701 on 2011-05-25
it would appear that each time I add or change the configuration file and try to restart the daemon  the atftpd won't come up and it is bound to a port

netstat -na shows up as 

udp        0      0 0.0.0.0:69        0.0.0.0:*  
but there is no application bound to that port. it was only after rebooting my machine i was able to bring it up

---

### Post by Drezard on 2012-07-31
Add -p to netstat next time to show the programs. 

> 
root@mcsmashed:/etc/default# netstat -nap  | grep 69
udp        0      0 0.0.0.0:69              0.0.0.0:*                           4717/inetd      


Its because atftpd may have been running under inetd before and thus inetd is still listening on the port.

On my machine I don't have a /etc/init.d/inetd script because I think VMWare tools installed my inetd or something like this. So I had to reboot my machine also but normally on Ubuntu you can do:

> 
# service inetd restart


Or

> 
# /etc/init.d/inetd restart


---

### Post by wildmanne39 on 2012-07-31
Hi, please do not create duplicate threads it dilutes the communities efforts.
Thanks

---

