---
title: "Switching to ppp0"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by PeEllAvaj on 2009-08-24
I have two internet connections established on my computer, one on eth1 (normal wired with DHCP), and one on ppp0 (broadband card connection created with wvdial).

Ifconfig is reporting that I have IP and DNS and that everything is working, but I don't know how to get my computer to actually use the ppp0 connection.

I have tried unplugging eth1 but then I just lose internet.  Is there some type of switch I am supposed to trigger?  I have tried restarting /etc/init.d/networking and I here is the output of "route"  (stars added for privacy):
Kernel IP routing table                 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
**.**.**.**     *               255.255.255.255 UH    0      0        0 ppp0 
10.0.0.0        *               255.255.255.0   U     0      0        0 eth1 
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         assault.mortalp 0.0.0.0         UG    100    0        0 eth1

Thanks for any help!

---

### Post by GeorgeVita on 2009-08-24
Hi **PeEllAvaj**, just an idea:

as wvdial is the front-end of **pppd** I just looked at **man pppd** (parameters: defaultroute, replacedefaultroute) >        defaultroute
              Add  a  default route to the system routing tables, using the peer as the gateway, when
              IPCP negotiation is successfully completed.  This entry is removed when the PPP connec&#8208;
              tion is broken.  This option is privileged if the nodefaultroute option has been speci&#8208;
              fied.

       replacedefaultroute
              This option is a flag to the defaultroute option. If defaultroute is set and this  flag
              is also set, pppd replaces an existing default route with the new default route.

My idea is to add **defaultroute** and **replacedefaultroute** within parameters of file /etc/ppp/peers/wvdial and then using it will set its 'route' as 'default'. (I did not checked this)

Below are the contents of 'default' /etc/ppp/peers/wvdial +new params:
```
name wvdial
noauth
usepeerdns
defaultroute
replacedefaultroute

```
Regards,
George

---

### Post by PeEllAvaj on 2009-08-24
Thanks!  Adding those two lines to /etc/ppp/peers/wvdial worked perfectly!

defaultroute
replacedefaultroute

---

