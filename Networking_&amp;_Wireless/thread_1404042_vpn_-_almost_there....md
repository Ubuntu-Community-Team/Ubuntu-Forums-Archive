---
title: "vpn - almost there..."
date: 2010-02-11
forum: Networking &amp; Wireless
---

### Post by reggler on 2010-02-11
Hi There,

I tried to configure my vpn connection using pptp from the shell following following tutorial:
[http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html](http://www.cyberciti.biz/tips/howto-configure-ubuntu-fedora-linux-pptp-client.html)

now, if i use```
pppd call novax
``` to connect to my vpn i see following appearing in **/var/log/messages**:
```
Feb 10 21:11:57 reg-laptop pppd[2655]: pppd 2.4.5 started by root, uid 0
Feb 10 21:11:57 reg-laptop pppd[2655]: Using interface ppp0
Feb 10 21:11:57 reg-laptop pppd[2655]: Connect: ppp0 <--> /dev/pts/0
Feb 10 21:11:58 reg-laptop pppd[2655]: CHAP authentication succeeded
Feb 10 21:11:59 reg-laptop pppd[2655]: MPPE 128-bit stateless compression enabled
Feb 10 21:12:00 reg-laptop pppd[2655]: local  IP address 10.243.249.22
Feb 10 21:12:00 reg-laptop pppd[2655]: remote IP address 10.243.249.20
```
What tells me i'm connected, yeah? verifying with ifconfig, my ppp0 ip is correctly set to 10.243.249.22 - i can also ping this ip but i tried to ping other ips in our network and i can't reach any of them :( - did i mess up the route maybe?
Content of my **/etc/ppp/ip-up.d/route-traffic**:
```
#!/bin/bash
NET="10.243.249.46/8" # set me
IFACE="eth1" # set me
#IFACE=$1
route add -net ${10.243.249.46} dev ${eth1}
root@reg-laptop:/etc/ppp/peers# 

```
Any clues or ideas would be appreciated!

Thank you!
Ron

---

### Post by snowbourne on 2010-03-20
I had this same problem

Check out this link: [http://pptpclient.sourceforge.net/routing.phtml#client-to-lan](http://pptpclient.sourceforge.net/routing.phtml#client-to-lan)

I was following the same tutorial you were, follow those directions and you should be able to access other nodes on the VPN.

---

