---
title: "Linux gurus - how do I redirect IP traffic from one address out to another."
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by geometrikal on 2009-01-26
I have the following situation:

Special ethernet cam connected to linux box on eth0.

Laptop connected to linux box via ad-hoc network on wlan0.

I want the linux box to be kind of transparent, so that I can talk to the cam over the wireless network.

Thanks!

---

### Post by nixscripter on 2009-01-26
I would suggest bridging the two networks. A guide can be found here: [https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

Hope this helps.

---

### Post by geometrikal on 2009-02-05
The box is running open embedded and there is no brctl :(

---

### Post by punx45 on 2009-02-06
open embedded sounds like it makes you do things the hard way :(

[http://www.linuxfoundation.org/en/Net:Bridge](http://www.linuxfoundation.org/en/Net:Bridge)

[http://sourceforge.net/project/showfiles.php?group_id=26089](http://sourceforge.net/project/showfiles.php?group_id=26089)

---

### Post by geometrikal on 2009-02-06
Heh yea, I think I got it worked out now anyway. Setting up the build environment as I speak.. Thanks for the links  

:KS

---

