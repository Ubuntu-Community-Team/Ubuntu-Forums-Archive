---
title: "trouble with interfaces?"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2009-07-02
i've decided to drop networkmanager and wicd for just defining my stuff in /etc/network/interfaces and /etc/wpa_supplicant.conf; however, i'm having some start-up issues where i need to "sudo /etc/init.d/networking restart" after logging-in to connect. any ideas why networking wouldn't just work?

my /etc/network/interfaces:
```
auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wireless-essid 35moore
wpa-driver wext
wpa-conf /etc/wpa_supplicant.conf
```

my /etc/wpa_supplicant.conf:
```
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="35moore"
        key_mgmt=WPA-PSK
        psk="***"
}
```
thanks, in-advance, for any help.

---

### Post by computer13137 on 2009-07-03
I did some Googling and found a very similar problem right here on the Ubuntu Forums.

[http://ubuntuforums.org/showthread.php?t=323177](http://ubuntuforums.org/showthread.php?t=323177)

As the thread suggests, try adding "pre-up sleep 3" to your network configuration.

```
auto ath0
iface ath0 inet dhcp
pre-up sleep 3
[...]
```-Kirk

---

### Post by moore.bryan on 2009-07-06
thanks, kirk... i was able to "solve" this in some unknown way; i.e., it just suddenly started working. however, the sleep command is always useful and one i always forget about... i used it *extensively* when i ran a bare-bones openbox system. 

thanks, again, for the advice!

---

