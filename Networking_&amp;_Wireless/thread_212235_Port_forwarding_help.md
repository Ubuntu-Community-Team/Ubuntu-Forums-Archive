---
title: "Port forwarding help"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by Endow on 2006-07-09
I'm using Dapper Drake 64bit on a AMD64.I use bit torrent a lot and since I'm behind a router I would like to know how I can port forward.


Anyone [-o<

---

### Post by Xzallion on 2006-07-09
What is your router model?  Generally this has to due with the router settings.

---

### Post by ahaslam on 2006-07-09
Try [http://www.portforward.com/]("http://www.portforward.com/")

Tony.

PS. It should have a step by step guide for your torrent client & router. ;)

---

### Post by Endow on 2006-07-09
My router is a Billion Bipac -5100W.

Tony that's the site I used as references when i was port forwarding on windows.But I'm using Ubuntu...

---

### Post by ahaslam on 2006-07-09
> **Endow said:**
> My router is a Billion Bipac -5100W.

Tony that's the site I used as references when i was port forwarding on windows.But I'm using Ubuntu...
Why would it make a difference? You're accessing the routers configuration utility, not anything in Ubuntu. I've used it to successfully set up BitTorrent for my BT Voyager 205 (in Ubuntu).

I am of course assuming that you have no connection issues. Does the BitTorrent currently work at all?


Tony.

PS. Apart from BitTorrent not saying that I am behind a firewall, no noticeable improvements have occurred since forwarding ports.

---

### Post by Endow on 2006-07-09
It does but there is no preferences options on the standard bit torrent program

Just the Download Upload and Events tabs...

---

### Post by Endow on 2006-07-10
Anyone :'(?

Btw Tony that probably because you haven't disabled your firewall (firewalls slow d/l's)...which brings me to a related question : how do you disbale your firewall in Ubuntu? (i heard it has a built in firewall)

---

### Post by hayesey on 2006-07-10
As default the firewall allows all traffic to pass.

type the command:

```
sudo iptables -L
```

If output is like this:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Then you have no firewall on the PC itself.

Setting up port forwarding on your router is the same regardless of what operating system you are using.  You just access the router web configuration using a web browser.

---

### Post by Endow on 2006-07-10
Sorry guys :(  Dumb me...I was trying to configure another connection I have...


It's like this : I had this connection with a router communicatingw ith my wifi adapter and now I have one more which is the one I'm using now (the router one will be no more come the end of this month)...

I was trying to configure the router ...but my new connection doesn't use a router.Instead I have an acess point communicating with my wifi adapter.The ISP provides net to the whole building and each home has an access point...



Which makes me ask : does this mean I'm behind a router anyway?When I try accessing my router web configuration wizard I get a message of time out and saying my ISP holds the previleges....


Does this mean I'm NATed  with no way out???


PLease help me:(

---

### Post by Endow on 2006-07-12
Anyone?:(

---

### Post by tturrisi on 2006-07-12
> **Endow said:**
> Sorry guys :(  Dumb me...I was trying to configure another connection I have...


It's like this : I had this connection with a router communicatingw ith my wifi adapter and now I have one more which is the one I'm using now (the router one will be no more come the end of this month)...

I was trying to configure the router ...but my new connection doesn't use a router.Instead I have an acess point communicating with my wifi adapter.The ISP provides net to the whole building and each home has an access point...

Which makes me ask : does this mean I'm behind a router anyway?When I try accessing my router web configuration wizard I get a message of time out and saying my ISP holds the previleges....

Does this mean I'm NATed  with no way out???

PLease help me:(
Yes, more than likely the whold building is setuo via access points & a router somewhere on the LAN.  You do not need a firewall, router or no router, unless running services that are opened to the WAN, such as www server, mail server, etc..  Test if behind a router by going to [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

