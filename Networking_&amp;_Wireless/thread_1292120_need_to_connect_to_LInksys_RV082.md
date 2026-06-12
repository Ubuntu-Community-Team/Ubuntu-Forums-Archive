---
title: "need to connect to LInksys RV082"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by theduke0 on 2009-10-15
Hello Friends,

We just switched to a Linksys RV082 router at work and I need some help connecting to it from home.  It is setup to connect with an IPsec tunnel.  

I have searched around but really can't find much guidance as to where to even start.  I have downloaded ipsec-tools and racoon but I am not even sure where to start.  Could someone point me in the right direction? 

Thanks,
David

---

### Post by yknivag on 2009-10-15
Sadly it isn't possible in Linux.  The Linksys VPN server software is closed source and Linksys have only ever released a Windoze client.

---

### Post by theduke0 on 2009-10-15
> **yknivag said:**
> Sadly it isn't possible in Linux.  The Linksys VPN server software is closed source and Linksys have only ever released a Windoze client.
I know this isn't true.  We have mac users in the office that connect to the VPN using IPSecuritas.  

I also think there is a way to setup my home router so that it tunnels directly to the vpn here at work.  

I'm going to continue working with ipsec-tools.conf and/or racoon to see what I can get going.  Help from anyone is greatly appreciated.

---

### Post by theduke0 on 2009-10-22
it looks like there is a tool that works for this.  its name is shrew soft.  there are clients for windows and linux.  

i've got the client installed and i can connect to my tunnel.  i can ssh to internal servers but i can't reach anything outside the network.  

what gives?  where to go from here?

---

