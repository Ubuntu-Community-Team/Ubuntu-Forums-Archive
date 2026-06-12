---
title: "Internet connection sharing and routers"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by malcmail on 2011-07-25
This may seem a bit convoluted but bear with me.

I have a modem connected to my router (pfsense on 192.168.1.1) which is then connected to a wireless AP (192.168.1.253). A number of PCs pick up the wireless and all is well.

I've just received another broken PC that I've kicked into life and was going to run a FreeNAS box with it to back up a number of the PCs on the network. I've actually hooked this up via ethernet to my "server" PC (192.168.1.125 on its wlan NIC). Its all set up so that the server eth NIC (10.42.43.1) is connected to the FreeNAS box (10.42.43.2) and the FreeNAS box can ping both interfaces of the server, the router and the net, and any other box on the 192.16.1.x network. The problem is that I can't for the life of me get any of the 192 boxes to ping the FreeNAS box. I'm presuming its a routing / gateway issue with the server box but being pretty damn hopeless with these things I've been stumbling about breaking things.  Can anyone help me out? 

Thanks in advance.

---

### Post by jmoorse on 2011-07-26
You probably have the "server" setup to do NAT, in which case you won't be able to ping into the freenas subnet without making some changed to your NAT/iptables config.  Can you post your NAT config and:

```

sudo iptables -L

```

---

### Post by malcmail on 2011-07-26
Thanks for stepping in. The result of iptables -L is:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

I've not configured any NAT either - is there any way I can check this to make sure?

Thanks again.

---

### Post by newbie-user on 2011-07-27
The problem is that you have your FreeNAS box on a different subnet.  You need to set up static routes on your 192.168 boxes that tell them where to find your FreeNAS box.  In Ubuntu, use the route command:

route add -net 10.42.43.0 netmask 255.255.255.0 gw 192.168.125

To check NAT:  iptables -L -t nat

---

### Post by malcmail on 2011-07-27
Thanks for those bits of info. I would have preferred it on 192.168 as well but I couldnt seem to do that without killing the server box's connection to the net. If you knew a way to do it I'm all ears.

The NAT on the server box is set to :

```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  10.42.43.0/24       !10.42.43.0/24       
MASQUERADE  all  --  anywhere             anywhere
```

Not sure why there is a "!" before the destination on that line mind you.

I added the line you suggested on another ubuntu box and when I try to ping it gives me "Destination port unreachable" from the server box. Which is at least better than before when it gave no response.

ANy other ideas?

PS Just checking the server box's iptables again and it gives this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     udp  --  anywhere             anywhere            udp dpt:bootps 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:bootps 
ACCEPT     udp  --  anywhere             anywhere            udp dpt:domain 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:domain 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             10.42.43.0/24       state RELATED,ESTABLISHED 
ACCEPT     all  --  10.42.43.0/24        anywhere            
ACCEPT     all  --  anywhere             anywhere            
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 
REJECT     all  --  anywhere             anywhere            reject-with icmp-port-unreachable 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

---

### Post by malcmail on 2011-07-27
Sorted. I've taken out the last 2 FORWARD rules on the server as these were clearly causing the problem.  Of course its now easy to get my ubuntu boxes to find the right route but now time for Windows and Android now. Any other ideas? lol

---

