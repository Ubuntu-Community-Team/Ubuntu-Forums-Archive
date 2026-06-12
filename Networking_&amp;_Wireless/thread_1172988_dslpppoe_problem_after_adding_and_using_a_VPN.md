---
title: "dsl/pppoe problem after adding and using a VPN"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by okhi on 2009-05-29
hi everyone,

i am running Ubuntu 9.04 on a HP pavillion dv 6000 series.A few days ago i added a new VPN,which worked perfectly,but when i got back home i just couldn't connect to my DSL/PPOE.
I tried to edit the connection through the network manager and re-establish the DSL connection with sudo pppoeconf but without any luck.
Does anyone have any ideas?

thanks

---

### Post by FishyFantasy on 2009-05-29
Hello.

I have the same problem with you. Both pppoeconf and network manager doesn't work for me. I have found a solution in launchpad.net. Someone said "If you use pppoeconf in Ubuntu 9.04 Jaunty, you have doomed yourself." Use ONLY Network Manager. Hope it works for you.

```
sudo apt-get --purge remove pppoeconf

```

Sorry for my bad english :X

---

