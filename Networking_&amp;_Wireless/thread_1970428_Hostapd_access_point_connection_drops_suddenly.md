---
title: "Hostapd access point connection drops suddenly"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by dannyvanderzande on 2012-05-01
I set up a wifi access point on my ubuntu server box (now at ubuntu server 12.04) about a week or two ago. In order to get it working I bridged my eth1 with wlan0. Everything seems to be allright, no problems connecting or authenticating but after a few minutes my connection seems to "drop".

My device (phone) is still connected to the network but the internet just stops working. Just a note: My phone does connect to other wireless networks without problems and doesn't have "dropping" issues than.

My card is a D-Link DWL-G510.

Everytime the connection drops I find this message in my syslog. 

```
May  1 13:39:04 thuis-server kernel: [  943.428780] phy0 -> rt2x00queue_write_tx_frame: Error - Dropping frame due to full tx queue 2.
```

I've been googling it but I can't come up with a solution.. Is there anything I can do about this?

---

