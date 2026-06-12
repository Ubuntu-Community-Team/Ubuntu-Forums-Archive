---
title: "SSH connection refused"
date: 2011-05-24
forum: Networking &amp; Wireless
---

### Post by bonda.p on 2011-05-24
After going through a lot of threads, I'm still not able to find out where the problem is. The inputs and outputs are:
pre@pre-Inspiron-N4010:~$ sudo netstat -nap | grep :22
[sudo] password for pre: 
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      3737/sshd       
tcp        0      0 10.129.41.225:47356     10.129.41.225:22        ESTABLISHED 4186/ssh        
tcp        0      0 10.129.41.225:22        10.129.41.225:47356     ESTABLISHED 4187/sshd: pre [pri
tcp6       0      0 :::22 


/etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server sshd                                    Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Could not load host key: /etc/ssh/ssh_host_ecdsa_key

ifconfig

eth0      Link encap:Ethernet  HWaddr f0:4d:a2:59:1a:a2  
          inet addr:10.129.41.225  Bcast:10.129.255.255  Mask:255.255.0.0
          inet6 addr: fe80::f24d:a2ff:fe59:1aa2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:206766 errors:0 dropped:1447 overruns:0 frame:0
          TX packets:76137 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:143723744 (143.7 MB)  TX bytes:8311316 (8.3 MB)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70495 (70.4 KB)  TX bytes:70495 (70.4 KB)

virbr0    Link encap:Ethernet  HWaddr d6:3c:d1:f0:2a:58  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:8169 (8.1 KB)
 Still, I'm unable to ping another machine at 10.129.169.171.

---

