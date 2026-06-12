---
title: "problem when simulation network outage using iptables"
date: 2009-02-06
forum: Networking &amp; Wireless
---

### Post by neutro82 on 2009-02-06
Hi, i am trying to simulate a networt outage using iptables.

I configured a little script that closes all ports above 23 (so ssh is enabled)


sudo iptables -I INPUT -p tcp --dport 23:65535 -j REJECT

This works fine

Then I try to delete the rule using:
sudo iptables -D INPUT 1

But nothing happens, the rule remains active and there is no response from the console. The console is frozen, even CRTL+C does not work.
I waited for more then halt an hour, but nothing happend.

After rebooting everything is up an running again and the rule is deleted.

Does anyone know what causes the problem?

For the case it is relevant, I am using Ubuntu 8.04

Thanks in advance
SVen

---

