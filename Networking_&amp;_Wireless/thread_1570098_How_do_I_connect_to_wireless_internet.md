---
title: "How do I connect to wireless internet?"
date: 2010-09-07
forum: Networking &amp; Wireless
---

### Post by saharasaidi on 2010-09-07
Okay I'm a total newbie and none of my attempts have worked. I know my wireless router works because it works when I run Windows Vista. Where do I start?

---

### Post by alan8 on 2010-09-07
Hi, to make sure your wireless card was detected correctly:

1. Click "Systems" menu at the top.
2. Select "Preferences" => "Networks Connections".
3. Check if "Wireless" tab is present in "Network Connections".

If it is, you should be able to select your Wireless network and connect to it. If "Wireless" tab is missing, Ubuntu failed to recognise your wireless adapter :(

---

### Post by coffeecat on 2010-09-07
Look at the top panel near the right for the network manager icon. It's next to the volume control, usually to the left. Click on that and if your wireless card has been detected, you should see wireless networks including your own. Simply click on the one you want to connect to and put in your WPA/WEP passkey where prompted. If you don't see any wireless networks there may be a driver issue and we need to investigate more. In this case, open a terminal (Applications > Accessories) and post the output of:

```
sudo lshw -C network
```It will prompt you for your password, but you will not see any feedback when you type this in. This is normal.

---

### Post by saharasaidi on 2010-09-07
there were no wireless connections in the network connections. I put the magic words in the command prompt but it didn't seem to help. I will restart and try again.

Oh, I have a Broadcom 4322AG 802.11a/b/g/draft-n WiFi adapter, if that helps at all.

Edit: I re-entered the magic password and the terminal gave me a bunch of information on the driver. But I still had no available wireless internet connections.

---

### Post by bkratz on 2010-09-07
This will probably help

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by coffeecat on 2010-09-08
> **saharasaidi said:**
> there were no wireless connections in the network connections. I put the magic words in the command prompt but it didn't seem to help. I will restart and try again.

Oh, I have a Broadcom 4322AG 802.11a/b/g/draft-n WiFi adapter, if that helps at all.

Edit: I re-entered the magic password and the terminal gave me a bunch of information on the driver. But I still had no available wireless internet connections.

No, that command wouldn't have helped you connect. It was to tell us what your network hardware was - which is why I asked you to post the output. Anyway, you've now told us that it's a Broadcom card and bkratz has given you a useful link which should help you get connected.

Good luck.

---

