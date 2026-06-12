---
title: "PPPOE - Modem is over a network"
date: 2011-03-06
forum: Networking &amp; Wireless
---

### Post by orpharion on 2011-03-06
I would like to configure a PPPOE connection, but my network is set up in a bit of a confusing way and I have not yet been able to. I tried using pppoeconf (access concentrators could not be found on any of my network interfaces). I know that a PPPOE connection is required because I created one in windows. This is my network layout:
My PC -> wlan0 -> Router (repeater) -> eth cable -> Radio link -> Network (which is where the PPPOE must reach).
I managed to do this in windows without hassle. Any idea how to do it in ubuntu?

---

### Post by dineshs on 2011-03-09
What is the output of```
sudo lshw -C network
```?
Did you try ```
sudo pppoeconf wlan0
```?
Are you using ubuntu 10.10 ?

---

