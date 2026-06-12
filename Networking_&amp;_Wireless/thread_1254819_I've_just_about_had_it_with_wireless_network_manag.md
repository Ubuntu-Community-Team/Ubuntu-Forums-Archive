---
title: "I've just about had it with wireless network managers .. all of them, even the ones.."
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by sefs on 2009-08-31
...I have not tried.

I have a rt73 type dongle.

Can someone tell me how to set this baby up in /etc/network/interfaces

Is there anyone that has this type of card that is using /etc/network/interfaces?

Have a heart and lend a hand I am begging here after asking this umpteenth times on here and launchpad.net.

Can it be done? :lolflag:

---

### Post by sefs on 2009-09-01
Well, I finally got it sorted, it was easier than I thought and this is what was done.

Create /etc/wpa_supplicant/wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant
network={
        ssid="myssid"
        scan_ssid=0
        mode=0
        proto=RSN
        key_mgmt=WPA-PSK
        pairwise=CCMP
        group=CCMP
        psk=mykeyphrase
}

```

Test manually to make sure it is working from the CLI / Terminal
```

sudo wpa_supplicant -Dwext -iwlan0 -c /etc/wpa_supplicant/wpa_supplicant.conf -d

```
```

sudo dhclient wlan0

```


After any successful testing then configure to load at boot by adding the below to /etc/network/interfaces

/etc/network/interfaces
```

.
.
.
auto wlan0
iface wlan0 inet dhcp
	wpa-driver wext
	wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
.
.
.

```

And that was all it took to get me back to the beloved /etc/network/interfaces.

---

