---
title: "Router can ping, connected machines can't"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by mockdeep on 2011-02-16
So this isn't really an Ubuntu specific problem, but I figured I'd start my hunt here.  I'm running into a curious networking hiccup with my router setup.  I have a D-Link DIR-628 wireless router connected to our modem, and a wire running from that to a Linksys WRT-54G (v1.1) in our basement.  This setup worked great for a few days, but then suddenly the Linksys stopped routing us to the internet.  I can connect to the router page on the Linksys and using the diagnostic tools I can ping the web from there, but none of the computers connected to it can.  Everything is fine when connected to the D-Link.

After fiddling around with just about every setting on the Linksys I finally gave up and tried resetting it to factory defaults--and it worked!  Everyone could access the internet again.  But then, every day or two it locks up again and I have to reset factory defaults again.  What is happening here?  How can I permanently fix this problem?

---

### Post by mockdeep on 2011-02-18
No advice on this?  Is there a better place for me to post?

---

### Post by bhaverkamp on 2011-02-18
One thing to check. When daisy chaining routers you should disable DHCP on the secondary routers. If you don't you will have a very confused network that could lockup.

---

