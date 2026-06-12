---
title: "Uninstalled Guarddog : this dog won't die!"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by bobwyajnr on 2011-05-16
Hi

I am having issues with **iptables** in Ubuntu 10.10. I installed Guarddog to try it out. Didn't like the UI. So I uninstalled it.

Now I have the problem that my **iptables** keep resetting to a broken state (outgoing connections disabled) everytime I reboot! I've used **iptables** quite extensively in the past - so I've whipped up a script to reset them to the defaults.

Where are the **iptables** settings being stored that keeps overwriting the defaults - on a reboot??

Thanks
Bob

---

### Post by jerrrys on 2011-05-17
i do not use iptables, but wonder if you have some guarddog packages still laying around.  will a **locate guarddog **turn up anything?  did you purge guarddog.  like i said, its installed by default, but don,t use it.  can iptables be reinstalled without ill effects?  just some thoughts...

---

### Post by bobwyajnr on 2011-05-17
> **jerrrys said:**
> i do not use iptables, but wonder if you have some guarddog packages still laying around.  will a **locate guarddog **turn up anything?  did you purge guarddog.  like i said, its installed by default, but don,t use it.  can iptables be reinstalled without ill effects?  just some thoughts...

Ha, ha,

But you probably are using [iptables]("http://en.wikipedia.org/wiki/Iptables"). Type the following to prove the fact:
```
sudo iptables -L
```
Most FOSS firewalls for Linux distro's simply write an **iptables** script - using the rules you specify.

By default on Ubuntu, iptables, is set to pass all network traffic (I'm not convinced this is a good idea - but it does ensure you can access the Internet I suppose!) It can be used for all kinds of stuff: to setup a stateful firewall, do packet shaping (e.g. throttling different LAN/Internet network streams by IP address, protocol, ports, etc.), etc. In fact it's the basis of whole Linux distributions e.g. [IpCop]("http://www.ipcop.org/").

I phrased my question wrongly. I should have asked where the **iptables** settings are stored between reboots. The question is not really about GuardDog at all!! I couldn't resist a stupid thread title... :guitar:

I would add a general comment that GuardDog has a pretty pitiful user interface. Personally I would rather write an iptables script by hand!

Bob

---

### Post by jerrrys on 2011-05-17
ok, dumb idea.  good luck

---

