---
title: "SSH connection timed out"
date: 2013-02-14
forum: Networking &amp; Wireless
---

### Post by MrJones on 2013-02-14
I have two computers, a laptop and a desktop. When trying to log in from my laptop to my desktop via ssh, the connection times out. The other way around works fine. There is no firewall running on either machine and the desktop can ssh itself. Does anyone have any idea how to fix this?

---

### Post by Doug S on 2013-02-14
O.K. so your local test indicates that sshd is running and at least listening to the local interface.
On the desktop computer, is sshd listening on all interfaces? Example:```
doug@s15:~/iso$ [COLOR=red]sudo netstat -plnt[/COLOR]
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1725/mysqld
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      1038/smbd
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN      1949/apache2
tcp        0      0 192.168.122.1:53        0.0.0.0:*               LISTEN      3203/dnsmasq
[COLOR=red]tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      1109/sshd[/COLOR]
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN      1848/master
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN      1949/apache2
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      1038/smbd

```

---

### Post by MrJones on 2013-02-15
This is the output I get:
```

dennis@T160:~$ sudo netstat -plnt
[sudo] password for dennis: 
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      746/smbd        
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      1798/dnsmasq    
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      464/sshd        
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      562/cupsd       
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      746/smbd        
tcp6       0      0 :::139                  :::*                    LISTEN      746/smbd        
tcp6       0      0 :::22                   :::*                    LISTEN      464/sshd        
tcp6       0      0 :::445                  :::*                    LISTEN      746/smbd
```Is that ok?

---

### Post by Doug S on 2013-02-15
Yes, it looks O.K. Perhaps look in /var/log/auth.log and see if there are any clues. You could also increase the LogLevel in sshd_config to try to add more information to /var/log/auth.log. Look for this area:```
# Logging
SyslogFacility AUTH
LogLevel VERBOSE

```see "man sshd_config" for the LogLevel options, maybe DEBUG1 would be enough.

---

### Post by MrJones on 2013-02-15
Well, it doesn't seem to output anything to the log. This is its tail:

```
dennis@T160:~$ tail /var/log/auth.log
Feb 15 18:25:41 T160 lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Feb 15 18:25:41 T160 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Feb 15 18:25:44 T160 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "dennis"
Feb 15 18:25:45 T160 dbus[462]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.26" (uid=104 pid=1871 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.15" (uid=0 pid=1349 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Feb 15 18:25:52 T160 lightdm: pam_unix(lightdm:session): session closed for user lightdm
Feb 15 18:25:52 T160 lightdm: pam_unix(lightdm:session): session opened for user dennis by (uid=0)
Feb 15 18:25:52 T160 lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Feb 15 18:25:55 T160 polkitd(authority=local): Registered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session2 (system bus name :1.39 [/usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1], object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8)
Feb 15 18:26:13 T160 gnome-keyring-daemon[1942]: egg_symkey_generate_simple: assertion `iterations >= 1' failed
Feb 15 18:26:13 T160 gnome-keyring-daemon[1942]: couldn't set environment variable in session: The name org.gnome.SessionManager was not provided by any .service files

```I changed it to loglevel DEBUG3, just to make sure I would get something.

Also, one thing I noticed, I don't have any config files in ~/.ssh/. I don't think it matters though, since the /etc/ssh/ ones will then be used, if I understood the man pages correctly, and those are present. Anything else I can try?

---

### Post by steeldriver on 2013-02-15
Not sure if you mean it times out while trying to connect, or times out at some point after the connection is established? if the former, then have you tried running the *client* with debugging info turned on?

```
ssh -vvv *remotehost*
```

---

### Post by Doug S on 2013-02-15
> There is no firewall running on either machineAre you sure? To observe the iptables, do this:```
sudo iptables -v -x -n -L
```

---

### Post by MrJones on 2013-02-15
The -vvv opstion on the client gave me the same feedback: connection timed out. And it times out while trying to connect, sorry that was unclear.

The iptables command on the desktop gives me this:

```
dennis@T160:~$ sudo iptables -v -x -n -L
[sudo] password for dennis: 
Chain INPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       127.0.0.1            0.0.0.0/0            tcpflags:! 0x17/0x02
     390    33365 ACCEPT     udp  --  *      *       127.0.0.1            0.0.0.0/0           
       0        0 ACCEPT     all  --  lo     *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 10/sec burst 5
       2      108 DROP       all  --  eth0   *       0.0.0.0/0            255.255.255.255     
     243    31607 DROP       all  --  *      *       0.0.0.0/0            192.168.178.255     
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
      11      512 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
       0        0 LSI        all  -f  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 10/min burst 5
    2589  2453018 INBOUND    all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Input"

Chain FORWARD (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 10/sec burst 5
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Forward"

Chain OUTPUT (policy DROP 0 packets, 0 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  *      *       192.168.178.22       127.0.0.1            tcp dpt:53
       0        0 ACCEPT     udp  --  *      *       192.168.178.22       127.0.0.1            udp dpt:53
     390    33365 ACCEPT     all  --  *      lo      0.0.0.0/0            0.0.0.0/0           
       0        0 DROP       all  --  *      *       224.0.0.0/8          0.0.0.0/0           
      21     2453 DROP       all  --  *      *       0.0.0.0/0            224.0.0.0/8         
       0        0 DROP       all  --  *      *       255.255.255.255      0.0.0.0/0           
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0             
       0        0 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0            state INVALID
    2341   260995 OUTBOUND   all  --  *      eth0    0.0.0.0/0            0.0.0.0/0           
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            LOG flags 0 level 6 prefix "Unknown Output"

Chain INBOUND (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
    2369  2430300 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
     200    21140 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
      20     1578 LSI        all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
    pkts      bytes target     prot opt in     out     source               destination         

Chain LSI (2 references)
    pkts      bytes target     prot opt in     out     source               destination         
      20     1578 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
      11      660 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
      11      660 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x02
       0        0 LOG        tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
       0        0 DROP       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcpflags: 0x17/0x04
       0        0 LOG        icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
       0        0 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0            icmptype 8
       9      918 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix "Inbound "
       9      918 DROP       all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 LOG_FILTER  all  --  *      *       0.0.0.0/0            0.0.0.0/0           
       0        0 LOG        all  --  *      *       0.0.0.0/0            0.0.0.0/0            limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix "Outbound "
       0        0 REJECT     all  --  *      *       0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain OUTBOUND (1 references)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           
    1934   234081 ACCEPT     tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
       4      293 ACCEPT     udp  --  *      *       0.0.0.0/0            0.0.0.0/0            state RELATED,ESTABLISHED
     403    26621 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0
```

---

### Post by Doug S on 2013-02-15
O.K. so you do have a firewall and your SSH connection attempt is unable to get through.

---

### Post by MrJones on 2013-02-15
Oh, ok, so that's it. I checked ufw status and it told me inactive, so I assumed there was no firewall active. Thanx for your help!

---

### Post by MrJones on 2013-02-15
I allowed my ip in using firestarter and it's connecting in a sec. Thanx!

---

