---
title: "hostapd + ath9k = no 11n"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by dutch_gecko on 2010-11-19
Hi all

I've been running hostapd for a while in 11g mode with great success. Having upgraded the router machine to maverick today, I had a poke at getting hostapd working in 11n mode without too much fuss. From cursory reading of old forum posts, this appears to now be built in functionality without needing to compile drivers or hostapd from source - this is borne out by a few 11n-related lines in the default configuration file.

When adding those two lines to my config file, though, I get the same error message I did a few years ago when trying this out for the first time:
```
Line 15: unknown configuration item 'ieee80211n'
Line 16: unknown configuration item 'ht_capab'
2 errors found in configuration file 'hostapd.conf
```

Seems like the new 11n functionality isn't being recognised at all...

Anyone got any ideas on what I'm missing?

Below is my current hostapd.conf:
```
interface=wlan0
driver=nl80211
logger_syslog=-1
logger_syslog_level=2
logger_stdout=-1
logger_stdout_level=2
#dump_file=/tmp/hostapd.dump
ctrl_interface=/var/run/hostapd
ctrl_interface_group=0

ssid=43a
country_code=GB
hw_mode=g
ieee80211n=1
ht_capab=[HT40-][SHORT-GI-40][DSSS_CCK-40]
channel=3
own_ip_addr=192.168.2.1

##macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=3
wpa_passphrase=xxx
wpa_key_mgmt=WPA-PSK 
wpa_pairwise=TKIP
```

---

### Post by jhorck on 2010-12-05
Are you sure you're using the correct version? Try hostapd -v. It seems you're using a version with 11n disabled, compile time.

---

### Post by dutch_gecko on 2010-12-06
> **jhorck said:**
> Are you sure you're using the correct version? Try hostapd -v. It seems you're using a version with 11n disabled, compile time.

Hi, thanks for replying. The output I get is this:
```
hostapd v0.6.9
User space daemon for IEEE 802.11 AP management,
IEEE 802.1X/WPA/WPA2/EAP/RADIUS Authenticator
Copyright (c) 2002-2009, Jouni Malinen <j@w1.fi> and contributors

```

Nothing about compile-time options. This is just the package straight out of the ubuntu repository though, and I was under the impression that this included 11n support as standard now. Am I wrong?

---

