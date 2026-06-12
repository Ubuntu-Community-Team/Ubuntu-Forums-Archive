---
title: "SSH Tunneling"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by fhsm on 2012-05-03
**Background**
I have a work and a home PC that are behind NAT firewalls. I have a  server that is accessible via the public internet. All three systems are ubuntu and all three have sshd installed and working. I want to use the server to do bootleg NAT traversal so I can ssh from work to home.

**Setup**
*Server*
I can SSH to the server from either PC. Other than the usual blocking root, requiring certificates, changing ports the only change I've made to the server was sshd_config:
```
GatewayPorts yes
```
*Home PC*
Establish a tunnel from server port 22222 to home PC port 22, by running:
```
ssh -R 22222:localhost:22 server_user@my.server.com
```
*Work PC*
Connect to the previously established tunnel, using:
```
ssh home_user@my.server.com -p 22222
```

The principle is quite simple and by no means new or original (referencing the attached diagram): I establish the green tunnel across my home NAT from my home PC and then follow that tunnel back to my home PC from my work PC via my server over the internet. 

**Problem**
It doesn't work. After trouble shooting it I've worked out that the problem is in *hosts.allow / hosts.deny*. If I set *sshd: ALL* in hosts.allow on my home PC the connection goes without a hitch. If instead of allowing all I allow any of:
[LIST]
[*]server ip
[*]work public ip
[*]work pc LAN ip
[*]home public ip
[*]home pc LAN ip
[*]home LAN subnet
[*]localhost
[*]127.0.0.1
[/LIST]
I cannot connect to the tunnel. I can't even connect to it by ssh-ing to my server and then trying to connect with *server> ssh home_user@localhost -p 22222*. After a lot of digging around I realized that I could make it work by setting *sshd: <home_pc_hostname>* in hosts.allow.

**Question**
WTF? As I'd expect my home pc is seeing the connection coming from  it's own interface but why does hostname and only host name get the traffic past the hosts allow? It seems like one of localhost, 127..., LAN IP should have worked. Can someone please explain this?

---

