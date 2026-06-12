---
title: "Need help getting traffic to a certain IP routed to a different IP."
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by boaty on 2011-01-01
Hey everyone,

I'm not quite sure how to word it, so I'm going to be as non-technical as possible to avoid using certain terminology incorrectly and confusing everything.  Anyways here's the situation:  I have a java program whose source isn't available.  It goes to a certain IP to load a .txt file.  I want the java program to instead go to my localhost or the IP of my website.  So I'm asking how I can 'redirect' the traffic to the first IP to go to the second IP instead.

I've tried various things with iptables, but no one was very descriptive on how it worked.  My modifications never worked the way I wanted.  The man pages are also kind of confusing for a complete network incompetent person such as myself (I have almost zero networking experience).

So I greatly appreciate any help or advice anyone can offer.  Thanks guys!

---

### Post by PatchesTheCaveman on 2011-01-01
Hi boaty.  Happy New Year!

To accomplish this, simply add an extra IP address to your loopback interface.  To do that, run this command on the terminal:
```
sudo ifconfig lo add <ip>
```

For instance, to reroute 3.3.3.3 to *localhost*:
```
sudo ifconfig lo add 3.3.3.3
```

---

### Post by boaty on 2011-01-01
Thanks!  That's pretty cool but now I'm in another pickle.  I need to somehow set up a 'server' to which this java program can connect and grab a .txt file of my own making.

I'm currently googling how to set up a server on ubuntu, but I don't know if that's exactly what I want.

Happy new year to you too!  Thanks for any assistance :)

---

### Post by PatchesTheCaveman on 2011-01-01
It's most likely a web server.  Try using *lighttpd*, a lightweight HTTP server that works well.

Run ```
sudo apt-get install lighttpd
``` to install it.

The files in /var/www are served by the web server.  You will need to move the .txt file to the appropriate path under /var/www for it to work.

---

### Post by boaty on 2011-01-01
Thank you!  That worked perfectly!  Major props to you

---

