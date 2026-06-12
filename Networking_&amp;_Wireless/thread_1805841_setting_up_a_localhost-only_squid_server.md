---
title: "setting up a localhost-only squid server"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by Coder543 on 2011-07-16
I'm going to be going off to college in the fall and the internet probably won't be blazing fast like it is at home, so I was wanting to set my desktop up so that it would act as a local cache of the parts of the internet i frequent the most, but I can't find anything like that. All the tutorials I've found are either for sharing the load on a server or for setting up a separate machine as the squid. Can anyone help?

---

### Post by jmoorse on 2011-07-16
IMHO it won't make much of a speed difference.

If you still want to do it follow the guide that shows how to set up a squid proxy on a another machine, do it on your desktop, and set your proxy IP to 127.0.0.1.

---

### Post by Coder543 on 2011-07-16
It would make a huge speed difference, if I have a 5 GB proxy cache on my 120GB intel SSD in my desktop computer, reading webpages at 3200 Mb/s versus 30 Mb/s would be a huge improvement, not to mention once I get to my college where the speed difference will likely be a lot more dramatic. Unless you're suggesting something I haven't thought of. What would make it not much faster?

---

### Post by jmoorse on 2011-07-16
My experiences have been with standard 7200RPM HDs, and this was several years back, so maybe you will have better results!  I would be interested to see how it turns out.

Remember the proxy is only going to cache certain types of content and most current browsers are going to cache most content on your SSD already.

---

