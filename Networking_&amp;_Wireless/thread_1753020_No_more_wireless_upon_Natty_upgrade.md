---
title: "No more wireless upon Natty upgrade"
date: 2011-05-08
forum: Networking &amp; Wireless
---

### Post by dargaud on 2011-05-08
Hello all,
I just updated my work laptop to Natty: perfect. My home server: perfect. My oldish home laptop: no more wireless.

[I use wicd instead of Knetwork (or whatever it's called) because I want a permanent connection no matter the user]

I have a D-Link DWA-645. I get the whole stage: connecting, authenticating, etc... and bad password at the end. The password is correct (hasn't changed during upgrade). I also tried disabling WPA and it still won't connect. That's wlan2.

I also tried with an older PCMCIA card that _used_ to work on ubuntu 9, but stopped on version 10: a D-LinkDWL-G650. It doesn't even show up as wlan0 as it used to.

I also tried with a USB-wifi DWL-G122 which has always worked on every version of Ubuntu [I don't normally use it because it's not practical on a laptop]. I see it as wlan1, but same thing: won't connect. Note that like with wlan2 I can scan for networks and see several around. For instance:
```

$ iwconfig
IEEE 802.11bg
ESSID: off/any
Mode: managed
Access point: not associated
Tx power: 20 dBm
Retry long limit: 7
RTS thr: off
Fragment thr: off
Power management: on

```

Now I wonder what is broken: wicd ? The driver(s) ? Some intermediate wifi layer ?

I've enclosed a zipped copy of dmesg and wicd.log

[Edit]
Some more info: the access point works fine, I can connect with another device. The driver in use by Ubuntu is ath9k. Using KnetworkManager instead of wicd doesn't change anything.

---

### Post by dargaud on 2011-05-09
No taker ?

OK, some more info. After plenty of attempts (but without changing any significant parameter) I managed to get the DWA-645 to work exactly once. On the next tries it didn't.

And I can now get the DWL-G122 to work almost every time. But every time the computer reboots, sleeps or is left unattended for a while, it drops the connection (3 feet away).

I'm really flustered by this situation: 3 different wifi cards all acting flaky on a system that worked perfectly with 10.10 before ?!?

---

### Post by dargaud on 2011-05-12
Still no taker ? OK, I give up, what CardBus wifi card should I purchase to have b/g/n ?

I just spent hours testing my _4_ cards on my current install and with the 11.04 livecd on 2 different access points b/g and b/g/n and I can't make any sense of the results which I won't even try to sum up here. At worse they see the SSIDs but won't connect. At best they connect but slow as molasses and disconnect regularly. 

**** that ****: every new Ubuntu release forces me to purchase a new wifi card.

PS: how can you tell if you are in b, g or n connection?

---

