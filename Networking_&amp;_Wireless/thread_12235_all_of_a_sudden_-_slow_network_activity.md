---
title: "all of a sudden - slow network activity"
date: 2005-01-23
forum: Networking &amp; Wireless
---

### Post by machiner on 2005-01-23
...and I see in Firefox's status bar that it is now taking time and:

Resolving host...

Also, when I logged on the weather wasn't updated and it took about a minute to get the temperature.

Any ideas?

I tried to rectify this by adding a DNS (53) rule in allowed everyone in Firestarter. That didn't do anything.

[http://www.madcarters.com/loading.png](http://www.madcarters.com/loading.png)

see the tab next to the Ubuntuforums tab...said loading better than 60 seconds...

I typically get instant response on the web...

---

### Post by machiner on 2005-01-23
Problem fixed.

I commented out the ipv6 entries in my hosts file as following this suggestion:
[http://ubuntuforums.org/showthread.php?t=545](http://ubuntuforums.org/showthread.php?t=545)

I don't know why I suddenly had to do this, but it solved my problem.

That's screwy.

---

### Post by machiner on 2005-01-25
Problem NOT fixed.  I'll be speaking with Verizon tomorrow.

---

### Post by PeteJ on 2005-04-16
We seem to be having very slow and unreliable verizon dsl dns in Massachusetts, USA in recent weeks.   Lots of server not found errors. 

I tried all the about:config tricks I could find and nothing seemed to help (ipv6, pipelining, max connections, etc).  I tried disabling ipv6 in my /etc/modules.conf and in /etc/modutils/aliases, to no avail. 

So...knowing in my gut that it was a dns problem, I stumbled across someone recommending using dns server 4.2.2.4 (vnsc-pri-dsl.genuity.net.) and then I stumbled across the opennic project 
[http://www.opennic.unrated.net/public_servers.html](http://www.opennic.unrated.net/public_servers.html) (really cool, check it out)
and so now my resolv.conf looks like this, and my dns and browsing performance has been awesome for 24 hours now:

petjal@ubuntu:~ $ cat /etc/resolv.conf
search local.domain
nameserver 4.2.2.4
nameserver 216.87.84.209
nameserver 151.202.0.85  # old verizon
nameserver 151.203.0.85  # old verizon

(I thought I read somewhere that only the first 3 nameserver records are used.)

Maybe somebody has an improvement on this trick?

Enjoy,
Pete

---

### Post by wad on 2005-04-25
Your advice is a sound solution to the nameserver problems of Verizon customers in eastern MA.  Pointing to a nameserver other than Verizon is recommended as they are dropping lots of incoming packets.  They need to add more servers, please give them a call and let them know.

You can easily verify this under Linux.
dig @151.203.0.84 www.whitehouse.gov
returns "connection timed out; no servers could be reached"
more often than not.  Yet:
dig +tcp @151.203.0.84 www.whitehouse.gov
returns pretty reliably within a 100 mS.

Anybody know how to force bind9 to use TCP for the initial connection ?

wad

---

### Post by wad on 2005-04-27
I called Verizon and reported the problem.
They are unwilling to admit that there is a problem, and
flatly stated that they could not help me.

If you are a Verizon customer and are experiencing this problem,
please call them and let them know that their DNS servers are
overloaded and slow (actually, I suspect it is the network link to
the server, not the server itself, which leads them to believe that
nothing is wrong).

Any suggestions for alternative DSL providers in eastern MA ?

wad

---

### Post by fallen0047 on 2005-04-29
I was having similar slow problems after installing the released version of Hoary.  I would timeout getting a DHCP  response.  I set fixed the IP addr and was VERY slow.  I plugged in my XP laptop and got served up immediately - eliminate mechanical issues - It turned out to be the onboard network adapter.  What's the fallacy of logic? post hoc ergo prompter hoc?  Added a spare NIC and am back and Ubuntu'ing.

---

### Post by lespedeza on 2005-05-24
the advice in this thread works great if your internet provider has slow DNS servers, but one thing you might want to consider is editing your dhclient-script as described in this thread

[http://ubuntuforums.org/showthread.php?t=545](http://ubuntuforums.org/showthread.php?t=545)

my resolv.conf file would get overwritten every so often resulting in slow DNS resolution until i edited the resolv.conf file again.  

just thought i'd add that little part.

---

