---
title: "Unable to ssh to machine. Outbound ssh works. sshd is running on port 22."
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by Mike Buksas on 2013-05-27
I have an Ubuntu 12.10 machine on my LAN to which all ssh connections time out. Let's call it 'F' (for fail!)

Two other machines 'A' and 'B' on the same LAN can connect to each other. I can also ssh from F to A. So I don't believe there is a network config issue. The problem seems to be confined to machine F.

Following various other forums answers, I've verified and tried the following.

Verify sshd is running and listening on port 22:

```

F$ ps -A | grep sshd
853 ?        00:00:00 sshd

F$ sudo ss -lnp | grep sshd
LISTEN     0      128                      :::22                      :::*      users:(("sshd",4244,4))
LISTEN     0      128                       *:22                       *:*      users:(("sshd",4244,3))

F$ sudo lsof -i | grep ssh
sshd      4244    root    3u  IPv4  53321      0t0  TCP *:ssh (LISTEN)
sshd      4244    root    4u  IPv6  53323      0t0  TCP *:ssh (LISTEN)
ssh       5244 michael    3u  IPv4  82208      0t0  TCP localhost:40209->cubebot:ssh (ESTABLISHED)
sshd      5245    root    3u  IPv4  83301      0t0  TCP cubebot:ssh->localhost:40209 (ESTABLISHED)
sshd      5362 michael    3u  IPv4  83301      0t0  TCP cubebot:ssh->localhost:40209 (ESTABLISHED)

F$ netstat -nat | grep 22
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN     
tcp        0      0 192.168.1.28:41782      74.125.225.209:443      ESTABLISHED
tcp        0      0 192.168.1.28:47576      74.125.142.125:5222     ESTABLISHED
tcp        0      0 192.168.1.28:54925      91.189.89.122:443       ESTABLISHED
tcp        0      0 192.168.1.28:54762      74.125.225.167:443      ESTABLISHED
tcp        0      0 192.168.1.28:48473      74.125.225.181:443      ESTABLISHED
tcp        0      0 192.168.1.28:36177      74.125.225.198:443      ESTABLISHED
tcp6       0      0 :::22                   :::*                    LISTEN     

```

Try telnet:

```

A$ telnet F 22
Trying 192.168.1.28...
telnet: Unable to connect to remote host: Connection timed out

```

The same thing happens with ssh.  The IP address for F is correct:

```

F$ ifconfig
wlan1     Link encap:Ethernet  HWaddr 00:1a:70:3b:58:2e  
          inet addr:192.168.1.28  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:70ff:fe3b:582e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22070 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15344 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12137460 (12.1 MB)  TX bytes:2564022 (2.5 MB)

```

The hosts look correct:
```

F$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	cubebot

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

Where cubebot is machine 'F' and the hostname is correct:

```

$ cat /etc/hostname
cubebot

```

Using localhost and hostname on machine F both work:
```

F$ ssh localhost
Welcome to Ubuntu 12.10 (GNU/Linux 3.5.0-31-generic x86_64)

F$ ssh cubebot
Welcome to Ubuntu 12.10 (GNU/Linux 3.5.0-31-generic x86_64)

```

I'm completely out of ideas (and helpful links) at this point. Any/All suggestions, hints, or encouraging words of sympathy would be appreciated at this point!

Cheers,
Mike

Edit: Adding ssh debug output:
```

$ ssh -vvv cubebot
OpenSSH_6.0p1 Debian-3ubuntu1, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to cubebot [192.168.1.28] port 22.
debug1: connect to address 192.168.1.28 port 22: Connection timed out
ssh: connect to host cubebot port 22: Connection timed out

```

Edit: Adding iptables output:

```

F$ sudo iptables -v -x -n -L
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
      65     8910 ACCEPT     tcp  --  *      *       127.0.1.1            0.0.0.0/0            tcpflags:! 0x17/0x02
    5221   550165 ACCEPT     udp  --  *      *       127.0.1.1            0.0.0.0/0           
    5610   386390 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       4      336 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 10/sec burst 5
    2482   446197 DROP       all  --  wlan1  *       0.0.0.0/0            255.255.255.255     
    2189   377221 DROP       all  --  *      *       0.0.0.0/0            192.168.1.255       
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
      16      640 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
       0        0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 10/min burst 5
  679215 977324369 INBOUND    all  --  wlan1  *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Input"

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 10/sec burst 5
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Forward"

Chain OUTPUT (policy DROP 626 packets, 106145 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       192.168.1.28         127.0.1.1            tcp dpt:53
       0        0 ACCEPT     udp  --  *      *       192.168.1.28         127.0.1.1            udp dpt:53
   10896   945465 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
      65     4012 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
  388572 21733125 OUTBOUND   all  --  *      wlan1   0.0.0.0/0            0.0.0.0/0           
     626   106145 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
     626   106145 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Output"

Chain INBOUND (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
  673496 976737119 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    5643   582237 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       0        0 ACCEPT     all  --  *      *       192.168.1.14         0.0.0.0/0           
      76     5013 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
      76     5013 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      44     2640 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
      44     2640 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x02
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x04
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
       0        0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
      32     2373 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
      32     2373 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix "Outbound "
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       4      336 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
  379432 21049049 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
     331    25140 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
    8805   658600 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

```

---

### Post by papibe on 2013-05-27
Hi Mike Buksas.

Could you post the output of an attempt to connect to F from either A or B using the triple verbose option?
```
A$ ssh -vvv F
```
Regards.

---

### Post by Mike Buksas on 2013-05-27
Here it is papibe,

```

A$ ssh -vvv F
OpenSSH_6.0p1 Debian-3ubuntu1, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to cubebot [192.168.1.28] port 22.
debug1: connect to address 192.168.1.28 port 22: Connection timed out
ssh: connect to host cubebot port 22: Connection timed out

```

---

### Post by Doug S on 2013-05-27
I wonder if there is some firewall running, preventing a new incoming connection to "F" on port 22? Perhaps check with and post results from:```
sudo iptables -v -x -n -L
```

---

### Post by Mike Buksas on 2013-05-27
Doug,

I've added to output at the bottom of the question. Thanks.

---

### Post by Doug S on 2013-05-27
So you are running a firewall and, if I read it right, it is not allowing a new incoming SSH connection. I am reasonably sure you are running some sort of front end to iptables. I am much less sure that the front end is firestarter (going only by how the code looks). Firestarter is pretty old and not generally supported or recommended anymore. ... Anyway, you need to allow the incoming new TCP session to port 22.

---

### Post by Mike Buksas on 2013-05-27
> **Doug S said:**
> So you are running a firewall and, if I read it right, it is not allowing a new incoming SSH connection. I am reasonably sure you are running some sort of front end to iptables. I am much less sure that the front end is firestarter (going only by how the code looks). Firestarter is pretty old and not generally supported or recommended anymore. ... Anyway, you need to allow the incoming new TCP session to port 22.

Ah-ha! I had forgotten that firestarter was even installed. Removing firestarter and a quick reboot and the problem is gone.

Thanks!

---

