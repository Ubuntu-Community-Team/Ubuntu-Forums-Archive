---
title: "Getting wlan0 interface to work"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by bks07 on 2011-10-10
Hi there,

I just tried to install ndiswrapper drivers (I followed the steps in a ndiswrapper howto and the extended troubleshooting guide here in the forum) and now my wlan0 interface disappeared completely. I removed ndiswrapper completely but after typing "lshw -C Network" my network controller is still unclaimed.

So, the controller itself is RTL8188CE. I already found it's drivers at the realtek page and - as I already said - I uninstalled ndiswrapper.
I have to say, that my WiFi works before installing ndiswrapper but it resetted every 2 minutes or so - so I tried ndiswrapper.

Ok, question is, how can I get back my wlan0 interface?

Thanks,
bks07

Edit: I'm using an Ubuntu 11.04 on a Lenovo Edge 11" AMD.

---

### Post by bks07 on 2011-10-10
Ok, problem solved.

I just had to do this:
"sudo modprobe rtl8192ce"

But thanks anyway. :)

---

