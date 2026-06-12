---
title: "Ubuntu and network logging?"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by TheAlien on 2009-12-31
Is there a way to get Ubuntu to continuously and permanently log all input and output packets going trough my eth0 device to a text file with dates, times, ip-addresses and ports, without using third-party applications like Wireshark? I would like this to just stick in the background and be active from the system boot without needing to run a third-party application, and just look trough it when or if needed.

I'm a fresh Linux admin and would appreciate some help to set this up.

:)

---

### Post by TheAlien on 2010-01-01
I'm just bumping this one up in case someone should be able to help me.

---

### Post by puppywhacker on 2010-01-01
snort logs traffic like you said, although it might fall under your interpretation of third-party application. (I think ubuntu is mostly neatly packaged 3rd party)

```
sudo apt-get install snort
```

---

### Post by TheAlien on 2010-01-18
Sorry for the late reply.

I managed to get tcpdump that comes with Ubuntu to do this.

Now my computer log all network traffic from boot time and stores it in a file. I can even use Wireshark to read the outcome of these files.

If anyone wants help to set this up, just let me know. I'm not going to write this down unless someone needs it.

---

