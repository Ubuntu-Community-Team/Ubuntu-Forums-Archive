---
title: "How to block a roque dhcp server"
date: 2009-02-09
forum: Networking &amp; Wireless
---

### Post by Spenser_Gilliland on 2009-02-09
My girlfriend has been struggling for three weeks with a rogue DHCP server on her apartments network.  Is there an iptables rule that would allow me to block DHCP replies from this rogue DHCP server but allow them from the real DHCP server?  I have the rogue servers MAC address.

---

### Post by redmk2 on 2009-02-10
When your host requests a dhcp assigned address all dhcp servers in the LAN respond.  Your host accepts the first offer it receives. 

Short of Isolating the rouge device with a layer 3 device (router) or physically removing the device there is nothing you can do.  

Is the device handing out addresses in the correct range for the apartment house? If so, do you really care how you got the address?  Once you have the lease the host IP should be uniquely yours AFAIK.

What does the network admin say about this issue?

---

### Post by Iowan on 2009-02-10
Check **man dhclient**. There is a "-s" option to specify server - but I can't say if that's what it is intended to do.> The DHCP client normally transmits any protocol messages it sends before acquiring an IP address to, 255.255.255.255, the IP limited broadcast address. For debugging purposes, it may be useful to have the server transmit these messages to some other address. This can be specified with the -s flag, followed by the IP address or domain name of the destination. 
If the addresses are valid, the main problem would be if the rogue and real DHCP servers are handing the same address to different machines.

---

### Post by puppywhacker on 2009-02-10
iowan's -s option to limit the scope of the broadcast is a very good option. just dhcp straight to the correct dhcp server

the other option is to filter all traffic from that MAC address, if you also filter on the MAC and port 53

 iptables -A INPUT -m mac –mac-source 00:0F:EA:91:04:08 -j DROP

you can make the rule reboot persistant with
 iptables-save

---

### Post by Spenser_Gilliland on 2009-02-10
I'll try the -s option this weekend thanks.

Spenser

---

### Post by Spenser_Gilliland on 2009-04-22
I found this rule on a how to.  Looks like what I want.  I have to change the policy on the INPUT chain to REJECT, but it should be golden.

$IPTABLES -A INPUT -p UDP -s $DHCP_SERVER --sport 67 --dport 68 -j ACCEPT

---

### Post by Stuggi on 2009-04-22
Doesn't that just block DHCP traffic on a specific port? If that's so, it'll block the trafic from the "good" server as well...

use the command posted above;
```
iptables -A INPUT -m mac –mac-source 00:0F:EA:91:04:08 -j DROP
```

Which will drop everything from the "rogue" server. Which should fix your problem permanently (if the two servers uses different pools, and they never ever change the nic.... :D)

---

