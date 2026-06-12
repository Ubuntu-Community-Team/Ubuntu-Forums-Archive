---
title: "how to STOP network manager from auto-reconnecting"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by GTOkid on 2011-04-11
Hello,

I am running openVPN to secure my wireless network traffic right now. Everything works great except every once in a while, my Internet connection will drop out for about a minute or so. Ubuntu very nicely tries to reconnect, and most of the time successfully does. The issue is that if I don't catch it every time this happens, I am now running without my VPN, it's a huge pain.

I want to know if there is any way to DISABLE auto-reconnect to a wireless network if connection is lost or signal fades.

Thanks

[edit] im running ubuntu 10.10 by the way

---

### Post by cbowman57 on 2011-04-12
Pretty sure you can R-click on the network manager -> Edit connections -> Select the offending connection -> Click 'edit' -> un-check the 'auto' box.

Of course you'll have to authenticate, etc.. but those steps should get it done.

---

### Post by GTOkid on 2011-04-12
I have tried that, while it will stop ubuntu from auto-connecting to the network, it fails to stop it from auto RE-connecting :/

---

### Post by cbowman57 on 2011-04-12
Hmm.. there probably is a way to make network-manager quit doing that but I don't know what it is.
Been awhile since I used wicd but I think that option was easily configurable via a checkbox. You might want to give that one a try if an answer isn't forthcoming here in the forum.  

Make sure to post your solution here if you find one.

---

