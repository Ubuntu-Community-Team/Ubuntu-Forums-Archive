---
title: "Can't connect to secure wireless network"
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by impervius on 2009-07-01
Ok, I have a Broadcom BCM4318 wireless card in my laptop, and i just managed to install drivers with ndiswrapper.

I can connect to a public, unencrypted wifi network, but i am finding myself unable to connect to my own, encrypted, wireless network.

The security mode is "WPA/WPA2-Personal(PSK)" and the Authentication is "WPA-PSK + WPA2-PSK"

Encryption technique "TKIP+AES"

The network broadcasts on 11b+g+n so i dont think it is a network compatibility issue.

In the networks window, the PSK is changed from what i set it to, to some sort of hash, no matter how many times i set it back.

Any advice anyone?

Edit: both baubles in the connecting icon turn green

---

### Post by impervius on 2009-07-01
anyone?

---

### Post by impervius on 2009-07-01
ok, here's an update- it managed to connect once, but after a restart it refuses to reconnect itself.

please help, i have no idea what exactly is happening

---

### Post by t0mppa on 2009-07-01
I had a similar problem with my Broadcom card. I'd guess it's because the Windows wireless drivers for those that are posted in all guides are so old that they don't really support WPA or WPA2.

Anyway, to circumvent the issue I just went back to b43 instead and now it works just fine.

---

### Post by MaindotC on 2009-07-01
Please try the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  I use zd1211rw on my card.

---

### Post by impervius on 2009-07-02
im not sure what part of that guide i should be looking at.

it's now connected twice, both times without a problem. however, every other time, it doesn't work.

---

### Post by impervius on 2009-07-02
it has now stopped noticing wireless networks

---

### Post by MaindotC on 2009-07-02
You don't know which part of the guide to view because you haven't read it.  Follow the instructions and show us exactly where you are having difficulty.

---

