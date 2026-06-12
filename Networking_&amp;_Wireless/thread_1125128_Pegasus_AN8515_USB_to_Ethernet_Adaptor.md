---
title: "Pegasus AN8515 USB to Ethernet Adaptor"
date: 2009-04-14
forum: Networking &amp; Wireless
---

### Post by kevsticle on 2009-04-14
Hi,

I have a machine that needs 3 NIC's but only has support for 2 (1 onboard and 1 PCI slot). I don't want to buy a dual NIC card.
I have bought a no-name USB to Ethernet adaptor and it works fine, just plug it in. however, after some hours it drops the connection. Ethtool reports 10mB/half duplex when it is normally 100mB/full duplex. lsusb shows that it is no longer on the list.
The only way to get it to work again that I have found is to physically unplug it and plug it back in when it will then work for a few more hours!
It is on a pretty long cable run (tried and tested on normal NIC card for months on end previously). I have put a single router on there that I had spare to boost the signal just in case the thing is getting overloaded but I don't expect it to help.
Does anyone have any ideas? Even how to restart it without having to go to the server would be a start (I have ssh through another NIC).

Thanks,
Kevin.

**UPDATE**

Ok, the unit has now been up for 24hrs and is still fine so I am thinking the USB port is overloaded driving the long cable run? Anyone have any ideas on this? I don't really want to use a 16 port router to connect one NIC to a modem!!! Thanks.

---

