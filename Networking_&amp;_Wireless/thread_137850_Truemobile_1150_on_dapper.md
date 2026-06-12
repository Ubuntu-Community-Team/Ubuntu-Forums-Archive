---
title: "Truemobile 1150 on dapper"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by oyvindh on 2006-02-28
Hi, I have just tried to swap from debian to dapper on my laptop.

I have a strange problem with my Truemobile PCMCIA card. Let me explain.

The card is detected fine and the orinoco_cs and hermes kernel modules are loaded. It pops up in ifconfig just fine and iwconfig reports it to be there. Now, the thing is that I'm unable to get a nework address from my dhcp server. Strange messages are appearing in /var/log/syslog saying:

eth1: LinkStatus=1 (Connected)
eth1: invalid skb-cb magic (0x00000000, expected 0xf08a36a2)
...
eth1: invalid skb-cb magic (0x00000000, expected 0xf08a36a2)

The error persiststs when allocating a static address as well.
I don't use WEP encryption.
The card worked with debian unstable kernel 2.6.12, but not with dapper kernel 2.6.15.

Any takers?

---

### Post by oyvindh on 2006-02-28
I also get:

eth1: hfa384x_get_rid - RID len mismatch rid=0xfd51, len=2 (expected 6)

in /var/log/syslog

---

### Post by oyvindh on 2006-03-02
It seems that the driver is unable to set the hardware address type 801, which is ethernet, right? Also ifconfig says:

eth1   Link encap:UNSPEC HWaddr 00-xx-xx-xx-xx-xx-xx-xx-00-00-00-00-00-00-00-00

This looks bad to me? Anyone with knowledge in the area?

---

