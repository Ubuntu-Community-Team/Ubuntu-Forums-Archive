---
title: "Connections to dyndns"
date: 2012-08-09
forum: Networking &amp; Wireless
---

### Post by Statia on 2012-08-09
I am seeing substantial network traffic when I have no application open that should use the network. Using netstat -tnp I find IP-addresses that are linked to dyndns services, but I don't use anything like that. Also, netstat -tnp can't give me processes that are linked to this traffic. Traffic lasts for several minutes, is mostly down and can be as much as 100kbytes/sec.

```
$ netstat -tnp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0    298 192.168.178.31:35489    192.168.178.1:445       ESTABLISHED -               
tcp        0      0 127.0.0.1:7634          127.0.0.1:53711         TIME_WAIT   -               
tcp        0      0 192.168.178.31:34621    91.198.22.70:80         TIME_WAIT   -       

 $ whois 91.198.22.70

% Information related to '91.198.22.0 - 91.198.22.255'

inetnum:         91.198.22.0 - 91.198.22.255
netname:         DYNDNS-UK
descr:           Dynamic Network Services, Inc.
country:         GB

```And:

```
$ netstat 
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 Quokka.fritz.box:35489  fritz.box:microsoft-ds  ESTABLISHED
tcp        1      1 Quokka.fritz.box:48845  checkip-lax.dyndns:http CLOSING    
tcp        0      0 localhost:7634          localhost:53717         TIME_WAIT  
```And:

```
$ netstat -tnp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0    324 192.168.178.31:35489    192.168.178.1:445       ESTABLISHED -               
tcp        0      0 192.168.178.31:48845    216.146.39.70:80        TIME_WAIT   -               
tcp        0      0 127.0.0.1:7634          127.0.0.1:53719         TIME_WAIT   -               
$ whois 216.146.39.70


NetRange:       216.146.32.0 - 216.146.47.255
CIDR:           216.146.32.0/20
OriginAS:       AS33517
NetName:        DNSINC-3
NetHandle:      NET-216-146-32-0-1
Parent:         NET-216-0-0-0-0
NetType:        Direct Allocation
RegDate:        2008-07-16
Updated:        2012-03-02
Ref:            http://whois.arin.net/rest/net/NET-216-146-32-0-1


```Computer is behind a firewalled router doing NAT (I think that is called differently these days, but I'm an old fart)
What's going on here?

---

### Post by Statia on 2012-08-09
Please forgive me a premature:
BUMP
as I think I am in the wrong time zone for maximum exposure and think this activity might be really fishy...

---

### Post by Statia on 2012-08-10
I was able to "catch" a process:

```
$ netstat -tnp
(Not all processes could be identified, non-owned process info
 will not be shown, you would have to be root to see it all.)
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.178.31:59176    216.146.39.70:80        TIME_WAIT   -               
tcp        0      0 192.168.178.31:42694    82.94.229.35:80         ESTABLISHED 6011/plasma-desktop
tcp        0      0 127.0.0.1:7634          127.0.0.1:37573         TIME_WAIT   -               
tcp        0      0 127.0.0.1:7634          127.0.0.1:37574         TIME_WAIT   -               
tcp        0    142 192.168.178.31:49645    192.168.178.1:445       ESTABLISHED -               

```

Also , without KDE running, no traffic.

---

### Post by bakegoodz on 2012-08-12
Looks suspicious. Maybe cracker has ddns so they can find your compromised computer even if the IP address changes. If I was in your shoes I would do a backup and reinstall right away. Look at your router setting see if there is any port forwarding you don't know about too.

---

### Post by Statia on 2012-08-13
I've been doing some digging, reading and thinking. I am starting to think the traffic I see is due to samba. I mount a large (932GB, 254GB used) samba share at boot.

```
# netstat -tnp
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.178.31:43394    216.146.39.70:80        TIME_WAIT   -               
tcp        0      0 192.168.178.31:48714    192.168.178.1:445       ESTABLISHED -               
tcp        0      0 127.0.0.1:7634          127.0.0.1:43718         TIME_WAIT   -               
```
I already blocked the "foreign" IP-address using
```
iptables -A INPUT -s 216.146.39.70 -j DROP
```but the traffic keeps going.
I still don know what this connection is, but I think the traffic I'm seeing is not coming from / going to the "foreign" IP, but is instead SMB related.

---

### Post by Statia on 2012-08-13
I added the suspicious IP's to rc.local with for each IP a line like this:
     
   ```
  iptables -A INPUT -s $SUSPICIOUS_IP -j DROP 
```but after a reboot, the addresses still show up with netstat.
Should I drop outgoing connections as well?

---

### Post by Statia on 2012-09-05
I found this in my .xsession-errors:

```
09/05/12 12:08:18 PM            Resolving checkip.dyndns.org (checkip.dyndns.org)... 216.146.39.70, 91.198.22.70, 216.146.38.70
09/05/12 12:08:18 PM            Connecting to checkip.dyndns.org (checkip.dyndns.org)|216.146.39.70|:80... 
09/05/12 12:08:28 PM            connected.
09/05/12 12:08:28 PM            HTTP request sent, awaiting response... 200 OK
09/05/12 12:08:28 PM            Length: 106 [text/html]
09/05/12 12:08:28 PM            Saving to: `index.html'
09/05/12 12:08:28 PM            
09/05/12 12:08:28 PM                 0K                                                       100% 14.8M=0s
09/05/12 12:08:28 PM            
09/05/12 12:08:28 PM            2012-09-05 12:08:18 (14.8 MB/s) - `index.html' saved [106/106]

```Anyone an idea what this is?

It's not likely I've been hacked, PC is behind a strict firewall, updates are checked for daily and applied right away.

---

### Post by Statia on 2012-09-05
Found it.
It's a Superkaramba widget called sysmaloon.
(It's quite gorgeous)
It displays my external IP-address (my router's IP). I guess it makes some kind of outgoing connection to retrieve my IP.

---

