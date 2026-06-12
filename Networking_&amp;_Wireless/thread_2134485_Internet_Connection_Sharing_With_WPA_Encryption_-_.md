---
title: "Internet Connection Sharing With WPA Encryption - tutorial"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by manoynmonic on 2013-04-11
Ok here is my situation: an aircard on the ubuntu machine, sharing the connection with other devices in the house.  The problem was with Ubuntu ad-hoc, I can't set up WPA (in fact, the ad-hoc network wouldn't share internet at all unless the network was open).  Problem two was one of the devices is a kindle (whose fw is android-based), and stock android devices can't connect to ad-hoc anyway.  Thankfully, there is a solution.  Others might be cleaner, but this works for me.

1. Set up a regular open ad-hoc network.
    1a. Click on network manager in the unity taskbar, and select "edit connections"
    1b. click on the wireless tab, and select "add".
    1c.  choose your connection name, ssid, and for mode select "ad-hoc"
    1d.  on the wireless security tab, select "none"
    1e.  on the ipv4 settings tab, select "shared to others" as the method, then click "save"
    1f.  connect to this new open ad-hoc network.  Verify that internet is indeed being shared; do not disconnect from this.
2. install a couple necessary packages

```
sudo apt-get install dhcp3-server hostapd
```

(note: I'm using 12.04 - dhcp3-server has been replaced by isc-dhcp-server in 12.10)

3. open gedit, and paste the following:

interface=wlan0
driver=nl80211
ssid=MyAP
hw_mode=g
channel=11
wpa=1
wpa_passphrase=MyPasswordHere
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
wpa_ptk_rekey=600

  3a.  Replace MyAP with whatever you want to call the connection, and MyPasswordHere with whatever you want, at least eight digits long.  Save this file in your home folder with the name "hostapd.conf"

4.  Now in a terminal, type

```
sudo hostapd hostapd.conf
```


And presto!  The open ad-hoc network is now a wpa encrypted hotspot.

All credit for this tut goes to Shaer
Source: [http://shaer.me/blog/2012/08/how-to-enable-ad-hoc-connection-on-your-android/](http://shaer.me/blog/2012/08/how-to-enable-ad-hoc-connection-on-your-android/)

---

