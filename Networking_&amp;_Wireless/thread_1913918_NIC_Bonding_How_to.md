---
title: "NIC Bonding How to?"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by anoopajay87 on 2012-01-23
Hai...
I have two NIC cards and I tried NIC bonding using these interfaces.
If the hardware(MAC) address of the bonding device is not configured using ifconfig or ip link then it will take the MAC address of the first available slave and it will pass the same to all the interfaces. But for me bonding MAC address is showing as 00 for all 6 octets and for available interfaces showing their original MAC address.
How to resolve this problem? Or is it required to configure manually?
Can we do NIC bonding at server? Or is it restricted only at client side?

Someone please share your thoughts in this regard...

---

### Post by drdos2006 on 2012-01-23
Check out this post.

[http://ubuntuforums.org/showthread.php?p=11320085#post11320085](http://ubuntuforums.org/showthread.php?p=11320085#post11320085)

regards

---

