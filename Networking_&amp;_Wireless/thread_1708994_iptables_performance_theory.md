---
title: "iptables performance theory"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by ant2ne on 2011-03-17
Suppose I was using an iptables firewall/filter by limiting traffic with something like this...
```
iptables -A FORWARD -d   xm.123123aqa.com -j REJECT
```
But maybe there was a few thousand or so lines like that. And lets suppose this filter is on a dual process with 4Ggis of RAM. What kind of performance degradation would one expect to see?

---

### Post by SeijiSensei on 2011-03-17
It would be indistinguishable to most any human even on a much slower machine than that.  All the processing happens in memory at CPU speeds.  iptables, and the entire Linux TCP/IP networking stack, are very efficient.

I have hundreds of rules in my iptables firewall.  They make no discernible difference in the performance of my network connection.  My firewall is an old P4, by the way.

---

### Post by ant2ne on 2011-03-17
I was thinking along those lines but wasn't sure.  BTW, does that command look correct for the function I want it to perform? This firewall/filter is a masquerading type device.

---

### Post by SeijiSensei on 2011-03-19
> **ant2ne said:**
> I was thinking along those lines but wasn't sure.  BTW, does that command look correct for the function I want it to perform? This firewall/filter is a masquerading type device.

If you want to block access to [www.example.com](www.example.com), use an INPUT rule like:

```
iptables -A INPUT -d www.example.com -j REJECT
```

although the FORWARD rule you propose probably works equally effectively.

WHat's more important is the order of rules.  Make sure all the blocking rules come at or near the top of the ruleset and certainly before any NAT rules.

---

### Post by ant2ne on 2011-03-20
i want hosts from inside the firewall to be unable to contact the listed sites, as well as the sites outside the firewall from contacting the hosts.

---

### Post by SeijiSensei on 2011-03-20
> i want hosts from inside the firewall to be unable to contact the listed sites, as well as the sites outside the firewall from contacting the hosts.

Denying with an INPUT rule means that requests for a banned host from any machine arriving on any interface of the firewall will be rejected.  Denying in the FORWARD chain accomplishes the same result but only after the packet has already been accepted by the INPUT chain.

Sites outside the firewall should never be able to contact any hosts behind the firewall, or even connect to the firewall itself except under restricted circumstances.  The simplest way to ensure that unauthorized traffic cannot cross your firewall is to set its default policies for both INPUT and FORWARD to DROP or REJECT.  (The latter informs the sender of the rejection; DROP silently ignores the sender's traffic.)  You can  specify a default policy with

```

iptables -P INPUT DROP
iptables -P FORWARD DROP
#iptables -P OUTPUT DROP

```

I usually leave OUTPUT to its default of ACCEPT because I trust my internal machines, but you can play with the implications of setting OUTPUT to DROP as well. 

I also include LOG and DROP rules at the bottom of the ruleset to catch and log traffic that fails to match a rule like this:

```

# log and drop everything unmatched on the floor
iptables -A INPUT -j LOG    --log-prefix INP_REJ_
iptables -A INPUT -j DROP

iptables -A FORWARD -j LOG --log-prefix FORW_REJ_
iptables -A FORWARD -j DROP

```

You'll see all the unauthorized traffic in /var/log/messages.  The prefixes let me discriminate between traffic blocked by the INPUT rule and traffic blocked by the FORWARD rule.  These rules let me see the amount of unauthorized traffic if I run "sudo iptables -L -nv".

I will add that if you're concerned primarily about controlling HTTP access to remote sites, you should look into running the Squid caching proxy in "transparent" mode.  See this [Guide]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch32_:_Controlling_Web_Access_with_Squid") for details.  Squid gives you enormous control over web requests, allowing you to filter them by any broad array of characterstics include source and destination IP addresses and hostnames, requested filenames, MIME types, POST vs. GET methods, etc.

---

### Post by ant2ne on 2011-03-23
What is the difference between setting the policy like this..
```
iptables -P INPUT DROP
iptables -P FORWARD DROP
```

And putting this at the bottom of the script...
```
iptables -A INPUT -j REJECT
iptables -A FORWARD -j REJECT
```

In my mind they do the same thing. If the packet goes down the list of rules and did not get accepted then the packet should hit this rule and get rejected, right?

---

