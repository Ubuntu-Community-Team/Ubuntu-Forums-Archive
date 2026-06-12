---
title: "Two Nics, Two internet Connections"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by xomikronx on 2011-04-01
__I've googled everywhere and even looked at Man pages....  but no help.


I have my server box with two NICS.

Let me draw a diagram


Internet
|
|
|
Switch01 ----------Router01 (ip = 192.x.x.x)
(10.x.x.x)           |
|                    |
|                    |
|                    |
-------------------Server01 (eth1 IP= 10.x.x.x)
                            (eth0 IP= 192.168.x.x) 

**I can't get it to display right, Router01 is also connected to Server01**


I know, but this is the only way to setup the Hardware at the moment. Both NICs have internet but I'm assuming my issue would be routing.  

I need computers on 10.x.x.x to use eth1
and computers on 192.168.x.x to use eth0

I need to server to be accessible from 192.x.x.x and 10.x.x.x networks.

Can someone please help me get this to work? Or if it's even optimal to operate like this?

---

### Post by Razorback on 2011-04-01
<delete>

---

### Post by Fire_Chief on 2011-04-01
First, is the router device also running a firewall or NAT?

Second, if this is just a file server or some standalone service system, then the optimal configuration would put the server in the 10.x.x.x network only. The clients in the 192.x.x.x network would reach the server anyway since they would be passing through the router to reach the 10.x.x.x network.

This setup will work as long as the server does not need to initiate communication with any device on the 192.x.x.x network.

It would look like this...

Internet
  |
  |
Switch ----- Server (10.x.x.x)
  |  |
  |  |------ Clients (10.x.x.x)
  |  
Router
  |
  |
Other clients (192.x.x.x)

Cheers!

---

### Post by xomikronx on 2011-04-01
It's a pxe server for imaging and also a SMB server.

I need to access it from the 10.x.x.x mainly for configuration and SMB.

I need to access it from the 192.168.x.x for the PXE service. ( It would be initiating the comm in this case.)

---

### Post by Fire_Chief on 2011-04-01
Ah. So PXE is not normally initiated from a server end. The PXE boot client on the PC makes the request to a PXE server based on information it gets from DHCP configured options. In theory, you should be able to point that to the server in the 10.x.x.x network. I haven't tested this kind of setup though.

Your other option is to leave the server dual homed but configure only 1 gateway (probably easiest on the 10.x.x.x network segment).

Network would still look like you originally described but the server would consider the 192.x.x.x network to be local only and not a route to reach the Internet (no gateway configured).


[INDENT][INDENT]|--------------(10.x.x.x)Server01(192.x.x.x)[/INDENT][/INDENT]
[INDENT][INDENT]|[/INDENT][/INDENT]
Internet-----Switch --------(10.x.x.x)Router01(192.x.x.x)-----Clients
[INDENT][INDENT]|[/INDENT][/INDENT]
[INDENT][INDENT]|----(10.x.x.x)Clients[/INDENT][/INDENT]

Cheers!

---

### Post by xomikronx on 2011-04-01
My problem is that I don't have the access on the 10.x.x.x, as far as configuration.  So I have to configure the dhcp server on the 192.x.x.x part to get the pxe to work.

I don't mind turning off the internet gateway on the 192.x.x.x side on the server, I just don't know how.

I've used IPTABLES to get this to work once, but it keeps failing after the dhcp lease ends, I believe.

But I also want clients that connect to the 192.x.x.x Router to have internet access.

I feel like I'm close to a solution!

In the diagram you've layed out, how can I configure the server to accept connections from 192.x.x.x (router?)

---

### Post by xomikronx on 2011-04-04
Bump

Anyone Please help?

I'm new to linux.  
Could someone help me with post above?

---

### Post by Fire_Chief on 2011-04-04
I had the same problem creating the diagram that you had where I could not put space between the connection lines. The 192.x.x.x network on the server and the router are connected (server is wired into the router). Sorry I didn't get that specified before.

To remove Internet connectivity on the 192.x.x.x side of the server (but still keep Internet access through the 10.x.x.x side): In the network configuration on the server, make sure you have a default gateway defined ONLY for the 10.x.x.x network. The 192.x.x.x network should not have a gateway defined at all. This would allow the server to talk to both networks, get to the Internet through the 10.x.x.x connection, and work with DHCP/PXE on the 192.x.x.x side. You probably want to make sure that the DHCP/PXE services are only listening on the 192.x.x.x IP on the server so it will not try to do DHCP/PXE on the 10.x.x.x net.

Cheers!

---

### Post by xomikronx on 2011-04-08
Thanks.  Working Great!!  ):P

---

### Post by uPatrick on 2011-10-10
Hello xomikronx,

I would like setup a server like you.

Could you show me how to make the setup ?

internet---switch-----PC-client(192.168.x.x)
             |
          (eth1-192.168.x.x)server(eth0-10.15.x.x)
                                  | 
                                 router(wireless LAn 172.168.x.x) 
                                                |                             
                                        PXEclient(172.168.x.x)

Thank

---

