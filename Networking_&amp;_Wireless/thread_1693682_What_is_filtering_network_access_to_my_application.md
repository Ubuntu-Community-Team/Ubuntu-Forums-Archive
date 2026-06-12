---
title: "What is filtering network access to my application (ftpd)?"
date: 2011-02-23
forum: Networking &amp; Wireless
---

### Post by krajcatomas@seznam.cz on 2011-02-23
Hi,

I have recently come across a weird problem with ubuntu server. I run ubuntu 10.04. Something is filtering network access to my application and I have no clue what it could be. If anyone could make any suggestions how to find out or how to unblock it, it would be great.

I need to get ftp access working (port 21). I installed and configured vsftpd. I can login from localhost without any problems. I can't log in from the network (timeout).

 I can see with netstat that it's listening correctly

```

root@socialsmart:/home/tomask# netstat -tupln
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4789/mysqld     
tcp        0      0 127.0.0.1:11211         0.0.0.0:*               LISTEN      562/memcached   
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      23552/apache2   
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      22868/vsftpd    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      8670/sshd       
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN      492/postgres    
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      648/master      
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      23552/apache2   
tcp        0      0 0.0.0.0:3333            0.0.0.0:*               LISTEN      23747/nc        
tcp6       0      0 :::22                   :::*                    LISTEN      8670/sshd       
udp        0      0 0.0.0.0:68              0.0.0.0:*                           275/dhclient3   
udp        0      0 127.0.0.1:11211         0.0.0.0:*                           562/memcached   

```

Other applications such as apache or sshd which I installed before work without problems. Also, I flushed several times iptables which didn't help either

```

root@socialsmart:/home/tomask# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

```

I also tried opening a listening port with netcat

```

yes|nc -l 3333

```Not reachable from the network either.

Nmap:
```

jumbo@jumbo-asusK52F:~$ nmap -sT -p21 socialsmartprod

Starting Nmap 5.21 ( http://nmap.org ) at 2011-02-23 22:57 EST
Nmap scan report for socialsmartprod (174.129.32.87)
Host is up (0.30s latency).
PORT   STATE    SERVICE
21/tcp filtered ftp


```I am really stuck because I have already checked all the logs, possible firewalls and so on. I am pretty sure there is no blocking firewall on the way from me to the server. I would be really grateful to anyone who could give me some clue.

Thanks,
Tomas

---

### Post by krajcatomas@seznam.cz on 2011-02-24
All right, so finally I cracked it.

The ubuntu server is hosted on Amazon Web Services and there is a default amazon firewall (Security groups) in the web administration. This firewall was blocking all the requests to my ports.

Cheers

---

