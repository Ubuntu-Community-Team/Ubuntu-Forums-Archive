---
title: "ssh connecting sql on bespoke ports"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by zippy5166 on 2013-03-05
I have inhertited a system where I want to connect 2 mqsql databases one on 

server A to one on server B the documentation says I need port 4036 on 

system A (a 32 bit ununtu server) to port 3036 on system B a Centos 64 bit 

server

 both are on the same lan
Ive tried ssh -N -L 4036:localhost:3036 serverb and after some time it times 
out sayng 
connection timed out on port 22!!

running ssh in verbose mode i get :
debug1: Connecting to x.x.0.x [x.x.0.x] port 3036.
debug1: Connection established.
debug1: permanently_set_uid: 0/0
debug1: identity file /root/.ssh/id_rsa type -1
debug1: identity file /root/.ssh/id_rsa-cert type -1
debug1: identity file /root/.ssh/id_dsa type -1
debug1: identity file /root/.ssh/id_dsa-cert type -1
debug1: identity file /root/.ssh/id_ecdsa type -1
debug1: identity file /root/.ssh/id_ecdsa-cert type -1
ssh_exchange_identification: Connection closed by remote host



if I try and connect from server B to 
server A I can establish tunnels but 
not on the right ports but only using 
ssh -D

also when i do ssh -D 3036 <ipadressofsystemA> it starts a 
tunnel ie it logs 
on remotely
 same when i try ssh-D 4036
 netstat 
-NT| grep your ip:22 on system B shows that tunnels do establish

I have 
checked the firewall on server B

Im pretty sure that default port for 
mysql is 3306 but my sql files seem to 
suggest 3036 is the port I 
need

so my questions are my sql doesnt seem to be conncting from system A 
to 
system B and I can only get tunnels with the right destination port not 
the 
right port
 Im new to linux as you may have gathered so much of this 
ive gleened from 
reading forums so this is my first post so want to know 
where to start crack 
this problem please

---

### Post by zippy5166 on 2013-03-10
Ive not reset keys & cheked port settings and things look alot better .I now get this

debug1: Authentication succeeded (password).
Authenticated to x.y.z.10 ([x.y.z.10]:3036).
debug1: Local connections to LOCALHOST:4036 forwarded to remote address localhost:3036
debug1: Local forwarding listening on ::1 port 4036.
bind: Address already in use
debug1: Local forwarding listening on 127.0.0.1 port 4036.
bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 4036
Could not request local forwarding.
debug1: Requesting [email]no-more-sessions@openssh.com[/email]
debug1: Entering interactive session.
 This makes me think that the tunnel is trying to start. On the other machine netstat -nt shows me that a tunnel on the target mahine with port 3036 is coming form teh source machine with port 39522

---

