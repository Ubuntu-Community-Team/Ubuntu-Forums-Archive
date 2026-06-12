---
title: "Strange Internet Address"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by BigBrotherWatcher on 2011-11-09
Hi everyone. I'm new to Ubuntu (duel boot with win 7) and love it so far. I'm curious about something found in the network tools and hope someone can explain it.

In Network Tools | Lookup | Internet Address of my router, the address is listed as 92.242.144.50, which is in the UK and I'm in California.  Barefruit Ltd. is evidently a DNS mistake ad company, like when we type in the wrong IP and the 404 not found is full of ads.

Also, an nslookup returns (xx is the router name)

> nslookup
Server:        192.168.2.1
Address:    192.168.2.1#53

Non-authoritative answer:
Name:    nslookup.xx
Address: 92.242.144.50

Could this be because of using the Comodo DNS servers? Any other thoughts?

Thanks in advance.

---

### Post by praseodym on 2011-11-09
Did you add the Comodo DNS servers in the network-manager applet? Try the google nameservers 8.8.8.8 and 8.8.4.4 instead. I am using them, too, they are fast and stable.

---

### Post by BigBrotherWatcher on 2011-11-09
> **praseodym said:**
> Did you add the Comodo DNS servers in the network-manager applet? Try the google nameservers 8.8.8.8 and 8.8.4.4 instead. I am using them, too, they are fast and stable.

Thanks for the reply. No, the DNS entries are in the router DNS fields. Is it necessary to make the clients match the router's DNS entries?

No offense, but wouldn't the Google DNS servers collect more info than usual?

---

### Post by papibe on 2011-11-09
Hi BigBrotherWatcher. Welcome to the forums.

Although further tests and info would be needed, that looks like a classic case of [NXDOMAIN hijacking]("http://en.wikipedia.org/wiki/DNS_hijacking"). But not necessarily for harming purposes, since it is usually used for advertisement.

This is how it usually works: they assume you will be using your browser, so when you misspelled an address instead of 'Page not Found', you'll be redirected to a proprietary search page (bypassing also your browser rules).

praseodym's advice is sound. I also use [Google's Public DNS]("http://code.google.com/speed/public-dns/").

Regards.

---

### Post by BigBrotherWatcher on 2011-11-09
papibe, thanks for the welcome and the reply. And for the nxdomain link. I read it but will study it. and its links. For now, I'll try to revert back to my ISP default name servers and hope this strange address corrects itself. If not and after that, I'll try the Google DNS servers. 

Could there be DNS cache poisoning going on?

---

### Post by BigBrotherWatcher on 2011-11-09
So, very strange. I set the router to auto find DNS  from ISP and now nslookup looks like this:

> nslookup
Server:        192.168.2.1
Address:    192.168.2.1#53

** server can't find nslookup: NXDOMAIN

Looks like you get to be right, papibe. The router shows IP, DNS and all the WAN stuff as normal ISP listings now.

Being one that likes to look deeper (at my own peril) I  wonder what happened. Evidently comodo DNS did it but how? Maybe the comodo servers always single out traffic by using what amounts to a reverse IP, one that originates with the client while surfing, something like a tracking cookie. Could this be?

Or maybe it was something else. Now for an address I'm getting something like this:

168.192.in-addr.arpa     (temp, EX) 0   SOA      prisoner.iana.org hostmaster.root-servers.org 

Thanks for the help and if anyone wants to dig deeper, feel free to let me know how to do so. Some Google on it also suggests using the Google DNS. In the mean time I'll try the Google DNS servers. Norton DNS servers are supposed to be pretty good too. Thanks again.

---

### Post by papibe on 2011-11-09
Great!

If you want to keep digging. Here's something interesting for you: [namebench]("http://code.google.com/p/namebench/").

It is a open source tool for DNS benchmarking. It also warn when a DNS hijack your NXDOMAIN.

Regards.

---

### Post by BigBrotherWatcher on 2011-11-10
> **papibe said:**
> Great!

If you want to keep digging. Here's something interesting for you: [namebench]("http://code.google.com/p/namebench/").

It is a open source tool for DNS benchmarking. It also warn when a DNS hijack your NXDOMAIN.

Regards.

Thanks. [namebench]("http://code.google.com/p/namebench/") looks interesting and I'll give it a try.

---

