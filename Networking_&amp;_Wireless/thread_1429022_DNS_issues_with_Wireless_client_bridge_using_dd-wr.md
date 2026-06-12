---
title: "DNS issues with Wireless client bridge using dd-wrt"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by pumazi on 2010-03-13
I'm having a **problem resolving domain names** on my Ubuntu 9.10 desktop. It was working a few days ago. The only changes I've made between now and then are the typical Ubuntu updates. The setup looks something like this:

<[COLOR="DarkRed"]cable modem[/COLOR]> [COLOR="Blue"]-- wired connection --[/COLOR] <[COLOR="Red"]router[/COLOR] (192.168.1.1)> [COLOR="Green"]... wireless ...[/COLOR] <[COLOR="Red"]router[/COLOR] with dd-wrt (192.168.1.101)> [COLOR="Blue"]-- wired connection --[/COLOR] <*multiple computers* (including the desktop in question)>

I don't believe the issue is with the router, because other computers use the same configuration mentioned about without issue. Additionally, I upgraded the dd-wrt fireware on the router just in case.

From the Ubuntu computer I am able to:
[LIST]
[*]ping other computers on the network and outside of the network
[*]surf to web sites by IP address (e.g. google)
[/LIST]

What I can't do:
[LIST]
[*]ping google.com ... result is "unknown host"
[*]surf to any domain name
[/LIST]

Any thoughts would be appreciated.

Related threads:
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=821043](http://ubuntuforums.org/showthread.php?t=821043)
[*][http://ubuntuforums.org/showthread.php?t=1291908](http://ubuntuforums.org/showthread.php?t=1291908)
[*][https://www.dd-wrt.com/phpBB2/viewtopic.php?p=118713&sid=2165de899c39cb349859942877e710e8](https://www.dd-wrt.com/phpBB2/viewtopic.php?p=118713&sid=2165de899c39cb349859942877e710e8)
[/LIST]

---

### Post by pumazi on 2010-03-13
What I've tried so far:
[LIST]
[*]manually include an **external nameserver** entry in /etc/resolv.conf
[*]**internet sharing** from my laptop (Mac OS 10.6) instead of the wireless client bridged router
[*]manual and dynamic ip configurations in all cases
[/LIST]

With the internet sharing, I am still able to ping internal and external IP addresses.

This issue definitely has nothing to do with my router setup, but does have something to do with the OS configuration. I'm not sure **where to look next**, so pointers would be very helpful.

---

