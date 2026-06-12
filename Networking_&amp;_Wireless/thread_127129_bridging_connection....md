---
title: "bridging connection..."
date: 2006-02-08
forum: Networking &amp; Wireless
---

### Post by woedend on 2006-02-08
Hello...I am interested in bridging connections which windows made seemingly easy.  Basically, I need one more port for my brothers play station 2.  Rather than buy another router or ab igger router i'd rather just buy a cheap network card to throw in my PC(which runs inactive most of the time anyhow) and run it out to his ps2.  Is this possible/easy with ubuntu and can anyone point me in the right direction?  thanks,
woe,

---

### Post by hollinch on 2006-02-08
Not an expert on the subject, but you'd need to set up a different IP range on the extra LAN adapter as your primary LAN (internet) connection, and by enabling ipforwarding allow your Ubuntu box to act as a router. See this [thread]("http://ubuntuforums.org/showthread.php?t=58753") for a similar question.

Example: if your primary LAN has IP net 192.168.1.0, set your other adapter to 192.168.2.0 for instance. By enabling ipforwarding your system will now allow routing between these two LANs.

There's more needed in terms of DNS etc, but there's more that you can find by searching for ipfowarwarding.

Hope this helps.

Cheers, Jaap.

---

### Post by mips on 2006-02-08
[http://ubuntuforums.org/showthread.php?t=111972](http://ubuntuforums.org/showthread.php?t=111972)

---

