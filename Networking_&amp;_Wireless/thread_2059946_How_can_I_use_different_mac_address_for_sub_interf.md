---
title: "How can I use different mac address for sub interface?"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by helleon on 2012-09-19
Sorry for my bad English first.

I've few sub interfaces like eth1:1 eth1:2 .... eth1:10 and so on. And I need every sub interfaces use different MAC address.

Firstly I use "ifconfig eth1:1 hw ether xx:xx:xx:xx:xx" to change mac address for ecery sub interface, but all of them use same mac address no matter which one I change.

So I found a tool named mulitimac here [http://www.primianotucci.com/default.php?view=57](http://www.primianotucci.com/default.php?view=57), and change mac address for each sub interfaces successful. But when I checked switch mac table, all of them still use same mac address of br0 to communication.

Now I've no idea to do, any one can help me to do this?

Thanks very much.

---

