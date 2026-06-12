---
title: "Cannot connect WIreless"
date: 2009-09-25
forum: Networking &amp; Wireless
---

### Post by bilbox on 2009-09-25
Hello,

I have a problem with wireless connection. I have read in the forum that many people have similar problems. I tried some solutions that i found in the forum but never work :(.

My card is
```

MODEL: CT-WN4320Z 
WLAN USB 2.0
```

if i try lsusb i get this:
```
Bus 001 Device 002: ID 0ace:1211 ZyDAS 802.11b/g USB2 WiFi
```

When I install Jaunty i see all the available wireless networks (my network included)... but when i try to connect i can't. I have a WEP Phrase and i had tried with HEX 40/64/128 and ASCII...and it doesn't work...

Then I have quit the WEP Phrase from Router and leave it like an OPEN WIRELESS (without password)... The Network Manager show me my wireless without the shield... Then I try to connect but it's impossible... few seconds later everything stops. :(

Could you give some ideas to try?

Thank you in advance...

Bil

P.S. Sorry for my english...

P.D. Sorry

---

### Post by spd106 on 2009-09-25
Your device is listed as supported on the following site.
[http://linuxwireless.org/en/users/Devices/USB](http://linuxwireless.org/en/users/Devices/USB)

Could it be a signal/interference problem? What level of signal to you get? Can you move closer to the Access Point/Router?

It might be worth monitoring the messages log via the 
System -> Administration -> Log File Viewer.
Anything that mentions wireless or wlan0 might be pertinent.

---

### Post by bilbox on 2009-09-25
Hi, thank you for you quick response.

I think there isn't  a signal/interference problem because if I have SO Windows in the same machine and it works fine. Signal streng is 94%...

In the Log File Viewer I get

```

Sep 27 04:16:18 bilbox-desktop kernel: [   18.124613] usb 1-2: firmware: requesting zd1211/zd1211_ub
Sep 27 04:16:18 bilbox-desktop kernel: [   18.144248] usb 1-2: firmware version 0x4330 and device bootcode version 0x4721 differ
Sep 27 04:16:18 bilbox-desktop kernel: [   18.144251] usb 1-2: firmware: requesting zd1211/zd1211_ur
Sep 27 04:16:18 bilbox-desktop kernel: [   18.209870] usb 1-2: firmware: requesting zd1211/zd1211_uphr
Sep 27 04:16:18 bilbox-desktop kernel: [   18.316523] zd1211rw 1-2:1.0: firmware version 4605
Sep 27 04:16:18 bilbox-desktop kernel: [   18.356645] zd1211rw 1-2:1.0: zd1211 chip 0ace:1211 v4721 high 00-c0-a8 RF2959_RF pa0 g7---
Sep 27 04:16:18 bilbox-desktop kernel: [   18.358884] cfg80211: Calling CRDA for country: US
Sep 27 04:16:18 bilbox-desktop kernel: [   18.362202] cfg80211: Regulatory domain changed to country: US
Sep 27 04:16:18 bilbox-desktop kernel: [   18.362205] ^I(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Sep 27 04:16:18 bilbox-desktop kernel: [   18.362207] ^I(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Sep 27 04:16:18 bilbox-desktop kernel: [   18.362209] ^I(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Sep 27 04:16:18 bilbox-desktop kernel: [   18.362211] ^I(5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 27 04:16:18 bilbox-desktop kernel: [   18.362212] ^I(5490000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Sep 27 04:16:18 bilbox-desktop kernel: [   18.362214] ^I(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Sep 27 04:16:18 bilbox-desktop kernel: [   18.764652] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep 27 04:16:19 bilbox-desktop kernel: [   19.501317] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by spd106 on 2009-09-27
Your card is definitely supported, which is why you can get a list of nearby APs.

It might be worth viewing the daemon.log for lines that begin with "NetworkManager:"

Hopefully you should get something like the following
```

NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed 
NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'O2wireless'. 
```

If not then can you post the stage that it gets up to?

---

### Post by bilbox on 2009-09-28
Thank you very much spd106 for your help. Finally I've download Wicd and I've installed it... Now i can connect to my wireless LAN and navigate.

I don't know what was the problem simplely with WICD it works and with NEtwork Manager no... It's strange because in my netwook it works perfecly with Network Manager...

So thank you very much for yours answers.

Bilbox.

---

