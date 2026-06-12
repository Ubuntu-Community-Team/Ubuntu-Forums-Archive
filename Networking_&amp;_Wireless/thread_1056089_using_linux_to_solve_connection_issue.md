---
title: "using linux to solve connection issue"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by kellogs908 on 2009-01-31
I currently live at a house close to campus that has eight people in it, and unfortuantly we have comcast internet, we ahve been having issues with a really slow internet, which we belive is mainly due to goign over comcasts 250gb limit well before the month is over, I guess its to be expected when you live with eight pretty tech savvy people. Anyways I am looking based on soemone elses suggestion to setup a linux box between the router and the switch in the house, but I havve no clue what to do after that. Someone said to use iptables? basically i want to be able to see exactly what ip's in the house are using to much bandwitdh and even throttle thier bandwidth if I have to. but also keep track of our total used bandwidth so we can try to not go over. Any help in how I would do this? Is ubuntu the best distro to do this? Should I go with an older version of ubuntu if I am putting this on an old machine?

---

### Post by kidders on 2009-02-02
Hi there,

> **kellogs908 said:**
> Someone said to use iptables?That's what I would do. One approach might be ...[LIST]
[*]Configure the linux box to issue fixed IP addresses with DHCP.
[*]Set up an iptables rule for each address that doesn't do anything much.
[*]Deny outgoing internet access to all other addresses.
[*]Install a web server, and create a catch-all page that says something like "Sorry ... you've exceeded your limit or aren't allowed to use our internet connection."
[*]Create a cron job to re-evaluate bandwidth usage every few minutes.
[/LIST]
In a little more detail ...

**DHCP Server & Iptables**
Running your own DHCP server on a small network has its advantages, because you can explicitly fix everyone's IP address. If you want to, you can pair it with a DNS server (so you can reliably refer to peoples' computers by name), but that's another day's work. An IP address is fixed based on the MAC address that asks for it.

Setting up corresponding iptables rules for each address allows you to count traffic to/from them with something like **sudo iptables -vL**. The default policy for unknown addresses would be to redirect all outgoing requests to an internal web server. That way, if someone wonders why their internet connection has suddenly stopped working, trying to visit any website would tell them.

**Web Server & Cron**
You could use a RewriteRule to have your web server respond to all incoming requests with the same page. A cron job could run every few minutes to remove the iptables rule corresponding to any IP address that has exceeded its allowance, so any further requests will wind up at that web page.

You might want to create something a bit smarter (eg capable of throttling throughput to IPs getting close to their limits) ... that's just a matter of how complicated you want your cron script to get.

The down-side of a scheme like this is the administrative overhead involved in allowing new computers onto your network. There are a few ways around that issue ... assuming you like my idea at all.

> **kellogs908 said:**
> Is ubuntu the best distro to do this?Your choice of distro is basically irrelevant. Virtually anything should be capable of running a couple of servers & a firewall, so you can choose whatever you're most comfortable with.

Is that any help?

---

