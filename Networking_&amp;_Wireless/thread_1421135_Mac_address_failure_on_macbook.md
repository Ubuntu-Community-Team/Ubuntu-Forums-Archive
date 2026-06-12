---
title: "Mac address failure on macbook"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by Sozin on 2010-03-03
Hi guys,

I've seen similar questions to this asked a few times but the answers sadly haven't been able to help me.

I'm running ubuntu 9.10 on a macbook and I'm trying to spoof the mac address, not for any sinister reasons.

I can't seem to enable my eth2 wireless using 

sudo /etc/init.d/networking start
but used stop to stop the wireless.

I've changed the gedit /etc/network/interfaces from

auto lo
iface lo inet loopback

to

auto lo
iface lo inet loopback

auto eth2
iface eth2 inet dhcp
hwaddress ether XX:XX:XX:XX:XX:XX

I also tried commenting out the top two "lo" lines.

When I tried this last night at home it was trying to connect to the wireless there, but now it just says "device not managed" in the network manager dropdown menu that normally displays the wireless networks.

What can i do to identify/fix the problem?

Thanks for your help!

---

