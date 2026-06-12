---
title: "Atheros ATH9K Wifi not working"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by knichel on 2009-06-11
I need help getting my wireless card going.  I use wicd for network connections. I just installed a fresh copy of Jaunty 64 Bit on my laptop.

$ lsmod | grep ath9k
```

ath9k                 288568  0
mac80211              251144  1 ath9k
led_class              13064  2 ath9k,asus_laptop

```

$lspci
```

07:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

```

$dmesg | grep ath9k
```

[   10.796841] ath9k: 0.1
[   10.796882] ath9k 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.796890] ath9k 0000:07:00.0: setting latency timer to 64
[   11.223112] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   11.247067] Registered led device: ath9k-phy0:radio
[   11.247081] Registered led device: ath9k-phy0:assoc
[   11.247092] Registered led device: ath9k-phy0:tx
[   11.247104] Registered led device: ath9k-phy0:rx

```

It *looks* like it should be working but wicd says no wireless networks found when I have 2 where I am and both are broadcasting ssid.

Can anybody assist?  I use wifi (or want to) at home.

JuJuBee

---

### Post by knichel on 2009-06-12
[COLOR="Red"]Well, I can just die... my wifi switch was off.  I never had a wifi switch and didn't even check it.  [/COLOR]

However, now I can see the wireless networks but cannot connect.  Wicd just keeps trying to connect and eventually fails.  I have a router that has no security settings at all.  

I am wondering what "WPA Suplicant Driver" I should be using. OR if that has anything to do with it....

---

### Post by knichel on 2009-06-14
The problem was solved by installing the compat-wireless... drivers from here [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

don't know why the ATH9k driver not working but the 5K seems to work.

---

