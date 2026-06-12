---
title: "How do I make 127.0.0.1:3306 redirect to a remote mysql server? Iptables NAT."
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by briwood on 2010-03-22
Hey, I'd love a hint or two on the following problem.  I've set up iptables rules to forward all connections to port 3306 to a non-standard mysql port on a remote server.  This works, except that I need to deal with the loopback interface in a special way and I'm stuck.

```

iptables -t nat -A PREROUTING -p tcp --dport 3306 -j DNAT --to 128.XXX.XXX.XXX:3197
iptables -A FORWARD -p tcp -d 128.XXX.XXX.XXX --dport 3197 -j ACCEPT
iptables -t nat -A POSTROUTING  -j MASQUERADE

```

Since locally-generated packets will never hit the PREROUTING rule, you'll need to setup a near identical rule using OUTPUT to make it work. Here is what I've tried:

```

iptables -t nat -A OUTPUT -p tcp -o lo --dport 3306 -j DNAT --to 128.XXX.XXX.XXX:3197

```


With all of these rules in place, I can connect to another server and n telnet to 3306 on this server and this results in a response from mysql on the remote server.  BUT from this server I cannot 'telnet localhost 3306' and get a mysql connection.  When I try that, the telnet connection hangs open with no response.

Here are what my chains look like:

```

# iptables -L 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             mysql.example.com tcp dpt:embrace-dp-s 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain RH-Firewall-1-INPUT (0 references)
target     prot opt source               destination      

iptables -L -t nat -v
Chain PREROUTING (policy ACCEPT 131 packets, 61868 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    1    60 DNAT       tcp  --  any    any     anywhere             anywhere            tcp dpt:mysql to:128.XXX.XXX.XXX:3197 

Chain POSTROUTING (policy ACCEPT 23 packets, 1470 bytes)
 pkts bytes target     prot opt in     out     source               destination         
  204 13161 MASQUERADE  all  --  any    any     anywhere             anywhere            
Chain OUTPUT (policy ACCEPT 826 packets, 53871 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    0     0 DNAT       tcp  --  any    lo      anywhere             anywhere            tcp dpt:mysql to:128.XXX.XXX.XXX:3197 


```

Thanks for any help!

---

### Post by gombadi on 2010-03-22
The PREROUTING table is just that - a point before the kernel has made routing decisions. You are waiting until the packet has been through and is now in the OUTPUT table and are then trying to change the destination address - trying to send a packet for 128.XXX.XXX.XXX out via the lo interface.

Have you had a look at stunnel?
It creates an encrypted tunnel from one machine to another so you can still connect to your local machine on port 3306 and stunnel will create a secure tunnel to the 128.XXX.XXX.XXX machine on what ever port you want to connect to. It would be better than sending mysql over the normal Internet.

---

### Post by briwood on 2010-03-22
Thanks for the reply. Stunnel doesn't help--I don't have control of the remote dbserver and it doesn't accept ssh connections, only mysql. I'm trying to work around a limitation in a server application.  The limitation is that I can only connect to a LOCAL mysql database.  I am trying to fool the server in to using a remote mysql database. I was hoping to do this by simply forwarding 3306 to another server on the same subnet.

---

### Post by briwood on 2010-03-23
> **gombadi said:**
> You are waiting until the packet has been through and is now in the OUTPUT table and are then trying to change the destination address - trying to send a packet for 128.XXX.XXX.XXX out via the lo interface.

I believe that doing DNAT in -t nat OUTPUT is legal as indicated on this diagram: [http://www.docum.org/docum.org/kptd/](http://www.docum.org/docum.org/kptd/) See the IPTABLES OUTPUT section on left under "Local Process."

Also: [http://www.faqs.org/docs/iptables/traversingoftables.html](http://www.faqs.org/docs/iptables/traversingoftables.html) Table 3-2: "This chain can be used to NAT outgoing packets from the firewall itself."

---

### Post by briwood on 2010-03-24
ssh is not needed on the remote end for a tunnel so going that route.

Lots more info on how you might do this with iptables (if you had to) here:
[http://www.linuxquestions.org/questions/showthread.php?p=3909624#post3909624](http://www.linuxquestions.org/questions/showthread.php?p=3909624#post3909624)

---

