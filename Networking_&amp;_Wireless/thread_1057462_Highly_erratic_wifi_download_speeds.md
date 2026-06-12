---
title: "Highly erratic wifi download speeds"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by jerrynewt on 2009-02-01
I have been using a laptop (specs in signature) here in this motel room for the past month and the download speeds have been driving me crazy. I am using the netspeed applet, for measuring download speeds, wicd for connections, and Network Connection applet. Wicd shows 60 to 70 percent connection, Network Connection applet shows 80 to 90 percent signal strength, both are very consistent (+ - 5%) at all times. I have minimal problems connecting every day a.m. or p.m. and can access the web. Thing is the download speeds come in like waves on a beach day and night. High speeds of up to 300 KiB/s in short bursts, settling down to around 100 to 150 KiB/s for a few seconds. Then drops off to less than 1 KiB/s for about two to three minutes. This occurs usually during system updates, or downloads from web sites. I have two removable hard drives - 1 running 9.04, and 1 running 8.10. Same speeds on either OS. Is this a wireless router problem (The motel's router) or should I be looking somewhere else for the problem?

---

### Post by jerrynewt on 2009-02-02
Bump please.

---

### Post by jerrynewt on 2009-02-03
Anyone have any ideas at all ??

---

### Post by jerrynewt on 2009-02-04
Did I word my problem wrong, not give enough information, or is it just not interesting enough for some help. Been at this for three days trying to get some help and so far no joy. What am I doing wrong ??

---

### Post by jerrynewt on 2009-02-05
Bump again (again).

---

### Post by srt4play on 2009-02-05
What wireless chip does the toshiba have?

---

### Post by jerrynewt on 2009-02-05
What would the command be for listing the chip ? Thanks for the reply by the way.

---

### Post by srt4play on 2009-02-05
```
lspci | grep Network
```

---

### Post by jerrynewt on 2009-02-05
05:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by srt4play on 2009-02-05
Look in System->Administration->Hardware Drivers to see if any drivers there are activated for your broadcom wireless.

---

### Post by jerrynewt on 2009-02-05
Yes the driver is activated and I am using the Belkin wifi card for my wifi connection. The receive signal strength is more than triple that of the built in wireless on the laptop. I can connect just fine but the download speeds vary dramatically over a period of a few minutes. Just wondering if it could be the motel's wireless router. I have ipv6 disabled, fasterfox installed and a few tweaks installed for firefox. When the speed picks up it can go all the way up to 400 KiB/s for a few seconds but usually stays between 20 and 80 KiB/s. Then after a few minutes it falls off to zero or less than 1 KiB/s for bout three to four minutes, then the cycle starts over again.

---

### Post by jerrynewt on 2009-02-08
bump

---

