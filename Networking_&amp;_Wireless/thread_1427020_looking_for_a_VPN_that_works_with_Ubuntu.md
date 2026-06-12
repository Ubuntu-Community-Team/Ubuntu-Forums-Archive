---
title: "looking for a VPN that works with Ubuntu"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by v1nsai on 2010-03-11
I have tried every single free VPN that I can find, and not a single one has worked.  The best result I can get is authenticating on the network, but my pings all reply "ping: sendmsg: Operation not permitted".  I'm not against paying for a VPN service, but I can't find one that openly supports Linux.

A search of 'VPN' in the forums reveals that a lot of us seem to be having problems with VPNs.  If you are happily using a VPN that works, come share your success with us please!

EDIT
I got UltraVPN and itshidden to run by flushing iptables and turning off firestarter, i.e.
```

sudo iptables -F
sudo /etc/init.d/firestarter stop

```

I'd still be interested in what VPNs others have gotten to work, however.

---

### Post by dmizer on 2010-03-11
I have OpenVPN working perfectly, and have been using it for many years: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

### Post by afrodeity on 2010-06-20
Thanks, will give Ultra a try. Haven't managed to get itshidden working yet.

---

### Post by v1nsai on 2010-06-20
openvpn is a protocol, what service are you using with it? Or did i miss something in the link?

---

### Post by afrodeity on 2010-06-20
[http://www.kabatology.com/11/24/how-to-setup-open-source-ultravpn-in-ubuntu/](http://www.kabatology.com/11/24/how-to-setup-open-source-ultravpn-in-ubuntu/)

Excellent tutorial. I now have a VPN showing in addition to Auto etho0 connection.

How does one go about using it?

---

### Post by v1nsai on 2010-06-21
You just click on it in network-manager

I can't get itshidden or ultravpn to work with lucid though

EDIT:
hey flushing iptables like I mentioned above has itshidden working for me, still no luck with ultravpn though.

---

