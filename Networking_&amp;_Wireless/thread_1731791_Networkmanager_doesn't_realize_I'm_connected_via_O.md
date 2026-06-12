---
title: "Networkmanager doesn't realize I'm connected via OpenVPN"
date: 2011-04-17
forum: Networking &amp; Wireless
---

### Post by W0nk0 on 2011-04-17
I'm spending my Sunday fighting with getting my Android phone tethered to Ubuntu 10.10.

I've gotten the tethering to work with the way described in [http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html](http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html).

Now my problem is that I have connectivity for HTTP and maybe more (tracepath works, ping doesnt), BUT NetworkManager doesn't know about it. Therefore, I cannot get the tightliy integrated Ubuntu software to accept that I am indeed connected. Evolution, Messaging etc. all say that I'm not connected.

As the tethering is quite a hacked solution, that isn't all that surprising. Now how do I make NetworkManager KNOW that I am connected? Is there such a thing as letting it know about my tun0 interface managed by the tethering script (via openvpn)? When I look at ip link show tun this is what it says:

```
tun0: <POINTOPOINT,MULTICAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 100
    link/none 

```Obviously, it thinks the interface is not linked.

I am really desperate by now and thoughts of "if only I had Windows on this box" are starting to pop up.... HELP! :(

Thanks in advance,
  W0nk0

---

