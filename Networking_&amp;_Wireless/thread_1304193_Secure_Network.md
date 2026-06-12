---
title: "Secure Network"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by dontgetshocked on 2009-10-29
My name is Forest Gump and I'm not a smart man.I have a desktop with Ubuntu on it and a Netbook with xp.Right now my Netgear wireless router network is not secure.Do I secure it via the router configuration and if so using which pc? Or secure it using the network settings?

---

### Post by t0mppa on 2009-10-29
Via the router configuration. Routers usually have a web interface, to which you can connect with any computer that's in its network by typing the routers IP on the address line of your browser. You can find out your routers IP by right-clicking the Network Manager icon, choosing connection information and checking the default route or by running **netstat -r** on terminal and checking the gateway of the default route.

If you're unable to get the above to work, then I suggest you refer to your routers manual. And in case you chucked it into garbage a long time ago, try going to manufacturers website and see if they have one there.

Once you do make your way to the configuration, be sure to pick WPA2 (or just WPA) encryption if possible, since WEP is very easy to crack (can even find a bunch of threads on this forum how to do that) and thus not much of a step up in security.

---

