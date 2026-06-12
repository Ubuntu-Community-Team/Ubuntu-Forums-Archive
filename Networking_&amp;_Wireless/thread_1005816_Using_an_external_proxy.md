---
title: "Using an external proxy"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by tetsujin on 2008-12-08
Hello Everyone,

At this point I have almost given up. In our testing lab we have access to a proxy server to get online. I would like to set up something that will transparently redirect all our traffic to this external proxy. 

The main reasoning behind this is our IT department has set up a proxy for us to get to the internet without having to be on the main network. We have a lot of testing computers in the lab that get reinstalled quite often and we do not want to have to reconfigure our proxy settings every single time.

So any suggestions would be great on how to do this. Also if you have any more questions just ask!

Cameron

---

### Post by albinootje on 2008-12-08
Is it allowed in your department to set up a firewall-machine which does all the routing for you ? If so, then you can make this new firewall-machine do the routing and hand out ip-addresses.
Another option is to start using disk-images with software like Clonezilla.
With Clonezilla you can replicate an ubuntu-install within 5 minutes!
I've used it with usb-disk to hold to image. See : [http://clonezilla.sf.net](http://clonezilla.sf.net)
The interface looks a little bit primitive, and you might have to test a few times before you'll understand the concept, but apart from that i think it's totally awesome software.

---

### Post by tetsujin on 2008-12-09
> **albinootje said:**
> Is it allowed in your department to set up a firewall-machine which does all the routing for you ? If so, then you can make this new firewall-machine do the routing and hand out ip-addresses.
Another option is to start using disk-images with software like Clonezilla.
With Clonezilla you can replicate an ubuntu-install within 5 minutes!
I've used it with usb-disk to hold to image. See : [http://clonezilla.sf.net](http://clonezilla.sf.net)
The interface looks a little bit primitive, and you might have to test a few times before you'll understand the concept, but apart from that i think it's totally awesome software.

To my knowledge I am allowed to set up a firewall machine to push out the information and route it to the proxy. At this point though I have attempted something to that extent and it did not work. Any thoughts on how to create the routing computer with ubuntu.

---

