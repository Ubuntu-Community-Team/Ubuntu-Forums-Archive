---
title: "Misconfigured DNS nameservers?"
date: 2006-06-06
forum: Networking &amp; Wireless
---

### Post by sog on 2006-06-06
quick and probably stupid question for all of you.

i've coloed a box in San Diego, and it apparently is not loading/finding the nameservers appropriately. the network information was provided to me by the colo provider, and i know the nameservers work because they resolved everything properly while the box was on my network. 

my /etc/network/interfaces reads as follows (IP's and so on obscured):

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address ##.##.###.###
netmask ###.###.###.###
gateway ##.##.###.###
dns-nameservers ##.##.###.### ##.##.###.#


at this point, i can successfully SSH into the box, but any attempt to wget anything fails to resolve the URI's appropriately. what should my interfaces file look like?

---

### Post by jdong on 2006-06-06
Nameservers go in /etc/resolv.conf....

---

### Post by sog on 2006-06-06
thx much for the quick response, jdong. 

this is my resolv.conf:

search hsd1.co.comcast.net.
nameserver 68.87.69.146
nameserver 68.87.85.98
nameserver 216.148.227.68

can i just change it to:

nameserver 69.55.255.255 
nameserver 69.55.230.3

?

if so, would it be a 

sudo /etc/init.d/networking restart

to reload the network? i'm being specific b/c i don't have local access to the box, so if i screw it up i've got to call support. 

thx much.

---

### Post by jdong on 2006-06-06
nameserver 69.55.255.255 

That is a broadcast IP, not a DNS server IP. Double-check your information.

But yes, that is how you change the nameserver settings. And there is no need to restart the network -- it applies instantly.

---

### Post by sog on 2006-06-06
thx much jdong. i checked, and the provider did send that broadcast IP over as a DNS setting, but after removing it leaving just the single entry DNS is restored. 

really appreciate the help.

---

### Post by jdong on 2006-06-06
you're welcome :)

DNS seems to work better when you're talking to a DNS server, doesn't it?

---

### Post by sog on 2006-06-06
strange, that :)

---

### Post by eboo on 2006-06-07
Hi 

Something similar has been discussed in the this [thread]("http://www.ubuntuforums.org/showthread.php?t=187466"):
[http://www.ubuntuforums.org/showthread.php?t=187466](http://www.ubuntuforums.org/showthread.php?t=187466)

I had a similar problem and resolved. My solution is at the thread above.

Hope this helps

---

