---
title: "Name resolution seriously screwed up"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by klazen on 2009-11-13
Hey all,

I recently switched over to Linux from Windows for my personal use, and am quite happy :). I'm now trying to see if I can't avoid Windows entirely, and am trying to set up my work environment inside Ubuntu. However, when I'm at work, I need to be able to use the terminal service client to use other machines, and need to be able to access the shared documents on these other computers as well. If I directly use the IP of the target machine, everything works like you'd expect. However, using the computer name does not. Also, going to Places->Network will show me the different windows networks (like WORKGROUP), but it will not populate them with the actual computers (I'm assuming that this is related to the resolution issue).

I tried checking what was happening via nslookup, and the results were a little interesting. My computer's name resolves to the correct IP address. One other computer on the network resolves to the address 192.168.27.229, while its actual IP is 192.168.27.29. Three other computers that I checked do not resolve whatsoever. My /etc/resolv.conf file contains one entry: nameserver 192.168.27.1, and that is the IP of the router in the office, so nothing's wrong there.

I just don't understand what's going on here. Any ideas?

---

### Post by Brandon Williams on 2009-11-13
Are you certain that name resolution at your office uses straightforward DNS? Could it be using WINS? Also, what does your /etc/nsswitch.conf file look like (especially the hosts line)?

---

### Post by klazen on 2009-11-13
Thanks, according to your hint, I think I found the problem. I checked the /etc/nsswitch.conf file, and this was my hosts line:
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
From my understanding, that means that if it isn't found via the first two methods, it gives up without even trying dns. I changed it to this:
hosts:          files dns mdns4_minimal [NOTFOUND=return] mdns4
Which I read may solve the issue by letting it check dns. I won't know until Monday, though. Will report back then!

---

### Post by klazen on 2009-11-16
Nope, no dice. Here's the whole /etc/nsswitch.conf (sans comments):

passwd:         compat
group:          compat
shadow:         compat

hosts:                    files dns mdns4_minimal [NOTFOUND=return] mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

---

### Post by Brandon Williams on 2009-11-19
I still wonder whether the other machines' hostnames are resolved via dns or wins (or some other method).

On a windows machine, what happens if you run 'nslookup 192.168.27.1 <hostname>' for one of the hostnames that your Linux machine can't resolve? Can the windows machine resolve it with a request to the server that's in your resolv.conf?

---

