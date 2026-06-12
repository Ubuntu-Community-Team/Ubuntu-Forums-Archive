---
title: "Firewall problem with nagios"
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by glisignoli on 2009-07-08
I'm trying to open port 5666 for nagios (nrpe) on a mail server, but I no matter what I do I can never get access to that port.

I check to see if the port is available with "nmap -A -v localhost"
but it never shows.

I added port 5666 to my firewall with:
```

iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5666 -j ACCEPT

```

I've set NRPE up as described in the NRPE pdf file (it says to use xinetd, I'm not to sure how the effect this).

My /etc/xinetd.d/nrpe file is:
```

 default: on
# description: NRPE (Nagios Remote Plugin Executor)
service nrpe
{
        flags           = REUSE
        socket_type     = stream
        port            = 5666
        wait            = no
        user            = nagios
        group           = nagios
        server          = /usr/local/nagios/bin/nrpe
        server_args     = -c /usr/local/nagios/etc/nrpe.cfg --inetd
        log_on_failure  += USERID
        disable         = no
        only_from       = 127.0.0.1
}

```

Output of netstat -an | grep "LISTEN "
```

tcp        0      0 0.0.0.0:5666            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:873             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN
tcp        0      0 192.168.1.1:53          0.0.0.0:*               LISTEN
tcp        0      0 10.10.50.254:53         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp6       0      0 :::4899                 :::*                    LISTEN
tcp6       0      0 :::2022                 :::*                    LISTEN
tcp6       0      0 :::873                  :::*                    LISTEN
tcp6       0      0 :::110                  :::*                    LISTEN
tcp6       0      0 :::143                  :::*                    LISTEN
tcp6       0      0 :::1877                 :::*                    LISTEN
tcp6       0      0 :::25                   :::*                    LISTEN
tcp6       0      0 ::1:953                 :::*                    LISTEN

```

Nmap -A -v localhost

```

Discovered open port 21/tcp on 127.0.0.1
Discovered open port 53/tcp on 127.0.0.1
Discovered open port 80/tcp on 127.0.0.1
Discovered open port 25/tcp on 127.0.0.1
Discovered open port 783/tcp on 127.0.0.1
Discovered open port 953/tcp on 127.0.0.1
Discovered open port 2022/tcp on 127.0.0.1
Discovered open port 139/tcp on 127.0.0.1
Discovered open port 143/tcp on 127.0.0.1
Discovered open port 110/tcp on 127.0.0.1
Discovered open port 3306/tcp on 127.0.0.1
Discovered open port 4899/tcp on 127.0.0.1
Discovered open port 445/tcp on 127.0.0.1
Discovered open port 873/tcp on 127.0.0.1

```

---

### Post by slugmax on 2009-07-09
> **glisignoli said:**
> I'm trying to open port 5666 for nagios (nrpe) on a mail server, but I no matter what I do I can never get access to that port.
I added port 5666 to my firewall with:
```

iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 5666 -j ACCEPT

```
...
```

tcp        0      0 0.0.0.0:5666            0.0.0.0:*               LISTEN

```


If the firewall is on the mail server, then check your nmap-services file for port 5666, if it is not present, nmap won't scan that port unless you specify it with something like 'nmap -v -p 5666 localhost'.

If your firewall is on a different box from your mail server, the problem is your iptables rule. The INPUT chain only sees packets destined for the firewall itself. You want:

```

iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -p tcp --dport 5666 -m state --state NEW -j ACCEPT
...

```

and you'll also need to enable IP forwarding (if it's not already).

You might find these scripts useful as a reference in that case:

[http://blog.unixlore.net/2006/03/linux-iptables-firewall-scripts.html](http://blog.unixlore.net/2006/03/linux-iptables-firewall-scripts.html)

Doug

---

