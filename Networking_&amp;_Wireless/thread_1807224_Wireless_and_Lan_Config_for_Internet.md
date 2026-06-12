---
title: "Wireless and Lan Config for Internet"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by sswittch on 2011-07-18
I am running Ubuntu 10.10 (Desktop) I currently have a local webserver which serves to iPads and Tablets, which I am using for entry to a competition. 

However I would like to add internet connectivity via the wireless to the webserver so I can send emails (via php)

Someone told me to read up on iptables but I am more than confused.  My internet is on wlan1 and eth0 is where the local webserver is served from.

Could someone please shed some light on this.

Cheers,

sswittch

---

### Post by jmoorse on 2011-07-19
Do you have internet connectivity on the server?  Can you open a web browser or ping [www.google.com?](www.google.com?)

---

### Post by sswittch on 2011-07-20
> **jmoorse said:**
> Do you have internet connectivity on the server?  Can you open a web browser or ping [www.google.com?](www.google.com?)

If I have LAN disconnected, I can connect to the internet via my wireless.  If wireless and LAN are enabled I have no internet connectivity.

The "webserver" in question serves locally over the lan and receives internet wirelessly from my iPhone.

---

### Post by jmoorse on 2011-07-21
Please post following output from when both interfaces are connected and internet connection is down:

```

ifconfig -a
route -n
cat /etc/resolv.conf
dig www.google.com
dig www.google.com @8.8.8.8

```

Thanks

---

