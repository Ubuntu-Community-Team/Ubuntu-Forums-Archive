---
title: "Firewalling my home network (blocking specific host and more)"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by XMLove on 2008-12-07
Hi forum

I want to block all the computers on my home network from accessing some specific domains. I want to know what goes in and out of my computers. Also, I would like to cut bandwidth spending by blocking ad networks and such on across the network.

I belive the best way to do this is by setting up a two-way firewall on one of the computers and passing all the data from the other computers thorough the firewalled computer.

The question though, is how to do this? And should I even do it?

Or should I setup one firewall on all the computers and somehow synchronize the rules between them? This would, however, probably leave out the computer running Windows.

Is there another method I have not though about that could be better?

Looking forward to being enlightened!

---

### Post by kevdog on 2008-12-07
Yes I suppose you could do the blocking websites with internet connection sharing, using your ubuntu computer as a router and enabling the firewall.  The Qos is another issue.

For a simplified solution I would buy a router compatible with either dd-wrt or tomato firmware and then flash the router with the dd-wrt or tomato firmware.  These 3rd party free firmwares allow you to do everything you want to do very easily, and the os actually written and designed to do what you want very efficiently.  They have been evolving for over 10 years.  For you to get all these features in a simple Ubuntu setup would be like to reinvent the wheel, and it probably wouldn't be nearly as efficient or well designed.

---

### Post by XMLove on 2008-12-07
Thanks for replying kevdog!

If I got you right, you are saying that I should use a hardware based firewall instead of a software based firewall? I have thought about that, but I have been afraid of investing in one because I feel like I would be stuck with it if it did not work as I would like it too. (For example, can I block a domain and all it's subdomains, or would it work like the /etc/hosts-blocking approach were you must specify every subdomain manually)?

I am about to invest in an 8-port gigabit switch. Is there any such thing as a gigabit switch/router that also can act like a firewall with the software you suggested?

I appreciate your input.

---

