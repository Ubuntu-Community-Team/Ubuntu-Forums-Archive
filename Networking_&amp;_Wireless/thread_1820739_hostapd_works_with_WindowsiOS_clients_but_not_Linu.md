---
title: "hostapd works with Windows/iOS clients but not Linux"
date: 2011-08-08
forum: Networking &amp; Wireless
---

### Post by Kensey on 2011-08-08
I don't know why this should be the case, but here you are:

I set up hostapd on one Ubuntu server (10.04, but I compiled hostapd from source so the running hostapd is 0.7.3 not 0.6.9).  The complete contents of hostapd.conf are:

```
interface=wlan2
driver=nl80211
ssid=apdtest
hw_mode=g
auth_algs=1
wpa=2
wpa_passphrase=asciipassphrase
wpa_key_mgmt=WPA-PSK
wpa_pairwise=CCMP
rsn_pairwise=CCMP
wme_enabled=0
channel=11
```

Using this config, dhcp3-server and a simple IP masquerading iptables rule, my wife's Windows 7 PC connects fine to the Internet over this connection.  Ditto my iPod.  But when I try to connect my Ubuntu 11.04 laptop, the laptop never associates to the AP (the wireless indicator just radiates until it asks me for the passphrase again -- even when I put the passphrase in it never associates).  While trying, iwconfig wlan0 on the laptop shows:

```
wlan0     IEEE 802.11abgn  ESSID:"apdtest"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

What's up with that?

---

### Post by Kensey on 2011-08-09
After some fiddling, I have gotten it to work, but not consistently.  Out of a couple dozen attempts, it's worked two or three times.  On the other devices it works all the time.

Is there something in the Network Manager code that doesn't like hostapd?

---

