---
title: "Wireless problems - slow or won't connect"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by jdfoote on 2010-01-15
I have been struggling with some wireless problems for a while. Any help would be greatly, greatly appreciated.

Here are the symptoms:

My wireless was working just fine until a few days ago. At that point, anything that connects to the internet started going really, really slow.

Then, it started asking me for the WEP key over and over again, and wouldn't connect at all. Recently, it has started to connect again, but it is very, very slow.

lshw -C network shows that I have a Realtek RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller, with the logical name wmaster0, and the rtl8180 driver.

/sbin/config -a shows both a wlan1 entry, and wmaster0. I don't understand why it does that, and I don't know if that has anything to do with the problem?

Please help! :)

---

### Post by superprash2003 on 2010-01-15
is it just the browsing experience or internet download speeds?? what does [www.speedtest.net](www.speedtest.net) say?

---

### Post by jdfoote on 2010-01-15
I didn't figure out what the problem was, but it seems to be fixed.

I removed the wireless card from the PCI slot, restarted, shut down, put the card back in, and restarted again, and now it's working.

---

### Post by ockky on 2010-01-30
> **jdfoote said:**
> I didn't figure out what the problem was, but it seems to be fixed.

I removed the wireless card from the PCI slot, restarted, shut down, put the card back in, and restarted again, and now it's working.

Wow.  i was experiencing the exact same problems and following your steps to remove the card and reboot straightened everything right up.

thanks for posting your solution

---

