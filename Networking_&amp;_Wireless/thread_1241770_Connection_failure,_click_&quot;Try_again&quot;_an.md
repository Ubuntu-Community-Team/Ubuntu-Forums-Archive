---
title: "Connection failure, click &quot;Try again&quot; and it works."
date: 2009-08-16
forum: Networking &amp; Wireless
---

### Post by kaffin on 2009-08-16
Every time I try to visit a page that isn't cached, I get connection failure instantly, the browser doesn't seem to even try loading the page, I click "Try again", and the page loads fine! This is in Firefox and Epiphany (Gecko). In Midori (WebKit), nothing happens at all. I haven't tried any other browser but I figure that the problem isn't browser specific since the same problem occur in Synaptic. When I try to get a package, it fails, I try again and it works.

I can't figure out what the problem is and it's very annoying so if someone could help my out here I would be happy!

---

### Post by Iowan on 2009-08-16
Out of my league (again), but...
What's in */etc/resolv.conf*? Kinda sounds like a slow (or somehow corrupted) DNS server. Why it would fail instantly is curious (I'd expect a timeout, instead).

---

### Post by kaffin on 2009-08-16
The resolv.conf says:
> 
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5291
#
### END INFO



nameserver xx.xxx.xx.xxx
nameserver xx.xxx.xx.xxx
Is it safe to put the actual nameserver values here?

---

### Post by Iowan on 2009-08-16
Always a good idea to make a backup copy first, but you could edit the file.  _IF_ you get IP address via DHCP, that file may get overwritten - in which case, you can edit in your preferred DNS servers on the "prepend" line in */etc/dhcp3/dhclient.conf*.  Same "backup copy" hint applies.

---

