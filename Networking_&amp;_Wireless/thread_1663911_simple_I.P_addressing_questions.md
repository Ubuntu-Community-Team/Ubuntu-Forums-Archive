---
title: "simple I.P addressing questions"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by methodtwo on 2011-01-10
Hi there
i'm wanting to build a network. The way i want to do it is to have a switch attached to my border router. my 2 servers will be on this switch. Also attached to this switch will be a dedicated firewall which will protect a few machines on my internal network. In building Internet firewalls(o'reilly) this is called a "screened subnet architecture".
I was wandering about I.P addressing though. My border router allows static internal I.Ps but they all have to have the same network and subnet address. So the dedicated firewall can do dhcp and N.A.T for hosts on the internal network, but packets send from these machines would have to be N.A.Ted twice(The dedicated firewall would, on it's external address, have to have a static internal address given out by the border router). I've tried having the dedicated firewall as a triple-homed host with it's external interface in the DMZ of the border router. To cut a long story short the so called screened subnet architecture would just be so much easier to implement, given the border router that i'm working with. The only question is, bearing in mind that the I.Ps of the dedicated firewall and the servers must come from the boarder router, should the dedicated firewall do dhcp and N.A.T for the hosts on the internal network?. Or should even the hosts on the internal network get their I.Ps from the border router?.

---

### Post by taseedorf on 2011-01-10
I will tell you what I personally would do.

I have a Network Modeling degree from St. Cloud State University.

You want to spread the load of the two devices (Router, Firewall) as much as possible, so, it is completely up to you which you want doing the DHCP.   If the load is higher on the router, have DHCP be done on the firewall.  Otherwise, have DHCP done on the Router.  

I would NOT recommend using DHCP with a firewall as this can cause issues with your firewall functioning properly and IF you do choose to use DHCP, give static IP addresses to devices on your network which will be stationary and only allow your DHCP server to give out a minimal set of IPS for new devices.

Make sure that you're border router is not doing DHCP while your firewall is doing DHCP UNLESS they are dishing out different IP's or you will run across a conflict.

Have your border router use DHCP and give your firewall an external IP of ex 192.168.1.199 and an internal of 192.168.2.199.  Have all computers on the internal network IPs like 192.168.2.*.  Do NOT have your Firewall on the DMZ of the router.  In fact, you would want your DMZ to come AFTER the firewall, unless youre router has a firewall inside of it as well that is filtering.... even though DMZ will allow connections, you still want to be very specific as to what traffic is passing through.

I might not be understanding your question correctly..?

If you're using say, a Cisco router and a Cisco firewall, you will have to tell the firewall to forward to packets to the router properly...or it will not know where to send them.   Have your DHCP server on the firewall dish out all internal IP's behind it and the DHCP on the router dish out all other IP's.  Or don't use DHCP at all.  That is what I would do.

---

