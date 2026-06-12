---
title: "NetworkManager's Wireless Connect Timeout"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by cmnorton on 2009-02-15
Is there a way to adjust NetworkManager's timeout, so that its timeout is longer while connecting right after booting up and logging in? What files are involved in controlling the timeout?

I am running 8.10 and am fully updated. NetworkManager takes a long time to connect when I first power up. I get the passphrase screen, press Enter, and after another long wait, I connect.

If I boot up and do not log in right away this does not happen. So, I am wondering if this could be solved if the NetworkManager timeout could be increased.

---

### Post by cmnorton on 2009-02-16
I have temporarily fixed this problem by backing up and editing 
/etc/wpa_supplicant/functions.sh. I changed MAX_WPA_PIDFILE_WAIT="5" to MAX_WPA_PIDFILE_WAIT="10" wherever this environment variable is used, and entered a bug. 

[https://bugs.launchpad.net/ubuntu/+bug/330162](https://bugs.launchpad.net/ubuntu/+bug/330162)

---

### Post by cmnorton on 2009-04-20
After upgrading to 10/2 broadband (Verizon FIOS), I have learned two valuable lessons. One of them is related to this post, and I should have seen its coming. At least in my house, I can situate my laptop too close to the wireless router. Given I have a late model router provided by Verizon, I let them install it upstairs, and my connections were spotty, failing periodically.

As soon as I put the router back in the basement, my connections complete in under thirty seconds, and are strong. (I attribute the signal strength to a newer model router.)

---

