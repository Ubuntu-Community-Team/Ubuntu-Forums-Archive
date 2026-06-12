---
title: "Simple network switch using Ubuntu"
date: 2013-01-08
forum: Networking &amp; Wireless
---

### Post by faroutliving on 2013-01-08
I have two servers on the far side of a radio link. The first one is connected to the radio and the second computer.

In the past I have simple done some port forwarding/translation to be able to access the second computer.

However, it turns out I actually have multiple ip addresses available to me. So I would like to simple using ip address #1 to access the first computer, and ip #2 to access the second computer.

Can I do this with iptables? Seems like it should be possible. Would I setup the second computer with a static address, or continue to just use DHCP on the first computer?

Thanks!
Deron

---

### Post by jonobr on 2013-01-08
Hello

Could you explain your setup a bit more as well as your IP address allocation?
What gets what Ip address and how is it connected up?

---

### Post by faroutliving on 2013-01-08
Hello,

I guess the easiest way to explain this would be to use some numbers.

On the "local" side of the radio a device (not sure what it is) is sending all 192.168.10.10 and 192.168.10.11 network traffic to the radio.

On the "remote" side of the radio are 2 computers. The first computer is hooked to both the radio (eth0) and the second computer (eth1). I want to pass all 192.168.10.11 traffic to the second computer.

Deron

---

### Post by jonobr on 2013-01-08
Forgive the crude drawing, but is this whats going on?
If yes, what are the question mark ip addresses?

---

### Post by faroutliving on 2013-01-12
Thanks for the help, but obviously this is not the easy question I thought it was.

The radios don't have network addresses. Well, they have admin addresses that can be used to configure the radios, but all traffic is passed through them, not to them. You can replace them with a single wire and need make no changes to the configuration on either end.

If you want to know the gateway address, it would be 192.168.10.1 in this case.

The rest is configurable by me and can be anything you want it to be.

I guess the real problem here is that box #1 can not act like a network switch. Imagine if I wanted box #2 to get its ip address from something upstream.

---

