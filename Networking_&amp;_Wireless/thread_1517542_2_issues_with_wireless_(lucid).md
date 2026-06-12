---
title: "2 issues with wireless (lucid)"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by roberto.tomas on 2010-06-25
I'm on 10.04 -- during configuration we turned on SSID broadcasting just to make things easier. We forgot about that until recently and just switched it off again. Now that the SSID netowkr name is no longer broadcast, my computer does not connect to the internet automatically when it starts. I've read up on this, it seems lots of people have *similar* problems to mine, but none exactly like mine that I can find.

diagnostic steps:
1. what does the log say -- not much:
```
Jun 20 18:49:21 quad-g5 kernel: [   49.066383] Bluetooth: RFCOMM ver 1.11
Jun 20 18:49:52 quad-g5 kernel: [   80.321994] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
Jun 20 18:49:53 quad-g5 nautilus: [N-A] Nautilus-Actions Menu Extender 2.30.2 initializing...
Jun 20 18:49:54 quad-g5 nautilus: [N-A] Nautilus-Actions Tracker 2.30.2 initializing...
Jun 20 18:49:59 quad-g5 pulseaudio[1778]: ratelimit.c: 1 events suppressed
```
once  manually select the network from the applet:
```
Jun 20 18:50:27 quad-g5 kernel: [  115.580930] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 20 18:50:27 quad-g5 kernel: [  115.581283] cfg80211: Calling CRDA for country: US
Jun 20 18:50:27 quad-g5 kernel: [  115.590255] cfg80211: Current regulatory domain updated by AP to: US
Jun 20 18:50:27 quad-g5 kernel: [  115.590262]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun 20 18:50:27 quad-g5 kernel: [  115.590269]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
```
So, I checked if the network settings still is marked for autoconnect, it is:
```
[connection]
id=foobar
uuid=1cf18787-5963-422e-b2aa-c89da91b0d3a
type=802-11-wireless
autoconnect=true
timestamp=1273264560
...
```
then I checked also that the Network Manager's /var state file is set to enable networking, as apparently sometimes this gets toggled. it is:
```
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

```
/var is a bad, *bad* place for a settings file, IMHO. I imagine anyone for whom this settings file needed to be changed would never find it without posting a bug. Anyway.. The last step I read about that might fix the problem is to reinstall network-manager. So I did that, it still does not autoconnect.

Another problem I have with wireless, which I had noticed a couple times before the SSID change, is that rarely I will lose my network connection and when I go to reconnect, it will appear to try and try forever but not actually connect. I have had to reboot to get around this problem until just recently I wrote this script, which odes, 100% of the time, resolve my problem:
```
 sudo service wpa-ifupdown stop
 sudo /etc/init.d/network-manager stop
 sudo /etc/init.d/network-interface stop
 sudo /etc/init.d/network-interface-security stop
 sudo service networking stop

sleep 5

 sudo service networking start
 sudo /etc/init.d/network-interface-security start
 sudo /etc/init.d/network-interface start
 sudo /etc/init.d/network-manager start
 sudo service wpa-ifupdown start
```

---

### Post by roberto.tomas on 2010-06-28
bump

---

