---
title: "Can't connect to access point"
date: 2012-11-10
forum: Networking &amp; Wireless
---

### Post by Baldrs on 2012-11-10
Hi all!

I've purchased an Dell Inspiron 5720 laptop, which comes with broadcom bcm43142 hybrid wifi/bluetooth card.

After some search, I've managed to install the driver and it seems to work(detects hardware, scans for networks).

The problem is that I can't connect to any of them. I've got a fresh Kubuntu install.

The access point is windows 7 lenovo laptop. It's properly configured, because my former Samsung(old one, lubuntu 12.10 driven) laptop is working with it just fine. I don't have access to another wifi spots and don't have wifi router(we're don't allowed to use such hardware due to our rent contract). The reason why cable is in win7 laptop is that it's my wifes laptop and she's never takes it out from house.

Any help on how I can connect?

---

### Post by Baldrs on 2012-11-11
dmesg says the next thing:
```

[   73.658629] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   73.658809] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   73.658840] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   77.018085] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   77.018112] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   83.011074] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   83.011123] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   89.007247] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   89.007340] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   95.005677] ERROR @wl_cfg80211_get_station : Wrong Mac address
[   95.005721] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  100.999271] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  100.999345] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  106.993698] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  106.993723] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  112.988016] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  112.988034] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  118.981434] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  118.981483] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  130.964863] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  130.964937] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  136.964471] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  136.964546] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  142.958052] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  142.958127] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  148.952657] ERROR @wl_cfg80211_get_station : Wrong Mac address
[  148.952732] ERROR @wl_cfg80211_get_station : Wrong Mac address


```

---

### Post by cfszero on 2013-01-31
In case anyone stumbles across this forum post in the future.

I had a similar problem with my dell laptop upon upgrading to Ubuntu 12.04, and did some research and it turns out that there is a [bug]("https://bugs.mageia.org/show_bug.cgi?id=3296") in some versions of the driver. I solved my issue by installing a newer version of the driver located [here]("http://www.broadcom.com/support/802.11/linux_sta.php")

---

