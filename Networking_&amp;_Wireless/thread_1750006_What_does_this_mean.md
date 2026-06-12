---
title: "What does this mean?"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by dioxtride on 2011-05-05
I've recently enquired about getting a second static IP address.

This is a quote from my ISP:

"I've check with our network manager and he can confirm that an ADSL connection can't establish 2 PPP session as it's restricted on the DSLAM. At the moment, we can only router a new /32 IP down to your existing IP addresses. You will then need to do your own IP mapping etc."

What does this mean exactly? What does a /32 IP mean?

---

### Post by Grenage on 2011-05-05
A /32 address means that it's an address for a single host, not a range.

---

### Post by dioxtride on 2011-05-05
Could you please simplify that with an example?

---

### Post by Grenage on 2011-05-05
No problem:

IP address one is 192.168.1.19/24, which means that its network mask is 24 bits, and is the equivalent of 255.255.255.0.  There can be many more machines in that network range (192.168.1.1 - 192.168.1.254).

IP address two is 213.120.62.101/32, which means that its network mask is 32 bits, and is the equivalent of 255.255.255.255  There can be no other machines in that network range, because the subnet only allows for one host.

If you're interested in learning more in-depth stuff, this [site]("http://www.learntosubnet.com/") is apparently quite good.

---

### Post by dioxtride on 2011-05-05
I see, well in a brief nutshell (so I know where to start looking when I get time), how would I be able to setup multiple PPP logins through a /32?

I need to give 2 computers a static IP each.

---

### Post by Grenage on 2011-05-05
Unfortunately that's not something I can help you with, I've never had to configure IP addresses in that fashion.  ISPs here always give you a range, which you would enter on each machine.

Would you not just manually enter the details into each machine?  Do you have a modem, or a router?

---

### Post by morrty11 on 2011-05-05
> **dioxtride said:**
> I see, well in a brief nutshell (so I know where to start looking when I get time), how would I be able to setup multiple PPP logins through a /32?

I need to give 2 computers a static IP each.

What you are trying to do is called 1:1 NAT.

You can purchase a home router and flash either DD-WRT or Tomato firmware on them to get this feature. However, you need a static IP other than a /32 subnet. Only one PPP session is required for this.

---

