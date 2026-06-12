---
title: "Can't connect to wireless networks after dist-upgrade to 10.10 alpha 1"
date: 2010-06-04
forum: Networking &amp; Wireless
---

### Post by isbura on 2010-06-04
System is an Asus Eee-PC 901 with a RaLink RT2860 wireless card, previously running 10.04 Netbook Remix. Wireless networking was fine for the most part until I decided to jump to the latest alpha. 

I'm pretty sure that drivers for the hardware are installed OK because the **cfg80211** kernel module seems to be loaded and I can see a list of available wireless networks from the drop-down list on the panel. However attempting to connect to any of them gives me a Connecting busy icon for about a minute before telling me a connection couldn't be established. I've tried disabling WPA on my router and connecting unsecured but still no luck.

I realise it's entirely my fault for jumping straight into an alpha release without the knowledge to fix it myself, but any pointers as to how to go about diagnosing where the problem lies would be most welcome.

```

> iwconfig wlan0
wlan0   IEEE 802.11bgn ESSID:"George"
        Mode:Managed  Frequency:2.462 GHz Access Point: Not-Associated
        Tx-Power=9 dBm
        Retry  long limit: 7   RTS thr:off   Fragment thr:off
        Power Management:off

```During a connection attempt I get a string of messages like this in the syslog:

```

wlan0: direct probe to 00:0f:b5:c3:51:66 (try 1)
wlan0: direct probe to 00:0f:b5:c3:51:66 (try 2)
wlan0: direct probe to 00:0f:b5:c3:51:66 (try 3)
wlan0: direct probe to 00:0f:b5:c3:51:66 timed out

```

edit: running **sudo service network-manager restart** allows me to briefly connect to a wireless network, but it then disconnects straight away.

---

