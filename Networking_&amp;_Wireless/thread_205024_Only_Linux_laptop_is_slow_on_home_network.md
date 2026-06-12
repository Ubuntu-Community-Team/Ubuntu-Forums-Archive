---
title: "Only Linux laptop is slow on home network"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by cartur25 on 2006-06-27
Hello,

I am on an Acer 1691WLCi trying to surf the net on a home network with a Linksys WRT54G v4 router.

My linux box surfs the net fine sometimes, but it has regular and frequent periods of slow to no internet speed when browsing. This does not happen on any other laptop in the network or desktop computer. My laptop is connected via ethernet cable and is not running wireless.

I am running 1.5.0.4

Any suggestions?

---

### Post by Azrael on 2006-06-27
It might be attempting IPv6 DNS look ups. Try this: type *about:config* in Firefox's address bar. Then toggle (right-click) the entry *network.dns.disableIPv6* to *true*.

---

### Post by drfox on 2006-06-28
Azrael, I don't know if it helped cartur, but it sure helped me. Thanks a lot!!!

Now, I have the same problem with Evolution---I can't connect to my POP email. Is there a similar setting system-wide or just in Evolution?

Thanks again.

Larry

---

### Post by cartur25 on 2006-07-01
That seemed to work for a few minutes, any other ideas?

I'm starting to have a feeling that the problem is actually with firefox because even when my internet is slow, download speeds are very fast still.

note: this does not imply that I am downloading (e.g., torrents) while web surfing. I just mean http downloads are fast while web surfing w/o active downloads cycles from fast to painfully 56k modem slow.

---

