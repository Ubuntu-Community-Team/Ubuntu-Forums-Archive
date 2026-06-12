---
title: "Wildcard iptables delete"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by OWScott on 2010-01-24
Hello.  I'm brand new to Linux, but a long time Windows administrator, so I understand the concepts, not the syntax.

I've stumbled through setting up Ubuntu Server as a NAT server.  It's working great now.

My goal is to map public IPs to private IPs.  However, I want to change them often through an automated fashion (SSH remote call).  So, I want to run commands that will remove the previous rule and add a new rule, or update the existing rule.

For example, the original rule may be something like:
iptables -t nat -I PREROUTING -d 206.72.119.76 -j DNAT --to-destination 10.240.5.5
iptables -t nat -I POSTROUTING  -s 10.240.5.5 -j SNAT --to-source 206.72.119.76

The issue I'm running into is finding out how to delete the previous entry before adding a new one.  For example, let's say that 206.72.119.76 should now map to 10.240.5.6 (instead of .5).

Is there a wildcard option for the delete rule so that I don't need to know the original destination IP?  i.e.
iptables -t nat -D PREROUTING -d 206.72.119.76 -j DNAT --to-destination [+]

Or, would it make sense to create a script that traverses all rules, gets the existing rule, and then deletes it?

Of course my next issue would be that I don't know any Linux scripting so it's hard to know where to start.

---

### Post by Barriehie on 2010-01-24
I would go with scripting and gawk/awk, I prefer gawk, will be your friend.  You can go, in the terminal, ```
which awk
``` or ```
which gawk
``` and if a path is listed it's installed.  If not, then ```
sudo apt-get install gawk
```.

Here's a manual for [[color="blue"]gawk[/color]](http://www.gnu.org/software/gawk/manual/).

HTH,
Barrie

---

### Post by OWScott on 2010-01-25
Great, thanks Barrie.  It wasn't installed already but your instructions are just what I needed.

---

### Post by Barriehie on 2010-01-25
> **OWScott said:**
> Great, thanks Barrie.  It wasn't installed already but your instructions are just what I needed.

Glad to help.  I'm far from a gawk expert but I'll keep watching this thread. 8)

---

### Post by Barriehie on 2010-01-26
Been thinking about this and may be able to jumpstart you but have a question first.  How are you notified that the IP's need to be changed???  What I'm looking for is some kind of file that has:
```

*OldIp NewIp*

```
i.e. a file that can be processed easily with gawk.  I can see doing this with a shell script that calls a gawk script...

Barrie

---

### Post by Barriehie on 2010-01-30
Removing subscription.

---

