---
title: "FIREFOX The connection has timed out"
date: 2010-06-09
forum: Networking &amp; Wireless
---

### Post by crgalindo on 2010-06-09
I installed the latest ubuntu, everything went fine until i tried to browse the web... firefox gives me a "Connection has timed out" page, everytime.
Checked the network connection, ping [www.google.com](www.google.com), disabled ipv6 from firefox, even access other computers on the network... everything is fine except when trying to surf the web.
I've looked on this forum and on many others and so far i can not find any solution to my problem. PLEASE HELP

---

### Post by sanderd17 on 2010-06-09
Are you sure it's a firefox issue? Can you download another browser like konquerror or epiphany?

---

### Post by mitsumits on 2010-06-09
I have the same problem I think. Firefox is very slow (wireless connection) in responding. But when the connection is established (with a specific site), it goes almost as fast as would normally go with the previous ubuntu version.
Every website takes too long to appear. When I start browsing in the specific website, things are a little bit better.
E.g. I open firefox, homepage google and it takes half a minute to see the page, if it does not time out. But sometimes when I google something, results come out immediately...
On the other hand, when I download updates... 900kB/s or more!
This usually takes my work on windows, cause I can't wait for ages for every website to appear and respond.
Any clues???
Help please.

---

### Post by phred_02 on 2010-06-13
I think it is a DNS issue. I haven't narrowed it down yet, but I think it has something to do with Qwest DSL DNS servers, or my old Actiontec router...

I had experienced the same problem running the live CD on my laptop.  In that instance, I solved it by over-riding the DNS servers to use opendns.com servers.

Today I just installed Ubuntu 10.04 on another computer and ran into the same problem.  I could ping any site from the terminal and any application except firefox seemed to work.  After a little bit of searching I came across this page:

[http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10](http://www.joehacker.com/index.php?title=Ubuntu_Tips#Disable_IPv6_on_Karmic_9.10)

and I followed the directions for Firefox:

Edit the config by opening the page about:config and filter for ipv6.  Toggle **network.dns.disableIPv6** to **true**. 

This seems to have resolved the problem.   So the only conclusion I can draw from this is that either my old Actiontec router GT701-WG, or the Qwest DNS servers do not like the IPv6 dns requests coming from Firefox.

Perhaps this should be listed as a bug, as I would imagine a lot of users could be running into this issue.

Steve

---

### Post by nikalek on 2010-10-11
Hi all,

I'm new with Ubuntu and Linux in general and have been having the connection time out problem since late last night. Was able to access most websites during the first 1-2hours after initial installation of Ubuntu. Tried a different browser, Epiphany and though it gives a different error message, I'm assuming the problem is the same. 

I can access some sites, but for instance Yahoo! Japan fails to load time after time. Also, I wasn't able to log on to my live-account (tried aMSN, and a couple of other applications). 

Firefox error message:
The connection has timed out
The server at yahoo.co.jp is taking too long to respond.

Epiphany error message:
Unable to load page
Problem occured while loading the URL [http://yahoo.co.jp](http://yahoo.co.jp)
Cannot connect to destination (yahoo.co.jp)


Tried disabling IPv6 as instructed by Joe, but wasn't really sure how to go about making the changes and have a feeling I didn't do it appropriately. Changed Firefox configuration as instructed but that didn't seem to have any effect.

I'm on a wireless (usually 70-90% connectivity although Windows gives it a 100%). I seem to lose the connection every 20 minutes or so for a few seconds (during which I'm being reconnected).

Any help is much appreciated,
Aleksi

---

### Post by nikalek on 2010-10-12
Please help, some pages load painfully slow while others don't load at all, getting desperate here.

---

