---
title: "Slow incoming packets?"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by relovett on 2006-07-11
I am experiencing slow ping times on a Thinkpad 60p running Ubuntu 6.06. The behavior is evident when sending pings to the laptop, but not when sending pings from the laptop.

I've tried sending the pings from several desktops on the same 100Mb segment. I've also tried sending pings to other machines on the network, but the Thinkpad is the only machine that responds slowly. I swapped cables and changed switch ports with no effect.

Note the one instance where the max time was over 1 second. Network sluggishness like this also turns up in ssh'ing into the laptop which is what I'm primarily concerned about.

The laptop uses the e1000 driver. I've tried examining the card with ethtool, but all settings appear to be correct, e.g. 100Mb, full duplex, etc.

  desktop% ping -q -c 10 thinkpad
  round-trip min/avg/max/mdev = 0.655/318.084/1191.811/406.250 ms

  desktop% ping -q -c 10 thinkpad
  round-trip min/avg/max/mdev = 0.213/3.687/16.973/6.597 ms

  desktop% ping -q -c 10 thinkpad
  round-trip min/avg/max/mdev = 2.245/3.371/8.331/1.953 ms

  desktop% ping -q -c 10 thinkpad
  round-trip min/avg/max/mdev = 0.438/4.498/6.798/1.499 ms

  desktop% ping -q -c 10 thinkpad
  round-trip min/avg/max/mdev = 12.022/12.022/12.022/0.000 ms

  desktop% ping -q -c 10 thinkpad
  round-trip min/avg/max/mdev = 1.076/8.189/15.953/4.835 ms

  desktop% ping -q -c 10 thinkpad
  round-trip min/avg/max/mdev = 0.430/7.617/15.324/4.694 ms

Any tips would be appreciated.

---

