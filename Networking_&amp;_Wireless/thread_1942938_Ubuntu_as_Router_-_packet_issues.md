---
title: "Ubuntu as Router - packet issues?"
date: 2012-03-18
forum: Networking &amp; Wireless
---

### Post by jcook818 on 2012-03-18
Hello,

I have just set up Ubuntu Server on a VM machine to act as a router on  my network. One of its network interfaces is connected to the modem  using PPPoE, and it is routing to another interface connected to a  wireless access point which is in turn serving my local network. While  using a client connected to this network, everything seems to go well  with the internet connection. However I've noticed that downloading a  podcast from iTunes on a client computer (i.e. a file of more than ~20mb) generates a 9006  error. This is strange, as I can download files of any size with other applications without a problem. Apple says "Your default packet size being set incorrectly can  cause this error." I have no idea what to look for in my Ubuntu Server  setup that can help me address this problem, which appears to be the  Ubuntu Server not adjusted to accept packets of a certain size, and I  could download whatever I wanted with my old router without issues... I  have looked up what I can, my MTU is at the same level as my old router,  etc. Does anyone know what might be causing this issue?

I am using iptables to do the routing as specified here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) I am also using dnsmasq as a dhcp server. This is a brand-new installation and I haven't done much beyond what was outlined in the linked article.

Thank you!

---

### Post by jcook818 on 2012-03-20
After doing more testing, I've noticed that the download stops after exactly 60 seconds each time, regardless of how much data has been downloaded.

---

