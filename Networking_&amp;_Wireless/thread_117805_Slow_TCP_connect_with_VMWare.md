---
title: "Slow TCP connect with VMWare"
date: 2006-01-15
forum: Networking &amp; Wireless
---

### Post by jondreads on 2006-01-15
Hello,

First let me apologise in advance for my first post here being a question, but I've been struggling with this problem on-and-off for quite a while!

I've been using Kubuntu 5.10 (and previously 5.04) as guest OSes in Windows XP.

On my main desktop box (XP Pro, VMWare Workstation 5.5) I'm using a bridged network so that I can access Kubuntu from the 'net. Internet connections from this box are generally slow (10 seconds to connect) and Firefox usually shows 'Looking up ...' during this time which made me think that the problem was with my DNS config. Here's the catch though, some apps are slow, some are quick.

E.g. 
dig [www.cisco.com](www.cisco.com) - < 50 ms
wget -N  [www.cisco.com](www.cisco.com) - 1.3 seconds

telnet [www.cisco.com](www.cisco.com) 80 - 10 seconds to connect
Ditto Firefox, Konquerer, Lynx ...

I've disabled IPV6 but to no avail... The machine (and virtual machine) has bags of memory and CPU power.

I had similar problems with VMWare 5.0 and Kubuntu 5.04, though 5.0 seemed to work OK with Mepis (before I abandoned it in favour of Kubuntu ;-). Everything works OK on my laptop though that uses Kubuntu in a NAT network. 

Any thoughts?

Thanks!
Jon.

---

### Post by Mr_Grieves on 2006-01-15
Do you have anything more reliable to test against? Like devices in your local network? What happens if you connect your computer directly to the "internet" without NAT?

What's happening "under the hood"? Is anything being send from/to you out on the network during the waiting periods? Try tcpdump.

```

apt-get install tcpdump
tcpdump ip host <target_ip>

```

---

### Post by jondreads on 2006-01-16
[QUOTE=jondreads]

telnet [www.cisco.com](www.cisco.com) 80 - 10 seconds to connect
Ditto Firefox, Konquerer, Lynx ...
[/QUOTE]
I forgot to mention here that if I use the IP address instead of the host name then there are no problems with telnet, firefox etc., 

Jon.

---

### Post by jondreads on 2006-01-16
[QUOTE=Mr_Grieves]Do you have anything more reliable to test against? Like devices in your local network?[/QUOTE]

Other devices in my local network are configured using static addressing and they work fine.

[QUOTE=Mr_Grieves]
What's happening "under the hood"? Is anything being send from/to you out on the network during the waiting periods? Try tcpdump.
[/QUOTE]
Ah, this shows some interesting results. Different queries DNS are being sent out to my router depending on the application initiating the request. 

In the case of the slow applications there appears to be two queries sent to my router, both of which take 5 seconds to time out, followed by a query that returns quickly. The quick applications just issue this final query, hence their speed.

I don't have time to investigate this fully tonight, hopefully I'll be able to devote some time to this tomorrow.

Many thanks,
Jon.

---

