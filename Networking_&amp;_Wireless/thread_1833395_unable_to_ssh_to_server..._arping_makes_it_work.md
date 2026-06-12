---
title: "unable to ssh to server... arping makes it work?"
date: 2011-08-25
forum: Networking &amp; Wireless
---

### Post by chadrebuck on 2011-08-25
I can't ssh to a pc on the same lan segment until after I do an arping to the server.

This is the ssh version running on the Ubuntu server
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010

This is the ssh version on the Arch client
OpenSSH_5.8p2, OpenSSL 1.0.0d 8 Feb 2011

I've tried these options in the server /etc/ssh/sshd_config, but they haven't helped

GSSAPIAuthentication no
UseDNS no

Reverse dns look up from the server using dig -x ip address of client ip always seems to come back immediately.

I don't know why I tried arping to the server but it seems to do the trick everytime.  Then I can log out of the server and ssh back in immediately

root@desktop-linux-pc:~# uname -a
Linux desktop-linux-pc 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 athlon i386 GNU/Linux

Last login: Thu Aug 25 12:46:37 2011 from 192.168.1.6
[chadr@pogo ~]$ ssh 192.168.1.100        
^C


[chadr@pogo ~]$ ssh -vvv 192.168.1.100
OpenSSH_5.8p2, OpenSSL 1.0.0d 8 Feb 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.100 [192.168.1.100] port 22.
^C


[chadr@pogo ~]$ ping 192.168.1.100       
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_req=1 ttl=64 time=1.29 ms
64 bytes from 192.168.1.100: icmp_req=2 ttl=64 time=1.07 ms
64 bytes from 192.168.1.100: icmp_req=3 ttl=64 time=1.07 ms
^C
--- 192.168.1.100 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.075/1.149/1.295/0.106 ms


[chadr@pogo ~]$ ssh -vvv 192.168.1.100
OpenSSH_5.8p2, OpenSSL 1.0.0d 8 Feb 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.100 [192.168.1.100] port 22.
^C

[chadr@pogo ~]$ su
Password: 
[root@pogo chadr]# arping 192.168.1.100
ARPING 192.168.1.100 from 192.168.1.150 eth0
Unicast reply from 192.168.1.100 [00:1A:92:15:41:FF]  0.683ms
Unicast reply from 192.168.1.100 [00:16:B6:44:4C:33]  1.537ms
Unicast reply from 192.168.1.100 [00:16:B6:44:4C:33]  0.965ms
Unicast reply from 192.168.1.100 [00:16:B6:44:4C:33]  0.950ms
^CSent 3 probes (1 broadcast(s))
Received 4 response(s)

[root@pogo chadr]# exit
[chadr@pogo ~]$ ssh -vvv 192.168.1.100
OpenSSH_5.8p2, OpenSSL 1.0.0d 8 Feb 2011
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.100 [192.168.1.100] port 22.
debug1: Connection established.


when I run arp on the server it doesn't really have many devices shown.  It has an entry for the router and  an entry for the ssh client at 192.168.1.150, but that is it.

root@desktop-linux-pc:~# arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.1              ether   00:22:3f:08:a7:6a   C                     eth0
192.168.1.150            ether   00:25:31:00:a3:c9   C                     eth0

root@desktop-linux-pc:~# netstat -an |less
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.100:22        192.168.1.150:55940     ESTABLISHED
tcp        0      0 192.168.1.100:48326     206.41.8.78:80          ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::1:631                 :::*                    LISTEN     
udp        0      0 0.0.0.0:5353            0.0.0.0:*                          
udp        0      0 0.0.0.0:34190           0.0.0.0:*                          
udp6       0      0 :::5353                 :::*                               
udp6       0      0 :::41998                :::*                            


here is the client arp and netstat

[chadr@pogo ~]$ arp
Address                  HWtype  HWaddress           Flags Mask            Iface
192.168.1.12             ether   00:1a:92:15:41:ff   C                     eth0
192.168.1.4              ether   00:25:d3:d6:98:12   C                     eth0
192.168.1.100            ether   00:1a:92:15:41:ff   C                     eth0
192.168.1.6              ether   00:1f:3c:a5:96:81   C                     eth0
192.168.1.1              ether   00:22:3f:08:a7:6a   C                     eth0
192.168.1.200            ether   00:1e:2a:bf:0c:e9   C                     eth0
192.168.1.7              ether   00:1e:c2:4a:ab:96   C                     eth0

[chadr@pogo ~]$ netstat -an | less
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN      
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      
tcp        0     40 192.168.1.150:22        192.168.1.6:3965        ESTABLISHED 
tcp        0      0 192.168.1.150:55940     192.168.1.100:22        TIME_WAIT   
tcp        0      0 :::80                   :::*                    LISTEN      
tcp        0      0 :::22                   :::*                    LISTEN      
tcp        0      0 :::631                  :::*                    LISTEN      
udp        0      0 0.0.0.0:631             0.0.0.0:*                           
udp        0      0 192.168.1.150:123       0.0.0.0:*                           
udp        0      0 127.0.0.1:123           0.0.0.0:*                           
udp        0      0 0.0.0.0:123             0.0.0.0:*                           
udp        0      0 fe80::225:31ff:fe00:123 :::*                                
udp        0      0 ::1:123                 :::*                                
udp        0      0 :::123                  :::*    

Thanks in advance for any suggestions

---

### Post by chadrebuck on 2011-08-30
oops, found that I already had another device at 192.168.1.100.  I changed the ip of the ubuntu server and it works as expected now.  I should have paid more attention to the arp table on my router since it made it obvious there were multiple mac entries for a single ip address.

---

