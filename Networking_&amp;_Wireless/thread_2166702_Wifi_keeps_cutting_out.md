---
title: "Wifi keeps cutting out"
date: 2013-08-10
forum: Networking &amp; Wireless
---

### Post by dustin2524 on 2013-08-10
[COLOR=#000000]My wireless internet stops working about every 5 minutes. If you reconnect you will get another 5 minutes out of it or if you just wait a few minutes it will come back. This also happens on windows 8, windows 7, and other laptops in the house as well. We have tried resetting the modem/router (it's one unit) before and that either does not fix anything or just gives us a temporary fix ranging from a day to a couple weeks. If I connect Ethernet then it works fine.

Here is some info before it cut out. 
[/COLOR]```
dustin@dove:~$ dmesg | grep -e iwl -e 80211[    9.639898] cfg80211: Calling CRDA to update world regulatory domain
[    9.689667] iwlwifi 0000:05:00.0: irq 45 for MSI/MSI-X
[    9.799902] cfg80211: World regulatory domain updated:
[    9.799905] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.799906] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.799908] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.799908] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.799909] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.799910] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.837314] iwlwifi 0000:05:00.0: loaded firmware version 18.168.6.1
[   10.032630] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.032633] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.032634] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.032635] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   10.032636] iwlwifi 0000:05:00.0: CONFIG_IWLWIFI_P2P disabled
[   10.032638] iwlwifi 0000:05:00.0: Detected Intel(R) Centrino(R) Wireless-N 135 BGN, REV=0x120
[   10.032690] iwlwifi 0000:05:00.0: L1 Disabled; Enabling L0S
[   10.079129] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   11.816341] iwlwifi 0000:05:00.0: L1 Disabled; Enabling L0S
[   11.823930] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
[   12.019447] iwlwifi 0000:05:00.0: L1 Disabled; Enabling L0S
[   12.027027] iwlwifi 0000:05:00.0: Radio type=0x0-0x0-0x0
[  233.855617] cfg80211: Calling CRDA to update world regulatory domain
[  233.862547] cfg80211: World regulatory domain updated:
[  233.862555] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  233.862558] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  233.862561] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  233.862564] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  233.862566] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  233.862568] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  277.587078] cfg80211: Calling CRDA to update world regulatory domain
[  277.593002] cfg80211: World regulatory domain updated:
[  277.593008] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  277.593011] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  277.593014] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  277.593017] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  277.593019] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  277.593022] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  737.111717] cfg80211: Calling CRDA to update world regulatory domain
[  737.117812] cfg80211: World regulatory domain updated:
[  737.117818] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  737.117821] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  737.117825] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  737.117827] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  737.117830] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

[  737.117832] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```[COLOR=#000000]
[/COLOR]```
dustin@dove:~$ nm-tool

NetworkManager Tool


State: connected (global)


- Device: wlan0  [DVW3201B54] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           yes
  HW Address:        0C:D2:92:47:43:57


  Capabilities:
    Speed:           65 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *DVW3201B54:     Infra, 84:4B:F5:85:D6:8B, Freq 2437 MHz, Rate 54 Mb/s, Strength 75 WPA2


  IPv4 Settings:
    Address:         192.168.0.19
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             209.18.47.61
    DNS:             209.18.47.62




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            alx
  State:             unavailable
  Default:           no
  HW Address:        8C:89:A5:09:B1:0D


  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s


  Wired Properties

    Carrier:         off
```[COLOR=#000000]


[/COLOR]

---

### Post by chili555 on 2013-08-10
Let's see:```
cat /etc/modprobe.d/iwlwifi.conf
```Also, I notice the regulatory domain is set to    *<-blank, nowhere, zippo*.> cfg80211: World regulatory domain updated:   Let's try to set it explicitly and see if it helps:```
sudo iw reg set US
```Of course, substitute your locale if it's not US from the list here. Now does the wireless persist?

[http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2)

---

### Post by dustin2524 on 2013-08-10
Setting the locale did not fix it.

---

### Post by fdrake on 2013-08-10
since the wifi has issues with other machines and OS I would suggest you to get a new router. Cisco is my advice.

---

### Post by dustin2524 on 2013-08-10
With the internet plan we have there is only one modem available to choose from. And it doubles as a router, so that is the only unit we have. So even if i buy another router the connection still has to go through the old modem/router.

---

### Post by chili555 on 2013-08-10
How is the wireless configured? WPA2 and what encryption? TKIP or AES? AES is preferred. Is it capable of N speeds? Have you tried resetting the wireless to B and G only? Is it capable of both 2.4 Ghz and 5 Ghz bands? Have you tried disabling the 5 Ghz band?> With the internet plan we have there is only one modem available to choose from. And it doubles as a router, so that is the only unit we have. So even if i buy another router the connection still has to go through the old modem/router. However, you would be using the ethernet capabilities of your current modem/router which apparently works fine. The wireless would be controlled by the new router. 

Before you buy anything, I'd first try the changes I discussed above.

Let's see:
```
cat /etc/modprobe.d/iwlwifi.conf
```

---

### Post by dustin2524 on 2013-08-10
It is fixed! Chili if karma were real you'd be sitting atop the highest throne. Turns out just turning off the 802.11 n-mode fixed it. Heres my working settings for anything that runs into this problem with this modem/router.

[IMG]http://i.imgur.com/gpzm7v0.png[/IMG]

---

### Post by chili555 on 2013-08-10
Woo hoo! Glad it's working! May I get another Solved, please? 

Have fun!

---

