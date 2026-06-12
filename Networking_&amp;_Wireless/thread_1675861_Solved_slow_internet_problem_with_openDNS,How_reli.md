---
title: "Solved slow internet problem with openDNS,How reliable is openDNS?"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by fasoulas on 2011-01-26
I had a problem for a long time with all the apps that required internet connection ,and for a long time i wasn't using ubuntu because of this and because i didn't have time to search and find a soution to the problem.All browsers were taking to long to load a website and some times timed out.

So yesterday after making some research on the net i found that this was a problem with dns and a lot of people had this problem after some updates ,like i had.

The problem for me seems to be my router and the way ubuntu handles dns requests.

i found some very useful info here

**[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/417757)**

I updated the firmware of my router(linksys) but still i had the same problem.
Another solution i found and this worked ,is to use the openDNS servers instead of my own ISPs dns servers.

[B]openDNS ips
208.67.222.222 208.67.220.220[/B]

I am posting this because i saw many ubuntu users having these problems and the only solution they get from other users is to disable IPv6 support in ubuntu or firefox but this doesn't work most of the time like in my case.I have to mention that i had this problem only on ubuntu and not in my windows installation.

And finally the question i want to ask is how reliable is the openDNS?

I mean is it secure to use it instead of my own ISPs dns servers?

Thanks for reading ,and sorry for the long thread.
I just wanted to share a solution to a problem may users have.

---

### Post by Grenage on 2011-01-26
We use OpenDNS as a forwarder for our main office, and have done for years; we've never had a problem.

> **fasoulas said:**
> I mean is it secure to use it instead of my own ISPs dns servers?

As far as trust goes, who can you ever trust?  While I'd say 'it's only DNS', many people do seem to care greatly about it.

---

### Post by ripat on 2011-01-26
There is nothing wrong in the way Ubuntu (and Debian BTW) format their DNS requests. But there is definitely something wrong the way some nameservers discard the quad-A request without sending a proper reply to the sender.

OpenDNS is not the only alternative, you could also try Google's nameservers:
[http://code.google.com/intl/fr/speed/public-dns/](http://code.google.com/intl/fr/speed/public-dns/)

Or:
[http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/)

---

