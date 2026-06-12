---
title: "open network fail"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Chuck Glenn on 2009-07-13
I have connected to several different password-protected WiFi networks, including my own home network.  So, I know that the WiFi hardware and software are working fine.  I tried to connect to my local coffee shop's supposedly "open" network, and no dice after several attempts.  Each one would act like it was connecting, but would spin for a few minutes and never connect.  I guess it could have been too busy that day or something, but this seems very unlikely.

My question is, how do I get more information when this happens?  Is there a way I can run something to diagnose?  I have tried using "dmesg | grep -e wlan -e ndis", and I see only a couple of "wlan0: link is not ready" lines, and that's it.  I did see about 12 networks in the WiFi drop-down, and 2 others were full strength, whereas the coffeeshop registered only about 50% strength.  I do remember connecting successfully using the same laptop when I had XP installed on it.  But I was in the main room, and not the side room, so who knows.

Anyway... Is there some software that will give me more immediate feedback about what the problem is?

THANKS.

---

### Post by anystupidname on 2009-07-13
Initially, I would recommend "kismet" if you're talking about tshooting the network itself. If you're talking about troubleshooting your computer's hardware/wifi NIC/networking you should have a look at iwconfig, ifconfig, iwlist, and um... I guess it depends on your NIC chipset and other variables.

---

