---
title: "xinetd and ipv4 or ipv6"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by matthewboh on 2009-06-15
I have an 8.04 LTS server running Amanda. My clients that run Hardy (8.04) are running backups and are configured to run over tcp4. I have upgraded those boxes using the upgrade manager to 9.04 and they still work just fine, with the amanda service running on IPv4.

I have a new computer running a clean install of 9.04. I copied over the configuration files and have been trying to run a client. However, the server just sits and waits for ACK

I ran a netstat -pat on the client and got

```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State PID/Program name
tcp 0 0 localhost:ipp *:* LISTEN -
tcp 0 0 localhost:smtp *:* LISTEN -
tcp 1 1 mlb-dell.imparisy:38059 master.mozillazine.:www LAST_ACK -
tcp 1 1 mlb-dell.imparisy:38062 master.mozillazine.:www LAST_ACK -
tcp 1 1 mlb-dell.imparisy:38061 master.mozillazine.:www LAST_ACK -
tcp 1 1 mlb-dell.imparisy:38060 master.mozillazine.:www LAST_ACK -
tcp 0 0 mlb-dell.imparisy:58330 od-in-f147.google.c:www ESTABLISHED 3506/firefox
tcp 0 0 mlb-dell.imparisy:45959 qy-in-f100.google.c:www ESTABLISHED 3506/firefox
tcp 1 1 mlb-dell.imparisy:38054 master.mozillazine.:www LAST_ACK -
tcp 0 0 mlb-dell.imparisy:43647 ubuntu.imparisystem:ssh ESTABLISHED 5068/ssh
tcp 1 1 mlb-dell.imparisy:38063 master.mozillazine.:www LAST_ACK -
tcp6 0 0 [::]:amanda [::]:* LISTEN -
tcp6 0 0 localhost:ipp [::]:* LISTEN -
```

Here is my Amanda service configuration

```
# default: on
# description: The amanda service
{
        only_from       = ubuntu.imparisystems.local
        socket_type     = stream
        protocol        = tcp
        flags           = IPv4
        wait            = no
        user            = backup
        group           = backup
        groups          = yes
        server          = /usr/lib/amanda/amandad
        server_args     = -auth=bsdtcp amdump
        disable         = no
}

```

As you can see, the amanda service is only running under tcp6. I went to the xinet man pages and it says that I can add in flags = IPv4 to force it to run tcp4. However, that doesn't work, and I have restarted xinetd and rebooted the machine for good measure.

I just need to know how to either make my 9.04 client listen to tcp4 or make the server talk on tcp4 and tcp6. Just a pointer to the right package, etc.

---

### Post by gombadi on 2009-06-15
> 
As you can see, the amanda service is only running under tcp6.


Not necessarily.

```

human@zagbot:~$ sudo netstat -pat | grep tcp6
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      5509/sshd       

```

ssh is working fine on ipv4 as well as ipv6 on this machine.

I think you problem may be something else - firewall?

---

### Post by matthewboh on 2009-06-16
That's great for you - but ssh is invoked with a different process.  The problem is not that ipv6 doesn't work at all, my problem is specifically with the amanda service being started up by xinetd and more specifically you are supposed to be able to set the flags = IPv4 in your xinetd service to force it to run on tcp4.

There are no firewalls set up - so nothing is blocking the amanda service.  In fact, on my LAN I have several other boxes that are currently running amanda backups over tcp4.

---

