---
title: "What is this filling up my router logs?"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by ridetheteapot on 2012-01-16
Hey I tried looking for some info on this because my routers logs are filling with this nonsense and its gotten me curious.

My routers log says that a udp connection (port 67) from my isp's dhcp ip is being denied to my lan broadcast ip port 68.
Is this a normal thing?

---

### Post by jonobr on 2012-01-16
Difficult to guess without the log.

67 and 68 are DHCP related so it could be ok, however, please post the results of the log

---

### Post by SeijiSensei on 2012-01-16
What you're seeing is likely the DHCP requests being made by other computers and routers in your network segment.  This is especially common on services that provide IP over cable-television circuits where you are sharing a physical network segment with a couple hundred other people in your neighborhood.

DHCP requests are broadcast (sent to IP 255.255.255.255) to the entire visible physical network.  If you're logging all packets that fail to meet a firewalling rule, you'll see lots of these requests.

I just add this rule to iptables so I won't see this traffic:

```
sudo iptables -I INPUT -j REJECT  -p udp --source-port 67:68 --destination-port 67:68
```

---

### Post by ridetheteapot on 2012-01-17
Seiji, that makes plenty of sense. Still totally weird to me.

Jonobr this is what the relevant log lines contain:
```
FIREWALL 	UDP connection denied from [ISP's DHCP IP]:67 to 255.255.255.255:68 (eth1) 
```

---

### Post by SeijiSensei on 2012-01-17
> **ridetheteapot said:**
> Seiji, that makes plenty of sense. Still totally weird to me.

Well, think of it this way.  Your computer boots up and needs some information to configure its network parameters.  How does it get this information?  It can't contact a specific server, since the computer doesn't yet have an IP address or gateway defined.  So instead it "calls out" to every computer it can see on the local network asking if there's a server that can help.  The DHCP server sees this request and replies with the appropriate information.  (I believe this is sent at the MAC layer since the computer still doesn't have TCP/IP configured yet.)

---

### Post by ridetheteapot on 2012-01-17
Maybe I am thinking about what is happening wrong:
My router is blocking dhcp offers from wan trying to get to the lan's broadcast address. Why would it want to jump that gap?
I don't think I could get the isp to assign more ips if i turned off my routers dhcp and let those offers go through.
Or is it just the normal offer for my router (if it was ip-less) and the router is just telling me that its not going to pass it through to my lan?

---

### Post by SeijiSensei on 2012-01-17
> **ridetheteapot said:**
> My router is blocking dhcp offers from wan trying to get to the lan's broadcast address.

I don't think so.  It's blocking DHCP requests from other hosts on the ISPs network segment that are broadcasting requests for addresses on that network.  

It's possible that the router is forwarding the broadcast request to the internal network address.  If so, that's a problem with the router's configuration.  You should be using a default REJECT rule for the FORWARD chain and only permitting specified external hosts/services across the router to the local network.  In most cases there's no reason at all why remote hosts should be able to send packets to your LAN hosts except in response to a specific request like web browsing.  In those cases the rules that allow ESTABLISHED and RELATED traffic apply.

---

### Post by ridetheteapot on 2012-01-18
Thanks you sensei I see what your saying now (also for the iptables silencer).

---

