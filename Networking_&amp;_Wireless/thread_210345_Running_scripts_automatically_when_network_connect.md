---
title: "Running scripts automatically when network connects"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by brickhead20 on 2006-07-06
Hi, I was wondering if there is a way of running scripts automatically when a network interface (i.e. eth0 or wlan0 / ra0) connects.

I want to do this to run wget on a Dynamic DNS service in order to update the IP information. I want this to be run any time the interface is reconnected. Also if the internet connection to the router goes down, is there a way of running the scripts when the router reconnects? Generally this will apply to the eth0 ethernet interface, but may also need to apply to the wireless interface (ra0, a Ralink chipset wireless card). I would appreciate any help anybody could give me.

Or maybe theres a way of running the script every, say, ten minutes or so?

Any help would be very much appreciated,

Thanks,

Rich

---

### Post by brickhead20 on 2006-07-07
Anyone?

---

### Post by mpvano on 2006-07-07
Read the man pages for interfaces, ifup, ifdown and friends.

You can place a script in one of the appropriate subfolders that will be called at the corresponding network changes. There are probably already some installed on your machine to do similar things you can look at as examples....

Mario

---

### Post by brickhead20 on 2006-07-07
Ok thanks.

---

