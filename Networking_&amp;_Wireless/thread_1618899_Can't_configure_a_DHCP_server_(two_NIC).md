---
title: "Can't configure a DHCP server (two NIC)"
date: 2010-11-11
forum: Networking &amp; Wireless
---

### Post by shafi on 2010-11-11
Hey Guys,
I have a desktop computer with ubuntu 10.10 installed. I want this computer to act as a DHCP server.
Currently there are two Network cards installed on this computer, the first NIC <eth0> has a public IP address and the second NIC <eht1> has a local IP.
I tried a lot to configure the dhcp server for this computer but I couldn't.

```

eth0      Link encap:Ethernet  HWaddr 00:21:86:12:51:2a  
          inet addr:<*public ip*>  Bcast:<*broad cost*>  Mask:255.255.255.128
          inet6 addr: fe80::221:86ff:fe12:511a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38304956 (38.3 MB)  TX bytes:4744123 (4.7 MB)
          Interrupt:16 Memory:d0480000-d04a0000 

eth1      Link encap:Ethernet  HWaddr 00:0a:5e:48:aa:6b  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49282 (49.2 KB)  TX bytes:10238 (10.2 KB)
          Interrupt:22 Base address:0xe000 


```
default/dhcp3-server
```

cat /etc/default/dhcp3-server

INTERFACES="eth1"


```

dhcpd.conf
```

# Sample /etc/dhcpd.conf
# (add your comments here) 
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.100;
option domain-name-servers 8.8.8.8, 8.8.4.4;
option domain-name "mydomain.example";

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.150 192.168.1.200;
} 

```

```

sudo /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [ OK ] 
 * Starting DHCP server dhcpd3                                           [ OK ] 


```
Everything looks fine, but the client can get an IP. Any help? thanks.

---

### Post by shafi on 2010-11-19
Any one?

---

### Post by SeijiSensei on 2010-11-19
> **shafi said:**
> Any one?

In an terminal, run "tail -f /var/log/messages", then try connecting from a client.  Do you see the attempt?  Do you see any errors?

---

### Post by shafi on 2010-11-22
> **SeijiSensei said:**
> In an terminal, run "tail -f /var/log/messages", then try connecting from a client.  Do you see the attempt?  Do you see any errors?

Thanks for the reply.

I tried a crossover cable, now it works fine, and i'm able to get the IP from the DHCP server, but I can't ping the internet. Means I'm not connected to the internet. any Idea?

---

### Post by SeijiSensei on 2010-11-22
Do a Google search for "linux nat masquerading".  You need to configure the router with iptables to "masquerade" the machines behind it.

---

### Post by shafi on 2010-11-23
> **SeijiSensei said:**
> Do a Google search for "linux nat masquerading".  You need to configure the router with iptables to "masquerade" the machines behind it.

Thanks a world. The link below helped me to figure out the nat masquerading.
[http://ubuntulinux.co.in/blog/ubuntu/nat-configuration-with-iptables-in-ubuntu/](http://ubuntulinux.co.in/blog/ubuntu/nat-configuration-with-iptables-in-ubuntu/)

---

### Post by shafi on 2010-11-23
One question more :)

Its quite strange. now the dhcp server works fine, but when ever I restart the server all the masquerading commands that I have entered are lost. and I have to manually type all iptables commands again. how can I make it permanent?

---

### Post by bitscarre on 2010-11-23
Do:

sudo nano[COLOR=#000000]**[FONT=monospace] [/FONT]/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]init.d[COLOR=#000000]**/**[/COLOR]rc.local

Add your command to be executed, also read those instructions at the top of the file and you should be good to go.

---

