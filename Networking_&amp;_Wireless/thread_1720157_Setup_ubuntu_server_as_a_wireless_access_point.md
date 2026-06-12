---
title: "Setup ubuntu server as a wireless access point"
date: 2011-04-02
forum: Networking &amp; Wireless
---

### Post by ice4ube on 2011-04-02
Hello everyone!

I'm trying to setup my ubuntu server as an access point but am running into some issues.

The server has an Atheros wireless card (AR5008 chipset) and I have used the following link to set it up in master mode using madwifi drivers: [https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

I then used this link to set it upas an access point using hostapd.
[http://www.how2pc.co.il/blog/page/77/](http://www.how2pc.co.il/blog/page/77/)

But inspite of following the above steps, other wireless clients in my LAN are unable to see the ssid "Linuxmaster"

Although iwconfig shows that the card is in master mode.

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Linuxmaster"  
          Mode[COLOR=Red]:Master[/COLOR]  Frequency:2.442 GHz  Access Point: 6C:F0:49:CF:90:3C   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:222  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

br0       no wireless extensions.

ppp0      no wireless extensions.

Your help is greatly appreciated.

Thanks!!

---

### Post by ice4ube on 2011-04-04
ideas anyone?

---

### Post by Tr1p on 2011-10-17
> **ice4ube said:**
> ideas anyone?

Nope

---

### Post by Hulkiedulkie on 2011-10-17
Does it give any errors when you restart hostapd:
 
```

$ sudo /etc/init.d/hostapd stop
$ sudo hostapd /etc/hostapd/hostapd.conf

```
(assuming /etc/hostapd/hostapd.conf is your .conf)

---

