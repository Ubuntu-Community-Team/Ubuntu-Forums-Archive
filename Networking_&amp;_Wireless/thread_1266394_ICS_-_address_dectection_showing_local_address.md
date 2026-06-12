---
title: "ICS - address dectection showing local address"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by lytithwyn on 2009-09-14
What I basically have is an ubuntu server box set up with ICS so I can use it as a transparent proxy.

My incoming cable from my modem goes into eth0, and a cable goes from eth1 to my router.  This manages my local network.

Everything works fine except that if I go somewhere like checkip.dyndns.org that will echo your ip address back to you, it shows the static address I have in my router instead of the static address of eth0 interface on my proxy.  In this case, my real external IP is 208.78.***.***, but the web page will show 192.168.2.10.  I think this is breaking my fail2ban protection.

Here's my setup:

internet -> [proxy (208.78.***.*** on eth0), (192.168.2.1 on eth1)] -> [router (192.168.2.10 on wan), (192.168.1.0/24 on lan)] -> [switch]

/etc/network/interfaces:
```
auto eth0
iface eth0 inet static
      broadcast 208.78.***.255
      address 208.78.***.***
      netmask 255.255.255.128
      gateway 208.78.***.***

auto eth1
iface eth1 inet static
      address 192.168.2.1
      netmask 255.255.255.0
      broadcast 192.168.2.255
```


rc.local content for forwarding:
```
# iptables forwarding
iptables -A FORWARD -i eth1 -o eth0 -s 192.168.2.0/24 -m state --state NEW -j ACCEPT
iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A POSTROUTING -t nat -j MASQUERADE 

# iptables for squid transparent proxy
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to 192.168.2.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128


# extra modules needed to make ftp work
modprobe ip_conntrack_ftp ports=21,29
modprobe ip_nat_ftp ports=21,29
```

---

### Post by fwre01 on 2009-09-15
The fact that checkip.dyndns.org displays that private IP address is very strange. Your ISP will drop any packets from private address space long before it makes it to checkip.dyndns.org. Perhaps it doesnt merely echo the originator of the socket?

Are the rest of your clients having any other problems?

The only thing I originally thought was to do with this MASQUERADE rule. 
```
iptables -A POSTROUTING -t nat -j MASQUERADE
```
I can't remember exactly, but i assume when you don't specify any match criteria in this rule IPtables PATs all packets to the outside interface?

Another possiblity is payload re-writes which your Squid proxy is doing to the return packets?

Out of curiosity, why you are using the router aswell as the proxy? PATranslating addresses twice always makes me nervous. Could you not get the server doing everything? and eliminate the router?

---

### Post by puppywhacker on 2009-09-15
those check ip address website also look at the http headers that are added by the proxy. Squid will add a X-Forwarded-For

In squid.conf you can disable this with

header_access X-Forwarded-For deny all

---

### Post by lytithwyn on 2009-09-15
You were right on target, fwre01.  It was squid.  After you mentioned that, I did some searching and found this article: [http://www.cyberciti.biz/faq/squid-proxy-is-not-hiding-client-ip-address/]("http://www.cyberciti.biz/faq/squid-proxy-is-not-hiding-client-ip-address/")

It said to add "forwarded_for off" to my squid.conf, and that fixed it right up.  Apparently this sets a special HTTP header called X-Forwarded-For, and the ip checker was using that value.  I'm sure this could cause problems, so I'm glad to have that disabled.

---

### Post by lytithwyn on 2009-09-15
Thanks, puppywhacker!  I was just replying when you posted that.  If I hadn't found it on google already, your advice would have been exactly what I needed to see.

---

### Post by fwre01 on 2009-09-16
lytithwyn, is this rule needed for squid? (see below) It may very well be needed, I must admit I have never used squid. It just doesnt seem to make sense...

```
iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3128
```

To me this says, you have web requests (dport of 80) coming in from the net which you want to redirect to 3128?

---

### Post by lytithwyn on 2009-09-17
It was in a transparent squid proxy tutorial I was reading somewhere.  I think what that command does is make it so that if someone is using the proxy machine to browse the web, they will hit the cache also; they will be connecting directly through eth0, not eth1.  Our proxy/caching server is headless, so I could remove that rule.  I probably won't though, since squid should also be caching ubuntu update packages.  I have two other Ubuntu machines on my network that would benefit as well as the caching server.

---

