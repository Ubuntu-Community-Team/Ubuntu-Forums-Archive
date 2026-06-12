---
title: "Problem connecting to router (Netgear DG834)"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by kavoura on 2010-07-12
I have a Netgear DG834 ADSL router (v3) which I have used for a couple of years. Prior to that I had a v2 of the same router, but upgraded for the one that supports ADSL 2+ (here in the UK).

Recently I have been having problems with the connection often being dropped, and when I access 192.168.0.1 for the router admin page, when it is not working I get no IP address listed for that of the ISP's server, and sometimes as well the upstream and downstream speeds are listed as 0 kbps.

Usually this was resolved by rebooting the router.

However, for the last couple of days, when using Ubuntu 9.04, the page of the router at 192.168.0.1 will not load. I have tried numerous different browsers, and none of them will give the router admin page.

When I tried booting from a live CD of Fedora 13, the router admin page came up just fine, no problems (although still not getting a proper connection to the Internet).

I was going to try to use the older router I had, but so far, as I cannot access the router admin page in Ubuntu, I have not done so (not had the time, and now I am at work posting this).

So there must be a problem in Ubuntu that is preventing it showing the router's admin page. The Network connection details show that the router has given the PC an IP address of 192.168.0.6 and the DNS servers are listed, so I know that Ubuntu is talking to the router, but it is not allowing me to access its settings in any way.

What could be the cause of the problem, and how do I solve it (other than maybe reinstalling Ubuntu)?

---

### Post by kavoura on 2010-07-13
UPDATE

Using a different router made no difference in Ubuntu 9.04. I then decided to try it from my netbook (running Xandros) and that worked fine to give me internet access via the new (borrowed) router.

So I booted my main PC using the old installation I still have on it of Ubuntu 8.04, and in that I can also access the internet okay.

So I know it is not a hardware fault in the PC. The old router I was using needs replacing. But what can cause Ubuntu 9.04 to block all internet access (except for Skype which did work)?

---

