---
title: "Limit Access to certain IP or FQDN via IPTABLES"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by bigdaddyweed on 2009-12-21
Hello folks,

I have a ubuntu 6.06 Server that I use as a remote access server. Its sole purpose is for users to connect and have access to the internet passed to them, giving them access to their email when wifi or other connections may not be present. I would like to limit the abuse on this service (restricting other services) and limit it to a very restricted set of IP's or domains.

here is my setup

~Ubuntu 6.06 server
~zoom 56k serial modem on ttyS0
~mgetty configured with server address of 192.168.1.151 and client address of 192.168.1.155.
~gateway at 192.168.1.1

I want to allow the user to connect and have access to pop.gmail.com and smpt.gmail.com so they can check their mail (more mail servers will be added later), while blocking all other traffic so that they can check mail and mail only..no IM'ing, no browsing, no automatic updates trying to connect, etc.

How would I setup my IPtables for this?

---

### Post by puppywhacker on 2009-12-22
I would try something like below. I didn't test it nor am I going to troubleshoot the rules. The warranty expired as soon as I hit "Submit Reply". The rule spells out in english

All the incoming packets from the wireless, with a ip-destination for gmail-pop.l.google.com (use "dig pop.gmail.com" to find the ip-addresses, you can't or at least shouldn't use domains), look for tcp packets only which establish a new connection (so with the SYN flag set) outgoing on the ports smtp 25, pop 110, google-tls-smtp 587, google-tls-pop 993 and remember to allow future packets of this connection, all else drop ...

```
iptables -A INPUT -i wlan0 -d 74.125.79.109 -p tcp -m state --state NEW -m multiport --dports 25,110,587,993 -j ACCEPT

iptables -A INPUT -i wlan0 -d 74.125.79.111 -p tcp -m state --state NEW -m multiport --dports 25,110,587,993 -j ACCEPT

iptables -A INPUT -j DROP

```

---

### Post by bigdaddyweed on 2009-12-23
> **puppywhacker said:**
> The warranty expired as soon as I hit "Submit Reply". 
[/CODE]

I think every forum should have this written into its "Code of Ethics" for people to see...

Thanks for the info too. I will give it a whirl and see if it works.

One more question though...do I need to setup IP Masquerading for this to work in the first place??? Or just add this to the iptable and it should work?

---

### Post by puppywhacker on 2009-12-23
It should work independently from the masquarading rule, but preferably before.

The INPUT rules are checked before the POSTROUTING rules so that should go fine hand in hand.

---

