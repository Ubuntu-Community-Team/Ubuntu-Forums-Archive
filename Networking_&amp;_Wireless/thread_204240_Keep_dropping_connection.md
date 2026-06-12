---
title: "Keep dropping connection"
date: 2006-06-26
forum: Networking &amp; Wireless
---

### Post by Elvish Legion on 2006-06-26
I have an IBM T40 Laptop (it has an ntel 802.11b Wireless(MPCI)).

My wireless router is  Linksys WRK54g.

Now my question is, my laptop keeps dropping connection, I suspect a configuration error, but where would I begin to look to correct?

Do I maybe need to use the ndiswrapper?

---

### Post by DarthMandeep on 2006-06-26
If the card itself works, I don't think you'd need to switch to ndiswrapper.

I'd check and make sure you're connecting to the right access point. What does the "iwconfig" program tell you when you run it in a terminal? What does your /etc/network/interfaces file say?

---

### Post by ubercat on 2006-07-02
My research reveals that this isssue is somewhat ubiquitous. 

I've installed both ubuntu 6.06 (mailed CD), and xubuntu (iso) using Belkin F5D6020 cards for Wireless access, and both machines drop their connections constantly when idle.  In fact, the connections aren't available when the system reaches the desktop - I have to start/restart the network via CL into compliance.

However, idle time seems to be the culprit; running a terminal with a ping set for once a minute holds the connection while not actively accessing the network (old dial-up trick). It's a royal pain, and there was no such loss of connectivity under 5.10.

---

### Post by wieman01 on 2006-07-03
Posting the "/etc/network/interfaces" file would help a lot. I have experienced similar issues in the past, but I could resolve them by carefully adjusting the "interfaces" file.

WPA supplicant seems to one of the culprits.

He

---

