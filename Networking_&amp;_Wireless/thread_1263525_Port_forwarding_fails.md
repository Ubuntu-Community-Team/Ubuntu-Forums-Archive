---
title: "Port forwarding fails"
date: 2009-09-11
forum: Networking &amp; Wireless
---

### Post by izziere on 2009-09-11
Friends, I had a server running fine but then I moved.  I was no longer on cable but moved to ADSL.  I had two ADSL router modems - one old and one new.  Both failed to work port forwarding properly.

Using public IP address from the web I simply get the web interface for the router.  Even using other ports that Port 80 (plus after I changed the router web interface from Port 80) I cannot get past the router.

I can access all open ports on the server by using local IP address.

There is no firewall in place and port forwarding on router has been set up in full accordance with the instructions.  I update firmware on new router to see if it solved and it fried the router, so am back to using an old BT Voyager 2000 router - though it still work for all other purposes.  To be clear, though, both old and new routers failed to work.

Out put of netstat as follows:

```
$ sudo netstat -taunp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:993             0.0.0.0:*               LISTEN      5050/dovecot    
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN      -               
tcp        0      0 0.0.0.0:48648           0.0.0.0:*               LISTEN      4941/rpc.mountd 
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      4425/mysqld     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      4974/smbd       
tcp        0      0 0.0.0.0:41805           0.0.0.0:*               LISTEN      3942/rpc.statd  
tcp        0      0 0.0.0.0:143             0.0.0.0:*               LISTEN      5050/dovecot    
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN      3923/portmap    
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      4018/apache2    
tcp        0      0 0.0.0.0:56278           0.0.0.0:*               LISTEN      -               
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN      4864/exim4      
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      4018/apache2    
tcp        0      0 192.168.1.108:139       192.168.1.202:1040      ESTABLISHED 9971/smbd       
tcp6       0      0 :::2222                 :::*                    LISTEN      9774/sshd       
tcp6       0   1872 192.168.1.108:2222      192.168.1.122:40484     ESTABLISHED 9972/sshd: ianmat [
udp        0      0 0.0.0.0:2049            0.0.0.0:*                           -               
udp        0      0 192.168.1.108:137       0.0.0.0:*                           4972/nmbd       
udp        0      0 0.0.0.0:137             0.0.0.0:*                           4972/nmbd       
udp        0      0 192.168.1.108:138       0.0.0.0:*                           4972/nmbd       
udp        0      0 0.0.0.0:138             0.0.0.0:*                           4972/nmbd       
udp        0      0 0.0.0.0:42122           0.0.0.0:*                           3942/rpc.statd  
udp        0      0 0.0.0.0:59281           0.0.0.0:*                           -               
udp        0      0 0.0.0.0:42196           0.0.0.0:*                           4941/rpc.mountd 
udp        0      0 0.0.0.0:726             0.0.0.0:*                           3942/rpc.statd  
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           4340/avahi-daemon: 
udp        0      0 0.0.0.0:111             0.0.0.0:*                           3923/portmap    
udp        0      0 0.0.0.0:42227           0.0.0.0:*                           4340/avahi-daemon: 
udp        0      0 192.168.1.108:123       0.0.0.0:*                           9813/ntpd       
udp        0      0 127.0.0.1:123           0.0.0.0:*                           9813/ntpd       
udp        0      0 0.0.0.0:123             0.0.0.0:*                           9813/ntpd       
udp6       0      0 fe80::217:3fff:fef5:123 :::*                                9813/ntpd       
udp6       0      0 ::1:123                 :::*                                9813/ntpd       
udp6       0      0 :::123                  :::*                                9813/ntpd       

```

I can successfully ping the public IP address.  Using nmap and the public IP it only finds the few open ports on the router, ie it is not 'seeing' the virtual server/port forwarding.

I am wondering whether it is the server-side settings.

Any ideas, please

---

### Post by izziere on 2009-09-13
Bump.  Now, don't all rush at once!

---

### Post by cariboo on 2009-09-13
Are you trying to check internally, as in your own network, or from a different location? One of the easiest ways to check port forwarding is to use [canyouseeme]("http://canyouseeme.org"), it may be your isp is blocking some of the ports you want to use.

---

### Post by izziere on 2009-09-13
Nope.  ISP is not blocking Port 80 as I can access my router control panel externally, if I set it to be on Port 80.  I have also tried forwarding public port nnnn to server Port 80 and that also fails.

Interestingly, the site you suggested can see my IMAP port, hence I think it is a configuration issue.

---

