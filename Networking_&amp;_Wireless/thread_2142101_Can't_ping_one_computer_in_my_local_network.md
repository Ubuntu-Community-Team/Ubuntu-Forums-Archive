---
title: "Can't ping one computer in my local network"
date: 2013-05-04
forum: Networking &amp; Wireless
---

### Post by Thibaud74 on 2013-05-04
Hi,
I have two computers in my network, a dell and a eeepc. Recently I reinstalled my dell. Now, I can use it to connect to the Internet, but I can't connect the two PCs via ssh anymore. I use autoscan-network from the eeepc that can't find my dell ; and autoscan from my dell can't find eeepc... The two PCs are be able to ping the router and to the Internet, but not between them. Router seems right, and firewalls are down. It seems that it's my dell that has a problem, here are the results of the commands below:

```
iwconfig
eth1      IEEE 802.11abg  ESSID:"freebox_ThiMoMe"                                                                                                                                                                                                                              
          Mode:Managed  Frequency:2.452 GHz  Access Point: C6:8C:76:EB:76:34                                                                                                                                                                                                   
          Retry  long limit:7   RTS thr:off   Fragment thr:off                                                                                                                                                                                                                 
          Power Management:on   


cat /etc/hosts                                                                                                                                                                                       
127.0.0.1       localhost                                                                                                                                                                                                                                                      
127.0.1.1       hulin-Latitude-E5520                                                                                                                                                                                                                                           
192.168.0.12    eeepc                                                                                                                                                                                                                                                          
                                                                                                                                                                                                                                                                               
# The following lines are desirable for IPv6 capable hosts                                                                                                                                                                                                                     
::1     ip6-localhost ip6-loopback                                                                                                                                                                                                                                             
fe00::0 ip6-localnet                                                                                                                                                                                                                                                           
ff00::0 ip6-mcastprefix                                                                                                                                                                                                                                                        
ff02::1 ip6-allnodes                                                                                                                                                                                                                                                           
ff02::2 ip6-allrouters    


cat /etc/hosts.allow 
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#

ALL:127.0.0.1,192.168.0.0/24


cat /etc/hosts.deny 
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5) and hosts_options(5).
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8) and rpc.mountd(8)
# for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.
#
# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID



cat /etc/hostname 
hulin-Latitude-E5520

 cat /etc/host.conf 
# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on



```
 I


Thanks a lot,
Thibaud.

---

### Post by ahallubuntu on 2013-05-04
~

---

### Post by prodigy_ on 2013-05-04
Run the following commands on both machines (as a sanity check):
```
ip addr show
ip route show
sudo iptables -L
```
Post the output here if you can't interpret it yourself.

There's no magic to TCP/IP. If you can't ping a host, it's either wrong ip address/netmask/routing table or firewall blocking traffic.

For SSH you additionally need to run ```
ss -altn
``` to check if anything is listening on the SSH port (default: 22).

---

### Post by Thibaud74 on 2013-05-06
@ahallubuntu: I installed the ssh server after the installation, however I can use ssh to connect to a server on the Internet, but not in my local network.

@prodigy_: here is what I get with the dell :
```
$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN qlen 1000
    link/ether d0:67:e5:41:05:29 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether e4:d5:3d:96:31:a3 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.13/24 brd 192.168.0.255 scope global eth1
    inet6 fe80::e6d5:3dff:fe96:31a3/64 scope link 
       valid_lft forever preferred_lft forever

```
```
$ ip route show
default via 192.168.0.1 dev eth1  proto static 
169.254.0.0/16 dev eth1  scope link  metric 1000 
192.168.0.0/24 dev eth1  proto kernel  scope link  src 192.168.0.13  metric 9 

```
```
$ sudo iptables -L
[sudo] password for hulin: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere  
```
```
$ ss -altn
State       Recv-Q Send-Q                                                                                                       Local Address:Port                                                                                                         Peer Address:Port 
LISTEN      0      5                                                                                                                127.0.0.1:6600                                                                                                                    *:*     
LISTEN      0      50                                                                                                                       *:3306                                                                                                                    *:*     
LISTEN      0      128                                                                                                                      *:42922                                                                                                                   *:*     
LISTEN      0      50                                                                                                                       *:139                                                                                                                     *:*     
LISTEN      0      5                                                                                                                127.0.0.1:23116                                                                                                                   *:*     
LISTEN      0      50                                                                                                               127.0.0.1:6543                                                                                                                    *:*     
LISTEN      0      128                                                                                                                      *:111                                                                                                                     *:*     
LISTEN      0      50                                                                                                               127.0.0.1:6544                                                                                                                    *:*     
LISTEN      0      5                                                                                                                127.0.1.1:53                                                                                                                      *:*     
LISTEN      0      128                                                                                                              127.0.0.1:631                                                                                                                     *:*     
LISTEN      0      100                                                                                                                      *:25                                                                                                                      *:*     
LISTEN      0      128                                                                                                              127.0.0.1:9050                                                                                                                    *:*     
LISTEN      0      32                                                                                                               127.0.0.1:8123                                                                                                                    *:*     
LISTEN      0      128                                                                                                                      *:17500                                                                                                                   *:*     
LISTEN      0      50                                                                                                                       *:445                                                                                                                     *:*     
LISTEN      0      100                                                                                                              127.0.0.1:35327                                                                                                                   *:*     
LISTEN      0      1                                                                                                                127.0.0.1:13666                                                                                                                   *:*     
LISTEN      0      5                                                                                                                127.0.0.1:19876                                                                                                                   *:*     
LISTEN      0      128                                                                                                                     :::43432                                                                                                                  :::*     
LISTEN      0      50                                                                                                                      :::139                                                                                                                    :::*     
LISTEN      0      50                                                                                               fe80::e6d5:3dff:fe96:31a3:6543                                                                                                                   :::*     
LISTEN      0      50                                                                                                                     ::1:6543                                                                                                                   :::*     
LISTEN      0      128                                                                                                                     :::111                                                                                                                    :::*     
LISTEN      0      50                                                                                               fe80::e6d5:3dff:fe96:31a3:6544                                                                                                                   :::*     
LISTEN      0      50                                                                                                                     ::1:6544                                                                                                                   :::*     
LISTEN      0      100                                                                                                                     :::8080                                                                                                                   :::*     
LISTEN      0      128                                                                                                                     :::80                                                                                                                     :::*     
LISTEN      0      128                                                                                                                     :::22                                                                                                                     :::*     
LISTEN      0      128                                                                                                                    ::1:631                                                                                                                    :::*     
LISTEN      0      100                                                                                                                     :::25                                                                                                                     :::*     
LISTEN      0      50                                                                                                                      :::445                                                                                                                    :::*     
LISTEN      0      1                                                                                                         ::ffff:127.0.0.1:8005                                                                                                                   :::*     

```

For the eeepc I do an other post...

---

### Post by Thibaud74 on 2013-05-06
...here are what I get with the eeepc:
```
$ ip addr show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether bc:ae:c5:d0:7c:88 brd ff:ff:ff:ff:ff:ff
3: eth3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 48:5d:60:b5:a2:1a brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.12/24 brd 192.168.0.255 scope global eth3
    inet6 fe80::4a5d:60ff:feb5:a21a/64 scope link 
       valid_lft forever preferred_lft forever
```
```
$ ip route show
default via 192.168.0.1 dev eth3  proto static 
169.254.0.0/16 dev eth3  scope link  metric 1000 
192.168.0.0/24 dev eth3  proto kernel  scope link  src 192.168.0.12  metric 9
```
```
$ sudo iptables -L
[sudo] password for hulin: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere 
```
```
$ ss -altn
State       Recv-Q Send-Q                               Local Address:Port                                 Peer Address:Port 
LISTEN      0      5                                        127.0.0.1:6600                                            *:*     
LISTEN      0      5                                                *:4713                                            *:*     
LISTEN      0      50                                               *:3306                                            *:*     
LISTEN      0      50                                               *:139                                             *:*     
LISTEN      0      128                                              *:111                                             *:*     
LISTEN      0      128                                              *:43792                                           *:*     
LISTEN      0      5                                        127.0.1.1:53                                              *:*     
LISTEN      0      128                                              *:22                                              *:*     
LISTEN      0      128                                      127.0.0.1:631                                             *:*     
LISTEN      0      100                                              *:25                                              *:*     
LISTEN      0      128                                      127.0.0.1:9050                                            *:*     
LISTEN      0      32                                       127.0.0.1:8123                                            *:*     
LISTEN      0      128                                              *:17500                                           *:*     
LISTEN      0      50                                               *:445                                             *:*     
LISTEN      0      5                                                *:16001                                           *:*     
LISTEN      0      1                                        127.0.0.1:13666                                           *:*     
LISTEN      0      5                                               :::4713                                           :::*     
LISTEN      0      50                                              :::139                                            :::*     
LISTEN      0      128                                             :::54349                                          :::*     
LISTEN      0      128                                             :::111                                            :::*     
LISTEN      0      128                                             :::80                                             :::*     
LISTEN      0      128                                             :::22                                             :::*     
LISTEN      0      128                                            ::1:631                                            :::*     
LISTEN      0      100                                             :::25                                             :::*     
LISTEN      0      50                                              :::445                                            :::*     
LISTEN      0      5                                               :::16001                                          :::*     

```

PS: I'm interesting to understand how to interpret the output..

Thanks,
Thibaud.

---

### Post by prodigy_ on 2013-05-10
SSH server on your Dell machine isn't bound to IPv4. Check your **/etc/ssh/sshd_config** or use IPv6 explicitly. Example (using link-local IP from your output):
```
 ssh -6 fe80::e6d5:3dff:fe96:31a3%eth3
```

---

### Post by Thibaud74 on 2013-05-10
The command ipv6 successes but not between the two computers.
Other information maybe interesting ? When I launch autoscan-network, I get an error with snmp:
```

Cannot find module (SNMPv2-MIB): At line 0 in (none)
Cannot find module (SNMPv2-SMI): At line 0 in (none)

```
Is this information useful ?

---

### Post by prodigy_ on 2013-05-10
Well, you don't have to use IPv6. You could but configuring IPv6 is usually more complex than binding SSH to IPv4. For the latter you need to perform three steps:

1) Ensure that your Dell machine either has static IP addresses or you can resolve its IPs by name (via /etc/hosts, DNS or [zeroconf](https://help.ubuntu.com/community/HowToZeroconf)). Ping the Dell machine by IP (if you set up static IP) or by name (if you set up name resolution).
2) Ensure that SSH server is bound to IPv4. Open sshd_config in text editor (e.g. **sudo nano /etc/ssh/sshd_config**) and see if there's **AddressFamily** option. Comment it out or remove. For more info see ```
man sshd_config
```
3) Reload SSH server to apply changes: ```
sudo service ssh reload
``` and check with ss. Example (assuming port 22): ```
ss -altn | grep ':22[\t ]'
``` Expected output: ```
LISTEN      0      128                                              *:22                                              *:*     
LISTEN      0      128                                             :::22                                             :::* 
```

---

### Post by prodigy_ on 2013-05-10
edit: double post

---

### Post by Thibaud74 on 2013-05-12
My router automaticly gives a static ip by hardware address. I suppose that I can't ping my dell, so my dell can't be reach by ssh. In fact, ssh from the dell to my university works fine only.
```

$ ss -altn | grep ':22[\t ]'
LISTEN     0      128                      :::22                      :::*
```
And here's my sshd_config :
```

Port 22
ListenAddress ::
Protocol 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
UsePrivilegeSeparation yes
KeyRegenerationInterval 3600
ServerKeyBits 768
SyslogFacility AUTH
LogLevel INFO
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes
IgnoreRhosts yes
RhostsRSAAuthentication no
HostbasedAuthentication no
PermitEmptyPasswords no
ChallengeResponseAuthentication no
PasswordAuthentication yes
X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
AcceptEnv LANG LC_*
Subsystem sftp /usr/lib/openssh/sftp-server
UsePAM yes

```

---

### Post by Thibaud74 on 2013-05-14
Solved ! Here is what I did :
```
rm -R $HOME/.autoscan-network
```
Now my network is no more hidden with autoscan-network
I deleted my wifi connexion (I'm not sure but maybe my connexion with eth worked).
Now my ssh connexion is working but not in both directions.
I comment ListenAddress :: in /etc/ssh/sshd_config. Strange, I thought that I had to let it.
I don't understand all but that works now.
Thanks for your help !

All the best,
Thibaud.

---

