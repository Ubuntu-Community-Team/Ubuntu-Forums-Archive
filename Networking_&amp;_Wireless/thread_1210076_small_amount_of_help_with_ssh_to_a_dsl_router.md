---
title: "small amount of help with ssh to a dsl router"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by brett- on 2009-07-11
I am working on learning how to connect two computers running Ubuntu across the internet using ssh.  The two machines are both connected to the www using qwest DSL and Actiontec modems.  Both connections have static IP address, separate accounts.  I began testing by installing open ssh on each machine.  On the first machine I created a guest account and on that same machine did - 

ssh [EMAIL="guest@the.static.IP.addres"]guest@the.static.IP.addres[/EMAIL]s

and got -

ssh_exchange_identification: Connection closed by remote host

then I did - 

ssh guest1@192.168.0.5

logged into guest, no problem.

I suppose 192.186.0.5 is an internal IP address assigned by the router.  How do I ssh to the.static.IP.address and then to the internal address?  I hope someone can help, thanks!

---

### Post by TheFuzz4 on 2009-07-11
So this is the one place I like cable or dsl since the cable modem will give you a direct link no middle man. 

When I had qwest I had to setup a direct route in the dsl modem to forward all traffic over to my linksys box and then just let that do all of the port forwarding for me.

Every DSL modem I've had, has always acted as a router in other words it will take care of the NAT for you

If you log into the modem directly make sure that you forward all port 22 traffic to the correct machine.

Those action tech modems are really POS from what I have dealt with them. If you want me to test trying to hit your machine from where I'm at let me know and I'll be glad to.  Hope this helps and if you need anything else just let me know.

---

