---
title: "Ubuntu VPS SSH browsing 'connection refused'"
date: 2011-08-07
forum: Networking &amp; Wireless
---

### Post by shmibs on 2011-08-07
hullo. i spend a considerable amount of time using a wireless network which utilises a router-based proxy to monitor every site which it's users visit. i'd rather avoid this, so i typically use either tor or PHP proxies. these work well, albeit slowly, but don't allow me to access client side scripting objects like flash and java web apps.

being annoyed by this fact, i decided to try SSH tunneling to my VPS instead. connecting to the remote machine works well. it is running Ubuntu 10.04.1 LTS and my local machine is running Ubuntu 10.10. i connect to the host machine with:

sudo SSH -D 9999 [username]@[host]

and then configure firefox to reroute traffic through it by heading to manual proxy configuration and then entering:

Socks Host: localhost 
port: 9999 
Socks v5

after doing so, activity is indeed rerouted. the sites i visit register the ip of the host machine rather than mine. however, the router based proxy mentioned above is still able to monitor and/or filter my activity, and all the while i am continually fed error messages through the terminal which read:

channel 9: open failed: connect failed: Connection refused
channel 20: open failed: connect failed: Connection refused
channel 19: open failed: connect failed: Connection refused
channel 21: open failed: connect failed: Connection refused
channel 3: open failed: connect failed: Connection refused

and so on and so forth, cycling between different 'channels.' does anyone have any ideas about what might be going on here? thanks in advance!

---

### Post by tripialos on 2012-04-23
Hi m8, have you found a solution t your problem? I am also having same issue  and still cant figure out whats the problem.

Cheers

---

### Post by wacky_sung on 2012-04-23
Why you don't try [Opendns]("http://www.opendns.com/") which is Free.

---

