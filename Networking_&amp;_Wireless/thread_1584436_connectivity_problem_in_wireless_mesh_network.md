---
title: "connectivity problem in wireless mesh network"
date: 2010-09-29
forum: Networking &amp; Wireless
---

### Post by mpmobvisnoob on 2010-09-29
hi there,

can MODs please move this to an appropriate thread if necessary,i couldnt find anything similar to the problem I have.

I have a HTC Legend, rooted using Pauls method(MoDaCo) (giving it a "generic 1.31 series based ROM that has Superuser access").

We recently managed to write create an application that switches the phone into wireless ad-hoc mode, and starts the B.A.T.M.A.N. mesh routing software as a service(thanks to the work done on android wireless tether app). This application allows the HTC to join/create a mesh network with any other mesh routers within range. My testbed consists of 3 mesh routers also running B.A.T.M.A.N., and my ubuntu lucid machine running a visualization server for B.A.T.M.A.N. networks.

So, this is the situation I have:
-the visualization server picks up the HTC and the 3 mesh routers.
-visualization server can ping and ssh into the mesh routers, using either password or public/private key authentication(manually distributing the keys), and the mesh routers can do the same
-the HTC can ping the visualization server and the 3 mesh routers via tiwlan0.
-the HTC did not have an ssh server/client, so I installed busybox, dropbear and ssh(ssh-daemon-dropbear from droidforums)
-I have tested the ssh client by trying to "ssh [EMAIL="root@10.130.1.xxx"]root@10.130.1.xxx[/EMAIL]" xxx=254 being the IP address of the HTC.I am prompted for a password and it accepts and "logs me in".so I assume i correctly configured dropbear, and the ssh client.
-even though the ssh server/client are "working" i expected that i would be able to ssh into and out of the HTC from other devices on the 10.130.1.xxx subnet(ssh/scp out would be more important as i plan to configure mesh routers using the HTC).this has failed, and I am stuck at this point.

these are some of the things i've done so far:**(wlan=10.130.1.xxx subnet)**
1. i started dropbear using the command:
dropbear -A -N root -U 0 -G 0 -C <password> -p wlan.254:22

2. i checked if dropbear is running:
busybox netstat -l                                          
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 wlan.254:22        0 0 0 0:*               LISTEN      
                    
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     379    @jdwp-control

3. I have disabled the firewall and added rules to accept connections from/to my wlan/mesh:
iptables -F
iptables -A INPUT   -j ACCEPT -p all -s wlan.0/24 -i tiwlan0
iptables -A OUTPUT  -j ACCEPT -p all -d wlan.0/24 -o tiwlan0 

4. the results from a ping on one of the routers on the mesh:
# ping -I tiwlan0 wlan.80
PING wlan.80 (wlan.80) from wlan.254 tiwlan0: 56(84) bytes of data.
64 bytes from wlan.80: icmp_seq=1 ttl=64 time=3.38 ms
64 bytes from wlan.80: icmp_seq=2 ttl=64 time=5.73 ms
64 bytes from wlan.80: icmp_seq=3 ttl=64 time=5.28 ms
^C
--- 10.130.1.80 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 3.387/4.801/5.737/1.018 ms

5. the attempt to ssh into the HTC
# ssh root@wlan.254                                       
ssh: Warning: failed creating //.ssh: Read-only file system

Host 'wlan.254' is not in the trusted hosts file.
(fingerprint md5 f1:a5:1a:d9:64:39:31:41:3c:cc:88:4c:a0:1d:a7:4f)
Do you want to continue connecting? (y/n) y
root@wlan.254's password: 

6. the failed attempt to ssh
# ssh root@wlan.80
ssh: exited: Error connecting: Network is unreachable

the error with ssh is prompting me to think that there is direct route from the HTC into the wlan/mesh. which is strange since I can ping devices via tiwlan0. my other assumption is that the ssh client/server are not listening/recognizing tiwlan0 as a having a route in and out of the 10.130.1.xxx subnet.i know this is not how it works, but, is there a way to "ssh -I tiwlan0" i.e. specify which interface to use. A better question is how can I establish a route into the subnet given the configuration described above.Am i missing something obvious here?

Regards.

---

