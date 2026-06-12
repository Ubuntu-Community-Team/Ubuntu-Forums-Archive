---
title: "Rhythmbox and Upnp plugin"
date: 2010-12-24
forum: Multimedia Software
---

### Post by ursus262 on 2010-12-24
In the Rhythmbox plugins menu, there is an entry there for UPNP, designed by "coherence".  There is a "configure" button, and when I click on this, a dialogue box opens with two fields: "Port" and "Interface".

Sorry to sound stupid, but what precisely do I put in here to make my laptop talk with my Naim Uniti?

Many thanks

---

### Post by jmate24 on 2010-12-24
no, no one is stupid it just is a simple and valid question. the port number is the number that the device uses to connect to your computer over the network and interface is like perl or python it also may be your device name so try all three until you get your device working you may also check [www.wikipedia.org](www.wikipedia.org) or the device's instruction manual for the port address of your device and i know that wikipedia has a long list but it may help.

---

### Post by Dark_Stang on 2010-12-24
Actually interface is the network interface. Wireless naming convetions are wlan0, wlan1, etc. Hardwired naming convetions are eth0, eth1, etc. If you don't know what your interfaces are called just run
```
ifconfig
```

For the port, just choose any port over 5,000 and below 64,000 and you should be okay.

---

### Post by ursus262 on 2010-12-24
Gentlemen

Many thanks!

---

